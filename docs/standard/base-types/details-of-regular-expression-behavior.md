---
title: Normal İfade Davranışının Ayrıntıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ceee0c228000982be83c79fed2f7af43712b3ae
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963389"
---
# <a name="details-of-regular-expression-behavior"></a>Normal İfade Davranışının Ayrıntıları
.NET Framework normal ifade altyapısı, Perl, Python, Emacs ve Tcl tarafından kullanılan gibi geleneksel bir belirleyici olmayan sonlu bir Automaton (NFA) altyapısını içeren bir geri izleme normal ifade eşleştirici. Bu, onu daha hızlı bir şekilde ayırır, ancak awk, egrep veya Lex içinde bulunanlar gibi daha sınırlı, saf normal ifade belirleyici bir otomasyon (DFA) altyapılarından ayırt edilmesini sağlar. Bu Ayrıca, bunu standartlaştırılmış, ancak daha yavaş, POSIX NFAs olarak da ayırır. Aşağıdaki bölümde, normal ifade altyapısının üç türü açıklanmakta ve .NET Framework normal ifadelerin geleneksel bir NFA altyapısı kullanılarak nasıl uygulandığı açıklanmaktadır.  
  
## <a name="benefits-of-the-nfa-engine"></a>NFA altyapısının avantajları  
 DFA motorları, düzen eşleştirmeyi gerçekleştirirken, işlem sırası giriş dizesi tarafından çalıştırılır. Motor, giriş dizesinin başlangıcında başlar ve sonraki karakterin normal ifade düzeniyle eşleşip eşleşmediğini tespit etmek için ardışık olarak devam eder. Mümkün olan en uzun dizeyi eşleştirmeye garanti edebilirler. Aynı karakteri iki kez test etmeyeceğinden, DFA motorları geri izlemeyi desteklemez. Ancak, bir DFA altyapısı yalnızca sonlu durum içerdiğinden, geri başvuruları olan bir Düzenle eşleşmez ve açık bir genişletme oluşturmadığından, alt ifadeleri yakalamaz.  
  
 DFA altyapılarından farklı olarak, Geleneksel NFA motorları düzen eşleştirmeyi gerçekleştirirken, işlem sırası normal ifade düzeniyle çalıştırılır. Belirli bir dil öğesini işlerken, altyapı doyumsuz eşleştirmeyi kullanır; diğer bir deyişle, giriş dizesinin büyük olasılıkla mümkün olduğunca fazla eşleşir. Ancak, bir alt ifadeyi başarıyla eşleştirdikten sonra da durumunu kaydeder. Bir eşleşme yine başarısız olursa, altyapı daha fazla eşleşme deneyebilmesi için kaydedilmiş bir duruma dönebilir. Bu işlem, normal ifadede daha sonraki dil öğelerinin *geri izleme*olarak bilinmesinin ardından, başarılı bir alt ifadenin eşleşmesi için eşleşir. NFA motorları, belirli bir sırada normal bir ifadenin tüm olası genişletmeleri test etmek için geri izlemeyi kullanır ve ilk eşleşmeyi kabul eder. Geleneksel bir NFA altyapısı başarılı bir eşleşme için normal ifadenin belirli bir genişletmesinin oluşturulduğundan, alt ifade eşleşmelerini ve eşleşen geri başvuruları yakalayabilir. Bununla birlikte, geleneksel bir NFA geri izlemeleriyle, farklı yollar üzerinde duruma alınırsa aynı durumu birden çok kez ziyaret edebilir. Sonuç olarak, en kötü durumda büyük olasılıkla çok daha yavaş çalışabilir. Geleneksel bir NFA motoru bulduğu ilk eşleşmeyi kabul ettiğinden, diğer (muhtemelen uzun) bulunamadan eşleşme de olabilir.  
  
 POSIX NSK motorları Geleneksel NFA altyapılarına benzer, ancak mümkün olan en uzun eşleşmeyi buldıklarından emin olacakları sürece geri izlemeye devam ederler. Sonuç olarak, bir POSIX NFA motoru geleneksel bir NFA altyapısından daha yavaştır ve bir POSIX NFA altyapısı kullandığınızda, geri izleme aramasının sırasını değiştirerek daha kısa bir eşleşmeyi daha uzun bir süre boyunca tercih edilemez.  
  
 Geleneksel nfa motorları, programcılar tarafından daha fazla denetim sağladığından, DFA veya POSIX NSK altyapılarından daha fazla denetim sunduklarında, bu programcılar tarafından sık sık kırmız En kötü durumda, yavaş çalışabilse de, belirsizlikleri azaltan ve geri izlemeyi sınırlayan desenler kullanarak bunları doğrusal veya polinom zaman içinde bulmak için onları eğilede yapabilirsiniz. Diğer bir deyişle, NFA motorları güç ve esneklik için performans sunar, ancak çoğu durumda düzenli bir ifade iyi yazılmışsa ve geri izlemenin performansı katlanarak düşürür.  
  
> [!NOTE]
> Aşırı geri izleme ve bir normal ifadeyi geçici olarak çözmek için kullanmanın bir performans cezası hakkında daha fazla bilgi için bkz. [geri izleme](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>.NET Framework motoru özellikleri  
 Geleneksel bir NFA altyapısının avantajlarından yararlanmak için, .NET Framework normal ifade altyapısı, programcıların geri izleme altyapısını ele geçirmesine olanak sağlayan bir yapı kümesi içerir. Bu yapılar, eşleşmeleri daha hızlı bulmak veya diğerleri üzerinde belirli genişleimler sağlamak için kullanılabilir.  
  
 .NET Framework normal ifade altyapısının diğer özellikleri şunlardır:  
  
- Yavaş nicelik belirteçleri: `??`, `*?`, `+?`, `{`ne`,`.`}?` Bu yapılar geri izleme altyapısından önce en az sayıda tekrarın aramasını söyler. Buna karşılık, sıradan doyumsuz nicelik belirteçleri öncelikle en fazla tekrarlık sayısını eşleştirmeye çalışır. Aşağıdaki örnek, iki arasındaki farkı gösterir. Normal ifade, bir sayıyla biten bir cümle ile eşleşir ve yakalama grubu bu sayıyı çıkarmaya yöneliktir. Normal ifade `.+(\d+)\.` , normal ifade altyapısının yalnızca sayının en `.+`son basamağını yakalamasına neden olan doyumsuz nicelik sayısını içerir. Buna karşılık, normal ifade `.+?(\d+)\.` , normal ifade altyapısının tüm sayıyı yakalamasına neden olan yavaş nicelik `.+?`sayısını içerir.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Bu normal ifadenin doyumsuz ve geç sürümleri, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır:
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`.+`(Greedy nicelik belirteci)|Herhangi bir karakterin en az bir oluşumunu eşleştirin. Bu, normal ifade altyapısının tüm dizeyi eşleştirmesine ve ardından düzenin geri kalanını eşleştirmek için gerektiğinde geri izlemesine neden olur.|  
    |`.+?`(yavaş nicelik belirteci)|Herhangi bir karakterin en az bir oluşumunu eşleştirin, ancak mümkün olduğunca az eşleşir.|  
    |`(\d+)`|En az bir sayısal karakteri eşleştirin ve ilk yakalama grubuna atayın.|  
    |`\.`|Bir noktayla eşleştirin.|  
  
     Yavaş nicelik belirteçleri hakkında daha fazla bilgi için bkz. [nicelik belirteçleri](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Pozitif ileri yönlü `(?=`: alt *ifade*`)`. Bu özellik geri izleme altyapısının alt ifadeyi eşleştirdikten sonra metinde aynı noktaya dönmesini sağlar. Aynı konumdan başlayan birden çok deseni doğrulayarak metnin tamamında arama yapmak yararlı olur. Ayrıca, altyapının alt dizeyi eşleşen metne dahil etmeden, eşleşmenin sonunda var olduğunu doğrulamasına izin verir. Aşağıdaki örnek, noktalama sembolleri tarafından izlenen bir tümcedeki sözcüklerin ayıklanmasına yönelik pozitif ileri yönlü kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Normal ifade `\b[A-Z]+\b(?=\P{P})` aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|  
    |`[A-Z]+`|Herhangi bir alfabetik karakterle bir veya daha fazla kez eşleştirin. <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntemi <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğiyle çağrıldığı için karşılaştırma büyük/küçük harfe duyarlıdır.|  
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
    |`(?=\P{P})`|Sonraki karakterin bir noktalama işareti olup olmadığını anlamak için öne bakın. Aksi takdirde, eşleşme başarılı olur.|  
  
     Olumlu ileri yönlü onaylar hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Negatif ilerleme: `(?!`alt *ifade*`)`. Bu özellik, yalnızca bir alt ifade eşleşmediğinde bir ifadeyle eşleşme özelliği ekler. Bu, genellikle bir aramayı ayıklama açısından güçlü bir durumdur çünkü dahil olması gereken durumlar için bir ifadeden daha kolay bir ifade sağlanması gerekir. Örneğin, "olmayan" ile başlamayan sözcükler için bir ifade yazmak zordur. Aşağıdaki örnek, hariç tutmak için negatif ilerleme kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Normal ifade deseninin `\b(?!non)\w+\b` , aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|  
    |`(?!non)`|Geçerli dizenin "olmayan" ile başlamadığından emin olmak için öne bakın. Varsa, eşleşme başarısız olur.|  
    |`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir.|  
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
     Olumsuz ileri onaylar hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Koşullu değerlendirme: `(?(` *ifade*`)`*Evet*Hayır ve ad Evet Hayır`|``)` `(?(``)` `|``)`burada *ifade* eşleşmek üzere bir alt ifade, *ad* bir yakalama grubunun adıdır,, *ifade* eşleşirse veya *ad* geçerli, boş bir yakalanamayan grup ise, eşleşen dize ve *Hayır* *ifadesi* eşleşmezse veya *ad* geçerli, boş olmayan bir yakalanan grup değilse, eşleştirilecek alt ifade yoktur. Bu özellik, bir önceki alt ifadenin veya sıfır genişlikli bir onaylama sonucuna bağlı olarak, altyapının birden fazla alternatif model kullanarak arama yapmasına olanak sağlar. Bu, örneğin, önceki alt ifadenin eşleştirildiği bir alt ifadeyi eşleştirmesine izin veren daha güçlü bir geri başvuru biçimi sağlar. Aşağıdaki örnekteki normal ifade, hem genel hem de iç kullanım için tasarlanan paragraflarla eşleşir. Yalnızca iç kullanım için tasarlanan paragraflar bir `<PRIVATE>` etiketle başlar. Normal ifade deseninin `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` , yakalama gruplarını ayırmak için genel ve iç kullanım için tasarlanan paragrafların içeriğini atamak üzere koşullu değerlendirme kullanılır. Bu paragraflar daha sonra farklı işlenebilirler.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`^`|Bir satırın başlangıcında eşleşmeyi başlatın.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Dizenin `<PRIVATE>` sıfır veya bir oluşumunu, ardından bir boşluk karakteri ile eşleştirin. Eşleşmeyi adlı `Pvt`bir yakalama grubuyla atayın.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|`Pvt` Yakalama grubu varsa, bir veya daha fazla sözcük karakterinin ardından sıfır veya bir noktalama ayırıcısından sonra bir boşluk karakteri gelen bir veya daha fazla tekrarı eşleştirin. Alt dizeyi ilk yakalama grubuna atayın.|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|`Pvt` Yakalama grubu yoksa, bir veya daha fazla sözcük karakterinin ardından sıfır veya bir noktalama işareti ve ardından bir boşluk karakteri gelen bir veya daha fazla tekrarı eşleştirin. Alt dizeyi üçüncü yakalama grubuna atayın.|  
    |`\r?$`|Satırın sonunu veya dizenin sonunu eşleştirin.|  
  
     Koşullu değerlendirme hakkında daha fazla bilgi için bkz. [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
- Dengeleme grubu tanımları: `(?<` *name1*`-`*AD2* `>` alt *ifadesi*.`)` Bu özellik, normal ifade altyapısının parantez ya da açılış ve kapanış ayraçları gibi iç içe yapıları izlemesini sağlar. Bir örnek için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Geri izleme olmayan alt ifadeler (doyumsuz alt ifadeleri olarak da bilinir): `(?>`alt *ifade*`)`. Bu özellik geri izleme altyapısının, ifadenin kendisini içeren ifadeden bağımsız olarak çalışıyor gibi, alt ifadenin yalnızca ilk eşleştirmelerle eşleştiğini garanti etmesine olanak tanır. Bu yapıyı kullanmazsanız, daha büyük ifadeden geri alma aramaları alt ifadenin davranışını değiştirebilir. Örneğin, normal ifade `(a+)\w` bir veya daha fazla "a" karakteriyle eşleşir ve "a" karakterlerinden sonraki bir sözcük karakteri ile birlikte ilk yakalama grubuna "a" karakteri dizisini atar, ancak son karakter Giriş dizesinin da bir "a" olması, `\w` dil öğesiyle eşleştirildiği ve yakalanan gruba dahil değildir.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Normal ifade `((?>a+))\w` bu davranışı engeller. Birbirini izleyen tüm "a" karakterleri geri izleme olmadan eşleştirildiği için ilk yakalama grubu tüm ardışık "a" karakterlerini içerir. "A" karakterlerinin ardından "a" dışında en az bir karakter daha olmazsa, eşleşme başarısız olur.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Geri alma olmayan alt ifadeler hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Bir<xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusuna veya statik örnek eşleştirme yöntemine seçenek sağlanarak belirtilen sağdan sola eşleme. Bu özellik soldan sağa yerine sağdan sola doğru arama yaparken veya sol yerine modelin sağ bölümünde bir eşleştirmeye başlamak daha verimli olduğu durumlarda faydalıdır. Aşağıdaki örnekte gösterildiği gibi, sağdan sola eşleşme kullanımı, doyumsuz nicelik belirteçleri davranışını değiştirebilir. Örnek, bir sayıyla biten bir cümle için iki arama yapar. Doyumsuz nicelik `+` sayısını kullanan soldan sağa arama, tümcedeki altı basamaktan biriyle eşleşir, ancak sağdan sola arama altı basamakla eşleşir. Normal ifade deseninin bir açıklaması için, bu bölümün önceki kısımlarında yer alan yavaş nicelik belirteçleri gösteren örneğe bakın.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Sağdan sola eşleştirme hakkında daha fazla bilgi için bkz. [normal Ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
- Pozitif ve negatif geriye yönelik: `(?<=`pozitif geriye yönelik alt *ifade* `)` ve `(?<!`negatif geri gerin alt *ifadesi* `)` . Bu özellik, bu konuda daha önce bahsedilen ileri yönlü olarak benzerdir. Normal ifade altyapısı tam sağdan sola eşleştirmeye izin verdiğinden, normal ifadeler sınırsız lookbehinds izin verir. İç içe geçmiş alt ifade bir dış ifadenin üst kümesi olduğunda, nicelik sayısını aşmamak için pozitif ve negatif geriye yönelik Ayrıca kullanılabilir. İç içe geçmiş nicelik belirteçleri olan normal ifadeler genellikle düşük performans sunar. Örneğin, aşağıdaki örnek bir dizenin bir alfasayısal karakterle başladığını ve bittiğini doğrular ve dizedeki diğer tüm karakterler daha büyük bir alt kümeyle biridir. E-posta adreslerini doğrulamak için kullanılan normal ifadenin bir bölümünü oluşturur; daha fazla bilgi için bkz [. nasıl yapılır: Dizelerin geçerli e-posta biçiminde](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)olduğunu doğrulayın.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Normal ifade ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`^`|Dizenin başlangıcında eşleşmeyi başlatın.|  
    |`[A-Z0-9]`|Herhangi bir sayısal veya alfasayısal karakter eşleştirin. (Karşılaştırma büyük/küçük harfe duyarlıdır.)|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Herhangi bir kelime karakterinin sıfır veya daha fazla tekrarı veya şu karakterlerden herhangi birini eşleştirin:-,!, #, $,%, &, ',., \*, +,/, =,?, ^, \`, {,}, &#124;, veya ~.|  
    |`(?<=[A-Z0-9])`|Sayısal veya alfasayısal olması gereken önceki karakterin arkasına bakın. (Karşılaştırma büyük/küçük harfe duyarlıdır.)|  
    |`$`|Dizenin sonundaki eşleşmeyi sonlandırın.|  
  
     Olumlu ve olumsuz geriye yönelik daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Normal ifade izleme dallarının alternatif eşleşmelerin nasıl bulunacağını gösteren bilgiler sağlar.|  
|[Derleme ve Yeniden Kullanma](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Performansı artırmak için normal ifadeleri derleme ve yeniden kullanma hakkında bilgi sağlar.|  
|[İş Parçacığı Güvenliği](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Normal ifade iş parçacığı güvenliği hakkında bilgi sağlar ve normal ifade nesnelerine erişimi ne zaman eşitlemeniz gerektiğini açıklar.|  
|[Normal Ifadeleri .NET Framework](../../../docs/standard/base-types/regular-expressions.md)|Normal ifadelerin programlama diline ilişkin bir genel bakış sağlar.|  
|[Normal İfade Nesne Modeli](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Normal ifade sınıflarının nasıl kullanılacağını gösteren bilgi ve kod örnekleri sağlar.|  
|[Normal İfade Örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)|Ortak uygulamalarda normal ifadelerin kullanımını gösteren kod örnekleri içerir.|  
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Normal ifadeleri tanımlamak için kullanabileceğiniz karakter, işleç ve yapılar kümesi hakkında bilgi sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>

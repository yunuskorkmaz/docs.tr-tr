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
ms.openlocfilehash: bc4d8fdc39153f227e8344ea1da52a0dba2688d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955967"
---
# <a name="details-of-regular-expression-behavior"></a>Normal İfade Davranışının Ayrıntıları
.NET Framework normal ifade altyapısı, Perl, Python, Emacs ve Ukazovat tarafından kullanılan gibi geleneksel bir belirleyici olmayan sonlu Otomasyon (NFA) altyapısı içeren bir geri izlemenin normal ifade Eşleştiricisi ' dir. Bu ondan daha hızlı, ancak daha sınırlı, saf normal ifade belirleyici sonlu Otomasyon (DFA) alt awk, egrep veya lex bulunanlar gibi ayırır. Bu ayrıca, standart, ancak daha yavaş ayıran POSIX NFAs. Aşağıdaki bölümde üç normal ifade altyapısı ve geleneksel bir NFA Altyapısı'nı kullanarak .NET Framework normal ifadelerinde neden uygulanan açıklanmaktadır.  
  
## <a name="benefits-of-the-nfa-engine"></a>NFA Altyapısı'nın avantajları  
 DFA altyapıları desen eşleştirme işlemi yapmak, bunların işleme sırası giriş dizesi ile yönetilir. Altyapı, Giriş dizesinin başında başlar ve sırayla sonraki karakteri normal ifade deseni ile eşleşip eşleşmediğini belirlemek için devam eder. Bunlar, mümkün olan en uzun dize eşleşmesi garanti edebilir. Bunlar hiçbir zaman aynı karakterle iki kez test etmek için geri izlemenin DFA altyapıları desteklemez. Ancak, DFA altyapısı yalnızca sınırlı bir durum içerdiği için bir desen ile geribaşvurular eşleşemez ve açık bir genişletme oluşturmak değildir çünkü alt ifadeler yakalayamaz.  
  
 Desen eşleştirme, geleneksel NFA altyapıları gerçekleştirdiğinizde DFA altyapıları, işleme sırası tarafından normal ifade deseni yönlendirilir. Belirli bir dil öğesi işler gibi doyumsuz eşleşme altyapısı kullanır; büyük olasılıkla mümkün olduğunca diğer bir deyişle, Giriş dizesinin kadar eşleşir. Ancak, bir alt ifade eşleştirildikten sonra da durumunu kaydeder. Bir eşleşme sonunda başarısız olursa altyapısı bir eşleşme deneyebilmek kaydedilmiş bir duruma geri dönebilirsiniz. Normal ifadede sonraki dil öğelerini de eşleşen bir başarılı alt ifade bir eşleşme bırakıp, bu işlem olarak bilinir *geri izlemenin*. Tüm olası genişletmeleri normal bir ifadenin belirli bir sırayla test ve ilk eşleşme kabul etmek için geri izleme NFA altyapıları kullanın. Geleneksel bir NFA altyapısı belirli bir normal ifade başarılı bir eşleşme genişletilmesi oluşturur çünkü alt eşleşme ve eşleşen geribaşvurular yakalayabilirsiniz. Geleneksel bir NFA provided olduğundan, farklı yollar duruma geldiğinde, ancak bunu aynı duruma birden çok kez ziyaret edebilirsiniz. Sonuç olarak, katlanarak yavaş en kötü durumda çalıştırabilirsiniz. Geleneksel bir NFA altyapısı ilk kabul ettiğinden bulduğu eşleşen, keşfedilmemiş (muhtemelen uzun) eşleşmeleri da bırakabilirsiniz.  
  
 Bunlar en uzun eşleşme olası bulduğunuz garanti kadar geri izleme yapmaya devam etmek dışında POSIX NFA geleneksel NFA altyapıları gibi motorlardır. Sonuç olarak, geleneksel bir NFA altyapısı daha yavaş POSIX NFA altyapısıdır ve POSIX NFA altyapısı kullandığınızda, geri izlemenin arama sırasını değiştirerek daha uzun bir üzerinden daha kısa bir eşleşme favor olamaz.  
  
 Bunlar DFA ya da POSIX NFA altyapıları eşleşen dize üzerinde daha fazla denetim sağlar çünkü geleneksel NFA altyapıları programcılar tarafından stadyumlarda. En kötü durumda, bunlar yavaş çalıştırabilirsiniz ancak bunları belirsizlikleri azaltma ve geri izlemeyi sınırlama desenleri kullanarak doğrusal veya polinom sürede bulmaya faaliyetidir. Güç ve esneklik, çoğu durumda sundukları için performans NFA altyapıları ticari olsa da başka bir deyişle, kabul edilebilir performans için iyi bir normal ifade iyi-yazılan ve hangi durumlarda önler geri izleme performansı katlanarak düşürür.  
  
> [!NOTE]
>  Aşırı geri izleme ve normal bir ifade çalışıyorlardı yolları tarafından etrafında çalışma nedeniyle performans cezası hakkında daha fazla bilgi için bkz. [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>.NET framework altyapısı özellikleri  
 Geleneksel bir NFA altyapısının avantajlarından yararlanmak için .NET Framework normal ifade altyapısı geri izlemenin altyapısı faaliyetidir programcıların etkinleştirmek için yapıları eksiksiz bir kümesini içerir. Bu yapılar, belirli genişletmeleri diğer tanınacağını ya da eşleşme daha hızlı bulmak için kullanılabilir.  
  
 .NET Framework normal ifade Altyapısı'nın diğer özellikleri şunlardır:  
  
- Yavaş miktar belirleyiciler: `??`, `*?`, `+?`, `{` *n*`,`*m*`}?`. Bu yapılar, ilk tekrarına en az sayıda aramak için geri izlemenin altyapısı söyleyin. Buna karşılık, yinelemeleri sayısı eşleştirilecek normal doyumsuz miktar belirleyiciler deneyin. Aşağıdaki örnek, ikisi arasındaki farkı gösterir. Bir sayı ile biten bir cümle normal bir ifadeyle eşleşiyor ve yakalama grubu bu sayıyı ayıklamak için tasarlanmıştır. Normal ifade `.+(\d+)\.` doyumsuz miktar Belirleyicisini içerse `.+`, yalnızca son basamak sayısının yakalamak normal ifade altyapısı neden olur. Buna karşılık, normal ifade `.+?(\d+)\.` yavaş miktar Belirleyicisini içerse `.+?`, normal ifade altyapısı tüm sayıyı yakalamak neden olur.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Bu normal ifade doyumsuz ve yavaş sürümleri aşağıdaki tabloda gösterildiği gibi tanımlanır.'  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`.+` (doyumsuz niceleyici)|Herhangi bir karakterle en az bir oluşumunu eşleştirin. Bu normal ifade altyapısının tüm dizeyi eşleştir neden olur ve ardından olarak geri izleme yapmaya geri kalanında deseni eşleştirmek gerekli.|  
    |`.+?` (yavaş belirleyici birlikte)|Herhangi bir karakterle en az bir oluşumunu eşleştirin, ancak en az bir eşleşen.|  
    |`(\d+)`|En az bir sayısal karakterle Eşleştir ve ilk yakalama gruba atayın.|  
    |`\.`|Bir noktayı eşleştirin.|  
  
     Yavaş miktar belirleyiciler hakkında daha fazla bilgi için bkz: [miktar belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Pozitif ileriye yönelik: `(?=` *subexpression*`)`. Bu özellik, bir alt ifade eşleştirildikten sonra metin aynı nokta dönmek geri izlemenin altyapısı sağlar. Aynı konumdan başlayan birden çok desen doğrulayarak boyunda metinde arama için kullanışlıdır. Ayrıca, eşleşen metnin alt dizeyi dahil etmeden bir alt dizeyi eşleştir sonunda bulunduğunu doğrulamak altyapı sağlar. Aşağıdaki örnek, noktalama simgeleri tarafından izlenmeyen bir cümle sözcüklerini ayıklamak için pozitif bir ileriye yönelik onay kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Normal ifade `\b[A-Z]+\b(?=\P{P})` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|  
    |`[A-Z]+`|Alfabetik karakterleri bir veya daha fazla kez eşleştirin. Çünkü <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği, karşılaştırma duyarsızdır.|  
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
    |`(?=\P{P})`|Sonraki karakterin bir noktalama işareti olup olmadığını belirlemek için önceden arayın. Yüklü değilse, eşleşme başarılı olur.|  
  
     Pozitif ileriye yönelik onaylar hakkında daha fazla bilgi için bkz: [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Negatif ileriye yönelik: `(?!` *subexpression*`)`. Bu özellik yalnızca eşleştirmek bir alt ifade başarısız olursa bir ifadeyle eşleşen özelliği ekler. Genellikle bir ifade dahil edilmesi gereken durumlar için daha ortadan bir çalışması için bir ifade sağlamak daha basit olduğu için bu özellikle güçlü bir arama kesilmeyeceğini budur. Örneğin, bir ifade "non" ile başlamayan sözcükleri yazın zordur. Aşağıdaki örnek, negatif ileriye yönelik dışlamak için kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Normal ifade deseni `\b(?!non)\w+\b` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|  
    |`(?!non)`|Şimdi geçerli dize emin olmak için "non" ile başlamıyor arayın. Aksi halde eşleştirme başarısız olur.|  
    |`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir.|  
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
     Negatif ileriye yönelik onaylar hakkında daha fazla bilgi için bkz: [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Koşullu değerlendirme: `(?(` *ifade*`)`*Evet*`|`*hiçbir* `)` ve `(?(` *adı*`)`*Evet*`|`*hiçbir*`)`burada *ifade* eşleştirmek için bir alt ifade *adı* bir yakalama grubunun adıdır *Evet* eşleşiyorsa dizedir *ifade* eşleştirilir veya *adı* geçerlidir, boş olmayan yakalanan grubu ve *hiçbir* eşleşiyorsa için alt ifade *ifade* eşlenemiyor veya *adı* geçerli, boş olmayan bir yakalanan grubu değil. Bu özellik, bir önceki alt ifade eşleşme sonucunu veya sıfır genişlikli onaylama sonucuna bağlı olarak birden fazla alternatif deseni kullanılarak aramak altyapı sağlar. Bu, eşleşen bir önceki alt ifade olup eşleştirildi dayalı bir alt ifade veren yeniden başvuru, daha güçlü bir form sağlar. Normal ifade aşağıdaki örnekte, hem genel hem de iç kullanıma yöneliktir paragraflar eşleşir. Yalnızca dahili kullanım için paragraflar ile başlayan bir `<PRIVATE>` etiketi. Normal ifade deseni `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` koşullu değerlendirme genel kullanıma yönelik ve yakalama grupları ayırmak iç kullanım için hedeflenen paragraflar içeriğini atamak için kullanır. Ardından paragraflarda farklı şekilde işlenebilir.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`^`|Bir satırın başında eşleşmeye başla.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Eşleşen dizeyi sıfır veya bir oluşumunu `<PRIVATE>` sonrasında bir boşluk karakteri. Eşleşme adlandırılmış bir tutma grubu atamak `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Varsa `Pvt` yakalama grubu varsa, bir boşluk karakteriyle ardından sıfır veya bir noktalama ayırıcısı tarafından izlenen bir veya daha fazla sözcük karakteri bir veya daha fazla oluşumunu eşleyin. Alt dizenin ilk yakalama gruba atayın.|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|Varsa `Pvt` yakalama grubu mevcut değilse, bir veya daha fazla örneğini bir veya daha fazla sözcük karakterini arkasından bir boşluk karakteriyle ardından sıfır veya bir noktalama ayırıcı. Alt dizeyi, üçüncü yakalama gruba atayın.|  
    |`\r?$`|Bir satırın sonuna veya dizesinin sonuyla eşleş.|  
  
     Koşullu değerlendirme hakkında daha fazla bilgi için bkz: [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
- Grup tanımlarını Dengeleme: `(?<` *name1*`-`*name2* `>` *subexpression*`)`. Bu özellik, parantez veya açma ve kapatma köşeli ayraçlar gibi iç içe geçmiş yapılar izlemek normal ifade altyapısı sağlar. Bir örnek için bkz. [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Geri dönüşlü olmayan alt ifadeler (doyumsuz yararlanılmaktadır olarak da bilinir): `(?>` *subexpression*`)`. Bu özellik, ifade, içeren ifade bağımsız çalışıyormuş gibi bir alt ifade yalnızca bu alt ifade için bulunan ilk eşleşme eşleştiğini güvence altına almak geri izlemenin altyapısı sağlar. Tento konstruktor je kullanmazsanız, geri izlemenin aramalarından daha büyük bir ifadenin bir alt ifade davranışını değiştirebilirsiniz. Örneğin, normal ifade `(a+)\w` eşleşiyorsa "bir veya daha fazla a" karakteri, "a" karakteri sırasını izler ve bir dizi "a" karakteri ilk yakalama grubu için ancak atayan bir sözcük karakteriyle yanı sıra son karakter Giriş dizesi, ayrıca bir "a", BT olan tarafından eşleştirilen `\w` dil öğesi ve yakalanan gruba dahil değildir.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Normal ifade `((?>a+))\w` Bu davranış engeller. Çünkü tüm ardışık "a" karakteri geri izleme olmadan eşleştirilir, ilk yakalama grubu tüm ardışık içerir "a" karakteri. "A" karakteri olarak "a" dışında en az bir karakter daha sonrasında eşleşme başarısız olur.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Geri dönüşlü olmayan alt ifadeler hakkında daha fazla bilgi için bkz: [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Sağ eşleştirme sağlanarak belirtilen sola <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> seçeneğini bir <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusunun veya statik eşleme yönteminin örneği. Bu özellik, sağdan sola yerine soldan sağa veya sola yerine deseninin sağ kısmındaki bir eşleşmeye başla daha verimli olduğu durumlarda ararken kullanışlıdır. Aşağıdaki örnekte gösterildiği gibi sağdan sola eşleştirme kullanılarak doyumsuz miktar belirleyiciler davranışını değiştirebilirsiniz. Örneğin, bir sayı ile biten bir cümle için iki arama yapar. Doyumsuz niceleyici kullanan soldan sağa arama `+` tüm altı basamaklı sağdan sola Aramayla eşleşen ise tümcedeki altı basamaklı biriyle eşleşir. Normal ifade deseni bir açıklaması için bu bölümün önceki kısımlarında yavaş miktar belirleyiciler gösteren örneğe bakın.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Sağdan sola eşleştirme hakkında daha fazla bilgi için bkz. [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
- Pozitif ve negatif geriye yönelik: `(?<=` *subexpression* `)` pozitif geriye yönelik için ve `(?<!` *subexpression* `)` negatif geriye yönelik için. Bu özellik, bu konunun önceki kısımlarında açıklanan ileriye yönelik benzer. Normal ifadeler, normal ifade motoru soldan sağa tam eşleşen izin verdiğinden, Kısıtlanmamış geriye ilerleme izin verir. Pozitif ve negatif geriye yönelik iç içe geçmiş alt ifade bir dış ifade bir alt kümesi olduğunda, iç içe geçmiş miktar belirleyiciler önlemek için de kullanılabilir. Normal ifadeler gibi iç içe geçmiş miktar belirleyiciler ile genellikle kötü bir performans sunar. Örneğin, aşağıdaki örnekte, bir dize başlar ve alfasayısal bir karakter ile sona eriyor ve herhangi bir karakter dizesindeki bir daha büyük bir alt kümesine olduğunu doğrular. Bu e-posta adreslerini doğrulamak için kullanılan normal ifadeyi bir bölümünü oluşturur; Daha fazla bilgi için [nasıl yapılır: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Normal ifade `^[A-Z0-9]([-!#$%&'.*+/=?^` {}| ~ \w])* (? < = [A-Z0-9]) $' aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`^`|Dizesinin başında eşleşmeye başla.|  
    |`[A-Z0-9]`|Sayısal veya alfasayısal bir karakterle eşleş. (Karşılaştırma büyük küçük harfe duyarlıdır.)|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])*<code>|Match zero or more occurrences of any word character, or any of the following characters:  -, !, #, $, %, &, ', ., *, +, /, =, ?, ^, \`, {, }, &#124;, or ~.|  
    |`(?<=[A-Z0-9])`|Arkasında sayısal veya alfasayısal olmalıdır bir önceki karaktere bakın. (Karşılaştırma büyük küçük harfe duyarlıdır.)|  
    |`$`|Dizenin sonunda eşleştirmeyi sonlandır.|  
  
     Pozitif ve negatif geriye yönelik hakkında daha fazla bilgi için bkz: [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Alternatif bulmaya dallar geri izlemenin nasıl normal ifade hakkında bilgi sağlar.|  
|[Derleme ve Yeniden Kullanma](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Derleme ve performansı artırmak için normal ifadeler yeniden kullanma hakkında bilgi sağlar.|  
|[İş Parçacığı Güvenliği](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Normal ifade iş parçacığı güvenliği hakkında bilgi sağlar ve normal ifade nesnelere erişimi olduğunda eşitlenmesi gerektiğini açıklar.|  
|[.NET framework normal ifadeleri](../../../docs/standard/base-types/regular-expressions.md)|Programlama dili en boy normal ifadelerin genel bir bakış sağlar.|  
|[Normal İfade Nesne Modeli](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Bilgi ve normal ifade sınıflarının nasıl kullanılacağını gösteren kod örnekleri sağlar.|  
|[Normal İfade Örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)|Normal ifadeler ortak uygulamalarda kullanımını gösteren kod örnekleri içerir.|  
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Karakter, işleç ve normal ifadeler tanımlamak için kullanabileceğiniz yapılar kümesi hakkında bilgi sağlar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>

---
title: "Normal İfade Davranışının Ayrıntıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b471cd8e934880fc8095fbad68b460174ec338c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="details-of-regular-expression-behavior"></a>Normal İfade Davranışının Ayrıntıları
.NET Framework normal ifade Perl, Python, Emacs ve Tcl tarafından kullanılan gibi geleneksel bir belirleyici sınırlı Automaton (NFA) altyapısı içerir kırıntıları oluşturma bir normal ifade Eşleştirici altyapısıdır. Bu ondan daha hızlı ve daha kısıtlı, saf normal ifade belirleyici sınırlı Automaton (DFA) altyapılarını awk, egrep veya lex bulunanlar gibi ancak ayırır. Bu ayrıca, standartlaştırılmış, ancak daha yavaş, ayırt POSIX NFAs. Aşağıdaki bölümde normal ifade motorları üç tür ve geleneksel NFA altyapısını kullanarak .NET Framework normal ifadelerinde neden uygulanan açıklanmaktadır.  
  
## <a name="benefits-of-the-nfa-engine"></a>NFA altyapısı yararları  
 DFA motorları desen eşleştirme gerçekleştirdiğinizde, bunların işleme sırası giriş dizesi ile yönetilir. Altyapı giriş dizesi başında başlar ve sırayla sonraki karakteri normal ifade deseni eşleşip eşleşmediğini belirlemek için devam eder. Bunlar, olası en uzun dizeyi eşleştirmek garanti edebilir. Bunlar hiçbir zaman aynı karakterin iki kez test etmek için geri dönüş DFA motorları desteklemez. Ancak, bir DFA altyapısı yalnızca sınırlı durumu içerdiğinden, yeniden başvurular olan bir desen eşleşemez ve açık bir genişletme oluşturmak değil çünkü alt ifadelerin yakalayamazsınız.  
  
 Desen eşleştirme, geleneksel NFA motorları gerçekleştirdiğinizde DFA altyapılarını, kendi işleme sırası normal ifade deseni tarafından yönetilir. Belirli bir dili öğesi işler gibi doyumsuz eşleşen altyapısı kullanır; büyük olasılıkla mümkün olduğunca diğer bir deyişle, Giriş dizesinin kadar eşleşir. Ancak bir alt başarıyla eşleştirildikten sonra da durumunu kaydeder. Bir eşleşme sonunda başarısız olursa ek eşleşmeleri deneyebilirsiniz şekilde altyapısı kaydedilen bir duruma geri dönebilirsiniz. Bu işlemi başarılı alt eşleşme terk normal ifadede sonraki dil öğeleri de eşleşmesi olarak bilinen *geri dönüş*. NFA motorları, belirli bir sırada tüm olası genişletmeleri normal bir ifade, test ve ilk eşleşmeye kabul etmek için geri dönüş kullanın. Belirli bir genişletme başarılı bir eşleştirme için normal ifadenin geleneksel NFA motoru oluşturur çünkü alt eşleşiyor ve eşleşen yeniden başvurular yakalayabilirsiniz. Geleneksel NFA backtracks çünkü farklı yollar duruma gelirse ancak onu aynı duruma birden çok kez ziyaret edebilirsiniz. Sonuç olarak, katlanarak yavaş kötü durumda çalıştırabilirsiniz. Geleneksel NFA altyapısı ilk kabul ettiğinden bulur eşleşmiyor, keşfedilmemiş (büyük olasılıkla daha uzun) eşleşmeleri bırakabilirsiniz.  
  
 Bunlar uzun eşleşme olası bulduğunuz garanti kadar geri izlemeyi devam dışında POSIX NFA motorları gibi geleneksel NFA altyapısı,'dır. Sonuç olarak, geleneksel bir NFA altyapısı yavaş POSIX NFA altyapısıdır ve POSIX NFA altyapısı kullandığınızda, kırıntıları oluşturma arama sırasını değiştirerek daha uzun bir üzerinden daha kısa bir eşleşme favor olamaz.  
  
 DFA veya POSIX NFA motorları eşleşen dize üzerinde daha fazla denetim sunduklarından geleneksel NFA motorları tarafından programcıları avantajlı. Kötü durumda bunlar yavaş çalıştırabilirsiniz ancak bunları belirsizlikleri azaltmak ve geri dönüş sınırlayabilirsiniz desenler kullanılarak doğrusal veya polinom zamanında eşleşmeleri bulunacak ilerletebilir. Güç ve esneklik, çoğu durumda bunlar sunmak için performans NFA motorları ticari olmasa da diğer bir deyişle, kabul edilebilir performans için iyi bir normal ifade iyi yazılmış ise ve hangi durumlarda önler geri dönüş performans katlanarak düşürür.  
  
> [!NOTE]
>  Yaşanan aşırı geri dönüş ve normal bir ifade oluşturabilir yolları tarafından etrafında çalışmaya neden performans sorunları hakkında daha fazla bilgi için bkz: [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>.NET framework altyapısını özellikleri  
 Geleneksel NFA altyapısı avantajlarından yararlanmak için .NET Framework normal ifade altyapısı kırıntıları oluşturma altyapısı ilerletebilir programcıların etkinleştirmek için yapıları eksiksiz bir kümesini içerir. Bu yapıları eşleşmeleri daha hızlı bulmak için veya belirli genişletmeleri başkalarının ayrıcalık tanıma için kullanılabilir.  
  
 .NET Framework normal ifade Altyapısı'nın diğer özellikleri şunlardır:  
  
-   Yavaş miktar belirleyiciler: `??`, `*?`, `+?`, `{`  *n*  `,` *m*`}?`. Bu yapıları tekrarları en az sayıda ilk aramak için kırıntıları oluşturma altyapısı söyleyin. Buna karşılık, yinelemeleri sayısını ilk eşleşecek şekilde sıradan doyumsuz nicelik deneyin. Aşağıdaki örnek, ikisi arasındaki farkı gösterilmektedir. Bir sayı ile biten bir cümle normal bir ifadeyle eşleşen ve bir yakalama grubunu bu sayıyı ayıklamak için tasarlanmıştır. Normal ifade `.+(\d+)\.` doyumsuz niceleyici içeren `.+`, yalnızca son basamaklı sayının yakalamak normal ifade altyapısı neden olur. Buna karşılık, normal ifade `.+?(\d+)\.` yavaş niceleyici içeren `.+?`, tüm sayıyı yakalamak normal ifade altyapısı neden olur.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Bu normal ifade doyumsuz ve yavaş sürümleri aşağıdaki tabloda gösterildiği gibi tanımlanır.'  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`.+` (doyumsuz niceleyici)|En az bir geçişi herhangi bir karakter ile eşleşir. Bu normal ifade altyapısını tüm dizeyi eşleştir neden olur ve ardından olarak geri izlemeyi desen kalanı eşleşecek şekilde gerekiyordu.|  
    |`.+?` (yavaş niceleyici)|En az bir geçişi herhangi bir karakter ile eşleşen ancak olabildiğince az eşleşmesi.|  
    |`(\d+)`|İlk yakalama grubuna atayın ve en az bir sayısal karakter eşleşmiyor.|  
    |`\.`|Bir süre aynı.|  
  
     Yavaş miktar belirleyiciler hakkında daha fazla bilgi için bkz: [nicelik](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Pozitif ilerleme: `(?=` *alt*`)`. Bu özellik metin aynı konumda bir alt eşleştirildikten sonra geri dönmek kırıntıları oluşturma altyapısı sağlar. Aynı konumu Başlat birden çok desenleri doğrulayarak metin arama için yararlıdır. Ayrıca, eşleşen metnin alt dizeyi eklemeden bir alt dize eşleştirme sonunda bulunduğunu doğrulamak altyapı sağlar. Aşağıdaki örnek pozitif ileri yönlü tümcedeki noktalama simgeleri tarafından izlenmeyen sözcüklerin ayıklamak için kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Normal ifade `\b[A-Z]+\b(?=\P{P})` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|  
    |`[A-Z]+`|Alfabetik bir karakterle bir veya birden çok kez eşleşmesi. Çünkü <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi ile çağrılır <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği, karşılaştırma büyük küçük harfe duyarsızdır.|  
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
    |`(?=\P{P})`|Sonraki karakteri bir noktalama işareti sembolü olup olmadığını belirlemek için önceden bakın. Değilse, eşleştirmenin başarılı olur.|  
  
     Pozitif ileri yönlü onaylar hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Negatif ilerleme: `(?!` *alt*`)`. Bu özellik yalnızca bir alt eşleşecek şekilde başarısız olursa bir ifadeyle eşleşecek yeteneği ekler. Genellikle bir ifade dahil edilmesi gereken durumlarda bir ifade daha ortadan bir servis talebi sağlamak daha basit olduğu için bu bir arama kesilmeyeceğini özellikle güçlüdür. Örneğin, bir ifade "harici" ile başlamayan sözcükleri yazmak zor olabilir. Aşağıdaki örnek, bunları dışarıda bırakma negatif ileri yönlü kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Normal ifade deseni `\b(?!non)\w+\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`\b`|Bir sözcük sınırında eşleşmeye başla.|  
    |`(?!non)`|Şimdi geçerli dizesi emin olmak için "harici" ile başlamaz arayın. Aşması durumunda eşleştirmesi başarısız olur.|  
    |`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir.|  
    |`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
     Negatif ilerleme onaylar hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Koşullu değerlendirme: `(?(` *ifade*`)`*Evet*`|`*hiçbir* `)` ve `(?(` *adı*`)`*Evet*`|`*hiçbir*`)`, burada *ifade* eşleştirmek için bir alt olduğu *adı* yakalama bir grubun adı *Evet* eşleşiyorsa dize *ifade* eşleşen veya *adı* geçerli, boş olmayan yakalanan grubu ve *hiçbir* alt eşleşiyorsa olan *ifade* eşlenemiyor veya *adı* geçerli, boş olmayan bir yakalanan grup değil. Bu özellik Sıfır Genişlik onaylama sonucunu veya önceki bir alt eşleşme sonucu bağlı olarak birden fazla alternatif düzeni kullanarak aramak altyapı sağlar. Bu, önceki alt eşleşen dayalı bir alt eşleşen verir yeniden başvuru daha güçlü bir tür sağlar. Normal ifade aşağıdaki örnekte, hem genel hem de iç kullanımı için tasarlanmıştır paragrafları eşleşir. Yalnızca dahili kullanım için hedeflenen paragrafları başlamak ile bir `<PRIVATE>` etiketi. Normal ifade deseni `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` ortak ve yakalama gruplarını ayırmak dahili kullanım için hedeflenen paragrafları içeriğini atamak için koşullu değerlendirme kullanır. Bu paragrafları sonra farklı bir şekilde işlenebilir.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`^`|Eşleşen bir satır başında başlar.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Eşleşen dizenin sıfır veya bir örneğinin `<PRIVATE>` sonrasında bir boşluk karakteri. Eşleşen adlı bir yakalama grubuna atama `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Varsa `Pvt` Grup yakalama var, bir veya daha fazla tekrarı sıfır veya bir noktalama ayırıcı sonrasında bir boşluk karakteri ve ardından bir veya daha fazla sözcük karakterlerini eşleşmesi. Alt dizeyi ilk yakalama grubuna atayın.|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|Varsa `Pvt` Grup yakalama olmayabilir, eşleşecek ya da bir veya daha fazla sözcük karakterlerini birden fazla örneğini sonrasında bir boşluk karakteri sıfır veya bir noktalama ayırıcı ardında. Alt dizeyi üçüncü yakalama grubuna atayın.|  
    |`\r?$`|Eşleşen bir satır sonu veya dize sonu.|  
  
     Koşullu değerlendirme hakkında daha fazla bilgi için bkz: [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
-   Grup tanımlarını Dengeleme: `(?<` *Ad1*`-`*ad2* `>` *alt*`)`. Bu özellik parantez veya açma ve ayraç gibi iç içe geçmiş yapılar izlemek normal ifade altyapısı sağlar. Bir örnek için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Nonbacktracking alt ifadelerin (olarak da bilinen doyumsuz alt ifadelerin): `(?>` *alt*`)`. Bu özellik ifadesi içeren kendi ifadesi bağımsız çalışıyormuş gibi bir alt yalnızca o alt, bulunan ilk eşleşme eşleştiğini güvence altına almak kırıntıları oluşturma altyapısı sağlar. Bu yapıyı kullanmazsanız, kırıntıları oluşturma aramalardan daha büyük bir alt davranışını değiştirebilirsiniz. Örneğin, normal ifade `(a+)\w` eşleşiyorsa bir veya daha fazla "a" karakter "a" karakter dizisi izler ve "a" karakter dizisi ilk yakalama grubuna ancak atayan bir sözcük karakteriyle birlikte son karakter Giriş dizesi bir "a", BT de olduğundan tarafından eşleşen `\w` language öğesi ve yakalanan gruba dahil değildir.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Normal ifade `((?>a+))\w` Bu davranış engeller. Çünkü tüm ardışık "a" karakterleri geri dönüş olmadan eşleştirilir, ilk yakalama grubu tüm ardışık içerir "a" karakter. "A" karakter "a" dışında en az bir daha fazla karakterle ardından eşleşme başarısız olur.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Nonbacktracking alt ifadelerin hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Sağ eşleştirme sağlayarak belirtilen sola <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> için seçeneğini bir <xref:System.Text.RegularExpressions.Regex> sınıfı oluşturucusu veya statik örnek eşleşen yöntemi. Bu özellik, sağdan sola yerine soldan sağa veya sola yerine deseninin sağ kısmındaki bir eşleşme başlamak için daha etkili olduğu durumlarda ararken kullanışlıdır. Aşağıdaki örnekte gösterildiği gibi sağdan sola eşleştirme kullanılarak doyumsuz nicelik davranışını değiştirebilirsiniz. Örneğin, bir sayı ile biten bir cümle iki arar yürütür. Doyumsuz niceleyici kullanan soldan sağa arama `+` tüm altı basamak sağdan sola arama sonuçları ise tümcedeki altı basamakların eşleşiyor. Normal ifade deseni açıklaması için bu bölümün önceki kısımlarında yavaş miktar belirleyiciler gösterilmektedir örneğe bakın.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Sağdan sola eşleştirme hakkında daha fazla bilgi için bkz: [normal ifade seçenekleri](../../../docs/standard/base-types/regular-expression-options.md).  
  
-   Pozitif ve negatif geriye ilerleme: `(?<=` *alt* `)` pozitif geriye ilerleme için ve `(?<!` *alt* `)` negatif geriye ilerleme için. Bu özellik, bu konunun önceki bölümlerinde açıklanan ileri yönlü benzerdir. Normal ifade altyapısı tam sağdan sola eşleşen izin verdiğinden, normal ifadeler Kısıtlanmamış geri yönler izin verir. Pozitif ve negatif geriye ilerleme, iç içe alt dış ifade bir üst olduğunda iç içe geçmiş nicelik önlemek için de kullanılabilir. Normal ifadeler gibi iç içe geçmiş nicelik ile genellikle düşük performans sunar. Örneğin, aşağıdaki örnek, bir dize başlar ve bir alfasayısal karakter ile sona erer ve herhangi bir karakter dizesi içinde daha büyük bir alt biri olduğunu doğrular. E-posta adreslerini doğrulamak için kullanılan normal ifade bir bölümünü oluşturur; Daha fazla bilgi için bkz: [nasıl yapılır: dizelerin geçerli e-posta biçiminde olduğunu doğrulama](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Normal ifade `^[A-Z0-9]([-!#$%&'.*+/=?^`{} | ~ \w])* (? < = [A-Z0-9]) $' aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
    |Desen|Açıklama|  
    |-------------|-----------------|  
    |`^`|Eşleşme dizenin başında başlar.|  
    |`[A-Z0-9]`|Sayısal veya alfasayısal bir karakterle eşleşmesi. (Karşılaştırma büyük küçük harfe duyarlıdır.)|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])*<code>|Sıfır veya daha çok tekrarı herhangi bir sözcük karakteri veya şu karakterlerden herhangi birini eşleşen:-,!, #, $, % &, ',., *, +, /, =,?, ^, \`, {,}, &#124; veya ~.|  
    |`(?<=[A-Z0-9])`|Arkasında sayısal veya alfasayısal olmalıdır bir önceki karakteri arayın. (Karşılaştırma büyük küçük harfe duyarlıdır.)|  
    |`$`|Son dizenin sonunda eşleşmiyor.|  
  
     Pozitif ve negatif geriye ilerleme hakkında daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Dalları alternatif eşleşmeleri bulmak için geri dönüş nasıl normal ifade hakkında bilgi sağlar.|  
|[Derleme ve Yeniden Kullanma](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Derleme ve performansı artırmak için normal ifadeler yeniden kullanma hakkında bilgi sağlar.|  
|[İş Parçacığı Güvenliği](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Normal ifade iş parçacığı güvenliği hakkında bilgi sağlar ve ne zaman normal ifade nesnelere erişimi eşitlenmesi gerektiğini açıklar.|  
|[.NET framework normal ifadeleri](../../../docs/standard/base-types/regular-expressions.md)|Normal ifadeler programlama dili yönünü genel bir bakış sağlar.|  
|[Normal İfade Nesne Modeli](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Bilgi ve normal ifade sınıflarının nasıl kullanılacağını gösteren kod örnekleri sağlar.|  
|[Normal İfade Örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)|Sık kullanılan uygulamalar normal ifadelerde kullanımını gösteren kod örnekleri içerir.|  
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Karakter, işleçler ve normal ifadeler tanımlamak için kullanabileceğiniz yapıları kümesi hakkında bilgi verilmektedir.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>

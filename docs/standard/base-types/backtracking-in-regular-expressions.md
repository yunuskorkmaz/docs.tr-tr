---
title: .NET normal Ifadelerinde geri izleme
description: Normal ifade deseninin eşleştirmesinde geri izlemeyi denetlemeyi öğrenin.
ms.date: 11/12/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, backtracking
- alternative matching patterns
- optional matching patterns
- searching with regular expressions, backtracking
- pattern-matching with regular expressions, backtracking
- backtracking
- regular expressions [.NET Framework], backtracking
- strings [.NET Framework], regular expressions
- parsing text with regular expressions, backtracking
ms.assetid: 34df1152-0b22-4a1c-a76c-3c28c47b70d8
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 289b6997a4d17463072418fbf17f5f99874f4988
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2019
ms.locfileid: "66378161"
---
# <a name="backtracking-in-regular-expressions"></a>Normal İfadelerde Geri Dönüş
<a name="top"></a>Bir normal ifade deseninin isteğe bağlı [nicelik belirteçleri](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md) veya [değişim yapılarını](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)içermesi durumunda geri izleme oluşur ve normal ifade altyapısı, bir eşleşme aramasına devam etmek için önceki kaydedilmiş bir duruma geri döner. Geri izleme, normal ifadelerin gücü bakımından çok önemlidir; ifadelerin güçlü ve esnek olmasına ve çok karmaşık desenlerle eşleşmelerine olanak sağlar. Aynı zamanda, bu güç bir maliyetle birlikte gelir. Geri izleme, genellikle normal ifade altyapısının performansını etkileyen tek önemli etmendir. Neyse ki, geliştirici, normal ifade motorunun davranışını ve geri izlemeyi nasıl kullandığını denetleyebilir. Bu konu, geri izlemenin nasıl çalıştığını ve nasıl kontrol edilebileceğini açıklar.  
  
> [!NOTE]
>  Genel olarak, .NET normal ifade altyapısı gibi belirleyici olmayan sınırlı bir Otomatikton (NFA) altyapısı, geliştirici üzerinde etkili ve hızlı düzenli ifadeler oluşturma sorumluluğunu önemli bir şekilde yerleştiriyor.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Geri Izleme olmadan doğrusal karşılaştırma](#linear_comparison_without_backtracking)  
  
- [Isteğe bağlı nicelik belirteçleri veya değişim yapıları ile geri izleme](#backtracking_with_optional_quantifiers_or_alternation_constructs)  
  
- [Iç Içe Isteğe bağlı nicelik belirteçleri ile geri izleme](#backtracking_with_nested_optional_quantifiers)  
  
- [Geri Izlemeyi denetleme](#controlling_backtracking)  
  
<a name="linear_comparison_without_backtracking"></a>   
## <a name="linear-comparison-without-backtracking"></a>Geri İzleme Olmadan Doğrusal Karşılaştırma  
 Bir normal ifade deseninin isteğe bağlı miktar niceleyicileri yoksa, normal ifade altyapısı doğrusal zamanda çalışır. Diğer bir deyişle, normal ifade altyapısı desendeki ilk dil öğesini giriş dizesindeki metinle eşleştirdikten sonra, it desende sonraki dil öğesini giriş dizesindeki sonraki karakterle veya karakter grubuyla eşleştirir. Bu, eşleştirme başarılı veya başarısız oluncaya kadar devam eder. Her iki durumda da, normal ifade altyapısı giriş dizesinde bir kerede bir karakter ilerler.  
  
 Aşağıdaki örnek, bir gösterim sağlar. Normal ifade `e{2}\w\b` , "e" harfinin ardından bir sözcük sınırı ve ardından bir sözcük sınırı gelen iki oluşum arar.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 Bu normal ifade nicelik `{2}`belirleyiciyi içerse de, doğrusal bir şekilde değerlendirilir. Normal ifade altyapısı, isteğe bağlı bir belirleyici olmadığı `{2}` için geri izleme yapmaz;, önceki alt ifadenin eşleşmesi gereken değişken sayısını değil, tam bir sayı belirtir. Sonuç olarak, normal ifade altyapısı, aşağıdaki tabloda gösterildiği gibi, normal ifade desenini giriş dizesiyle eşleştirmeye çalışır.  
  
|Çalışma|Desendeki konum|Dizedeki konum|Sonuç|  
|---------------|-------------------------|------------------------|------------|  
|1\.|e|"needing a reed" (dizin 0)|Eşleşme yok.|  
|2|e|"eeding a reed" (dizin 1)|Olası eşleşme.|  
|3|a{2}|"eding a reed" (dizin 2)|Olası eşleşme.|  
|4|\w|"al gerekli" (dizin 3)|Olası eşleşme.|  
|5|\b|"ing a reed" (dizin 4)|Olası eşleşme başarısız olur.|  
|6|e|"eding a reed" (dizin 2)|Olası eşleşme.|  
|7|a{2}|"al gerekli" (dizin 3)|Olası eşleşme başarısız olur.|  
|8|e|"al gerekli" (dizin 3)|Eşleme başarısız olur.|  
|9|e|"ing a reed" (dizin 4)|Eşleşme yok.|  
|10|e|"ng a reed" (dizin 5)|Eşleşme yok.|  
|11|e|"g a reed" (dizin 6)|Eşleşme yok.|  
|12|e|"bir Reed" (Dizin 7)|Eşleşme yok.|  
|13|e|"bir Reed" (Dizin 8)|Eşleşme yok.|  
|14|e|"Reed" (Dizin 9)|Eşleşme yok.|  
|15|e|"Reed" (Dizin 10)|Eşleşme yok|  
|16|e|"eed" (dizin 11)|Olası eşleşme.|  
|17|a{2}|"ed" (dizin 12)|Olası eşleşme.|  
|18|\w|"d" (dizin 13)|Olası eşleşme.|  
|19|\b|"" (dizin 14)|Eşleşme.|  
  
 Bir normal ifade deseni isteğe bağlı miktar niceleyiciler veya değişim yapıları içermiyorsa, normal ifade desenini giriş dizesiyle eşleştirmek için gereken en fazla karşılaştırma sayısı, kabaca giriş dizesindeki karakter sayısına eşittir. Bu durumda, normal ifade altyapısı, 13 karakterlik bu dizedeki olası eşleşmeleri tanımlamak için 19 karşılaştırma kullanır.  Diğer bir deyişle, isteğe bağlı miktar niceleyiciler veya değişim yapıları içermiyorsa, normal ifade altyapısı doğrusala yakın bir zamanda çalışır.  
  
 [Başa dön](#top)  
  
<a name="backtracking_with_optional_quantifiers_or_alternation_constructs"></a>   
## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>İsteğe Bağlı Miktar Niceleyiciler veya Değişim Yapıları ile Geri İzleme  
 Normal bir ifade isteğe bağlı miktar niceleyiciler veya değişim yapıları içerdiğinde, giriş dizesinin değerlendirilmesi artık doğrusal değildir. Bir NFA altyapısıyla desen eşleştirme, giriş dizesinde eşleştirilecek karakterlerle değil, normal ifadedeki dil öğeleriyle yönlendirilir. Bu nedenle, normal ifade altyapısı, isteğe bağlı veya alternatif alt ifadeleri tam olarak eşleştirmeye çalışır. Alt ifadede sonraki dil öğesine ilerlediğinde ve eşleştirme başarısız olduğunda, normal ifade altyapısı, normal ifadeyi giriş dizesiyle bir bütün olarak eşleştirmek amacıyla, başarılı eşleştirmesinin bir bölümünü bırakır ve daha önce kaydedilen bir duruma geri döner. Bir eşleştirme bulmak üzere daha önce kaydedilen bir duruma bu şekilde geri dönme işlemi, geri izleme olarak bilinir.  
  
 Örneğin, "es" karakterleriyle ve ondan `.*(es)`önceki tüm karakterlerle eşleşen normal ifade örüntüyi göz önünde bulundurun. Aşağıdaki örnekte gösterildiği gibi, giriş dizesi "Essential services are provided by regular expressions." ise, desen, "expressions"daki "es"a kadar ve "es" dahil olmak üzere tüm dizeyle eşleşir.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 Bunu yapmak için, normal ifade altyapısı aşağıdaki gibi geri izlemeyi kullanır:  
  
- Tüm giriş dizesiyle `.*` (herhangi bir karakterin sıfır, bir veya daha fazla tekrarı ile eşleşen) ile eşleşir.  
  
- Normal ifade deseninde "e"yi eşleştirmeyi dener. Ancak, giriş dizesinde eşleştirilebilecek başka karakter kalmamıştır.  
  
- En son başarılı eşleştirmesi olan "Essential services are provided by regular expressions" dizesine geri izleme yapar ve "e"yi cümlenin sonundaki nokta ile eşleştirmeyi dener. Eşleştirme başarısız olur.  
  
- Geçici olarak eşleştirilen "Essential services are provided by regular expr" alt dizesine kadar, bir kerede bir karakter olacak şekilde, daha önceki başarılı bir eşleştirmeye geri izleme yapmaya devam eder. Ardından, desendeki "e"yi "expressions"daki ikinci "e" ile karşılaştırır ve bir eşleştirme bulur.  
  
- Desendeki "s" ile, eşleştirilen "e" karakterini izleyen "s"yi ("expressions"daki ilk "s") karşılaştırır. Eşleştirme başarılıdır.  
  
 Geri izleme kullandığınızda, normal ifade desenini 55 karakter uzunluğundaki giriş dizesiyle eşleştirmek, 67 karşılaştırma işlemi gerektirir. Genellikle, normal bir ifade deseninin tek bir değişim yapısı veya tek bir isteğe bağlı miktar niteleyicisi varsa, deseni eşleştirmek için gereken karşılaştırma işlemlerinin sayısı, giriş dizesindeki karakterlerin sayısının iki katıdır.  
  
 [Başa dön](#top)  
  
<a name="backtracking_with_nested_optional_quantifiers"></a>   
## <a name="backtracking-with-nested-optional-quantifiers"></a>İç İçe Geçmiş İsteğe Bağlı Miktar Niceleyicilerle Geri İzleme  
 Desen çok sayıda değişim yapıları içeriyorsa, iç içe değişim yapıları içeriyorsa veya en yaygın olasılık olarak iç içe isteğe bağlı miktar niceleyiciler içeriyorsa, normal bir ifade desenini eşleştirmek için gereken karşılaştırma işlemlerinin sayısı katlanarak artabilir. Örneğin, normal ifade deseninin `^(a+)+$` bir veya daha fazla "a" karakteri içeren bir dizenin tamamını eşleştirmek için tasarlanmıştır. Örnek, aynı uzunlukta iki giriş dizesi sağlar, fakat yalnızca ilk dize desenle eşleşir. <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> Sınıfı, eşleşme işleminin ne kadar sürdüğünü belirlemekte kullanılır.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 Örnekteki çıktının gösterdiği gibi, normal ifade altyapısının, bir giriş dizesinin desenle eşleşmediğini bulması, eşleşen bir dize tanımlamasına göre iki kat daha uzun sürdü. Bunun nedeni, başarısız bir eşleştirmenin her zaman bir kötü durum senaryosunu temsil etmesidir. Eşleştirmenin başarısız olduğu sonucuna varabilmesinden ve iç içe parantezlerin veri içinde birçok ek yol oluşturmasından önce, normal ifade altyapısının veri içinde olası tüm yolları izlemek için normal ifadeyi kullanması gerekir. Normal ifade altyapısı, aşağıdakileri yaparak ikinci dizenin desenle eşleşmediği sonucuna varır:  
  
- Bu, dizenin başlangıcında olduğunu denetler ve dizedeki ilk beş karakterle birlikte bu stili `a+`eşleştirir. Ardından, dizede ek "a" karakteri grupları olmadığını belirler. Son olarak, dizenin sonu için sınama yapar. Dizede bir ek karakter kaldığından, eşleştirme başarısız olur. Bu hatalı eşleşme, 9 karşılaştırma gerektirir. Normal ifade altyapısı ayrıca, "a" (eşleştirme 1 olarak adlandırırız), "aa" (eşleştirme 2), "aaa" (eşleştirme 3) ve "aaaa" (eşleştirme 4) eşleştirmelerinden elde ettiği durum bilgisini de kaydeder.  
  
- Önceden kaydedilen eşleştirme 4'e döndürür. Ek bir yakalan gruba atamak için bir ek "a" karakteri olduğunu belirler. Son olarak, dizenin sonu için sınama yapar. Dizede bir ek karakter kaldığından, eşleştirme başarısız olur. Bu başarısız eşleşme 4 karşılaştırma gerektirir. Şu ana kadar toplam 13 karşılaştırma yapıldı.  
  
- Daha önce kaydedilen eşleşme 3 ' e döndürür. Ek bir yakalanan gruba atamak için iki ek "a" karakteri olduğunu belirler. Ancak, dize sonu sınaması başarısız olur. Ardından, eşleştirme 3'e geri döner ve yakalanan iki ek gruptaki iki ek "a" karakterini eşleştirmeyi dener. Dize sonu sınaması hala başarısız olur. Bu başarısız eşleştirmeler 12 karşılaştırma gerektirir. Şimdiye kadar, toplam 25 karşılaştırma gerçekleştirildi.  
  
 Giriş dizesinin normal ifadeyle karşılaştırılması, normal ifade altyapısı tüm olası eşleştirme birleşimlerini deneyinceye kadar bu şekilde devam eder ve ardından eşleştirme olmadığı sonucuna ulaşır. İç içe nicelik belirteçleri nedeniyle, bu karşılaştırma bir O (2<sup>n</sup>) veya üstel bir işlemdir; burada *n* , giriş dizesindeki karakter sayısıdır. Bu, en kötü durumda, 30 karakterlik bir giriş dizesinin yaklaşık 1.073.741.824 karşılaştırma gerektirdiği ve 40 karakterlik bir giriş dizesinin yaklaşık 1,099,511,627,776 karşılaştırma gerektirdiği anlamına gelir. Bu uzunluklarda veya daha uzun dizeler kullanırsanız, normal ifade deseniyle eşleşmeyen giriş işlediklerinde, normal ifade yöntemlerinin tamamlanması çok uzun zaman alabilir.  
  
 [Başa dön](#top)  
  
<a name="controlling_backtracking"></a>   
## <a name="controlling-backtracking"></a>Geri İzlemeyi Denetleme  
 Geri izleme, güçlü ve esnek normal ifadeler oluşturmanıza olanak tanır. Ancak, önceki bölümde gösterildiği gibi, bu yararlar kabuk edilemeyecek kadar düşük performansla eşleştirilebilir. Aşırı geri izlemeyi engellemek için, bir <xref:System.Text.RegularExpressions.Regex> nesneyi örneklediğinizde veya statik bir normal ifade eşleştirme yöntemini çağırdığınızda bir zaman aşımı aralığı tanımlamanız gerekir. Bu konu, sonraki bölümde açıklanmaktadır. Ayrıca, .NET, geri izlemeyi sınırlayan veya gizleyen ve çok az performans cezası olan karmaşık normal ifadeleri destekleyen üç normal ifade dili öğesini destekler: geri dönüş [olmayan alt ifadeler](#Nonbacktracking), geriye yönelik [ Onaylamalar](#Lookbehind)ve [ileri yönlü](#Lookahead)onaylar. Her dil öğesi hakkında daha fazla bilgi için bkz. [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
<a name="Timeout"></a>   
### <a name="defining-a-time-out-interval"></a>Bir Zaman Aşımı Aralığı Tanımlama  
 4,5 .NET Framework başlayarak, en uzun aralığı temsil eden bir zaman aşımı değeri ayarlayabilirsiniz. Bu işlem, denemesi yapılmadan önce bir özel durum arar ve bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> özel durum oluşturur. Örnek normal ifadeler için <xref:System.TimeSpan> <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> oluşturucuya bir değer sağlayarak zaman aşımı aralığını belirtirsiniz. Ayrıca, her bir statik model eşleştirme yönteminin bir zaman aşımı değeri belirtmenize <xref:System.TimeSpan> izin veren bir parametreye sahip bir aşırı yüklemesi vardır. Varsayılan olarak, zaman aşımı aralığı olarak <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> ayarlanır ve normal ifade motoru zaman aşımına uğrar.  
  
> [!IMPORTANT]
>  Normal ifadeniz geri izlemeye dayalıysa, her zaman bir zaman aşımı aralığı ayarlamanızı öneririz.  
  
 Bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> özel durum, normal ifade altyapısının belirtilen zaman aşımı aralığı içinde bir eşleşme bulamadığını ancak özel durumun neden gerçekleştiğini belirtmediğini belirtir. Bunun nedeni aşırı geri izleme olabilir, fakat özel durumun oluştuğu zamandaki sistem yükü nedeniyle zaman aşımı aralığı çok düşük ayarlanmış da olabilir. Özel durumu işlediğinizde, giriş dizesiyle diğer eşleştirmeleri bırakmayı veya zaman aşımı aralığını artırarak eşleştirme işlemini yeniden denemeyi seçebilirsiniz.  
  
 Örneğin, aşağıdaki kod, bir saniyelik zaman <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> aşımı değeri olan bir <xref:System.Text.RegularExpressions.Regex> nesneyi başlatmak için oluşturucuyu çağırır. Bir satırın sonundaki bir `(a+)+$`veya daha fazla "a" karakterinin bir veya daha fazla dizisi ile eşleşen normal ifade deseninin aşırı geri izlenmesi konusuna tabidir. Bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> oluşturulursa, örnek, zaman aşımı değerini üç saniyelik en fazla aralığa kadar arttırır. Bundan sonra, deseni eşleştirme girişiminden vazgeçer.  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  
  
<a name="Nonbacktracking"></a>   
### <a name="nonbacktracking-subexpression"></a>Geri İzlemeli Olmayan Alt İfade  
 `(?>` Alt ifadeLanguage`)` öğesi bir alt ifade içinde geri izlemeyi bastırır. Başarısız eşleştirmelerle ilişkili performans sorunlarını önlemek için yararlıdır.  
  
 Aşağıdaki örnekte, iç içe miktar niceleyiciler kullanılırken geri izlemenin bastırılmasının performansı nasıl iyileştirdiği gösterilmektedir. Normal ifade altyapısının bir giriş dizesinin iki normal ifadeyle eşleşmediğini belirlemesi için gereken süreyi ölçer. İlk normal ifade, ardından bir iki nokta işareti, ardından bir veya daha fazla ondalık basamak, ardından iki iki nokta işareti gelen bir veya birden fazla ondalık basamağın bir veya birden fazla örneğini içeren bir dizeyle eşleştirme yapmayı denemek için geri izleme kullanır. İkinci normal ifade, geri izlemeyi devre dışı bırakması dışında, birincisiyle aynıdır. Örnekteki çıktının gösterdiği gibi, geri izlemeyi devre dışı bırakmanın sağladığı performans iyileşmesi önemlidir.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  
  
<a name="Lookbehind"></a>   
### <a name="lookbehind-assertions"></a>Geriye Yönelik Onaylar  
 .Net, giriş dizesindeki önceki karakterle `(?<=`veya karakterlerle `(?<!`eşleşen iki dil öğesi, alt *ifade* `)` ve alt *ifade*`)`içerir. Her iki dil öğesi de sıfır genişlikli onaylardır; diğer bir deyişle, geçerli karakterden hemen önce gelen karakter veya karakterlerin, gelişmiş veya geri izleme olmadan alt *ifade*ile eşleştirilemeyeceğini tespit ederler.  
  
 `(?<=`alt *ifade* pozitif bir geriye yönelik onaylama onaydır; diğer bir deyişle, geçerli konumdan önceki karakter veya karakterlerin alt ifadeyle eşleşmesi gerekir. `)` `(?<!`*alt ifade* `)` negatif geriye yönelik bir onaylama onaydır; diğer bir deyişle, geçerli konumdan önceki karakter veya karakterler alt *ifade*ile eşleşmemelidir. Hem pozitif hem de negatif geriye yönelik Onaylamalar, alt *ifade* önceki alt ifadenin bir alt kümesi olduğunda faydalıdır.  
  
 Aşağıdaki örnek, bir e-posta adresindeki Kullanıcı adını doğrulayan iki denk normal ifade deseni kullanır. Birinci desen, aşırı geri izleme nedeniyle yetersiz performansa maruz kalır. İkinci desen, iç içe bir miktar niteleyiciyi pozitif bir geriye yönelik onayla değiştirerek birinci normal ifadeyi değiştirir. Örneğin çıktısı, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yönteminin yürütme süresini gösterir.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 İlk normal ifade deseninin `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin Yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğiyle çağrıldığı için bu karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`[-.\w]*`|Bir kısa çizgi, nokta veya sözcük karakterinin sıfır, bir veya daha fazla örneğini eşleştirin.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin|  
|`([-.\w]*[0-9A-Z])*`|Ardından alfasayısal bir karakter gelen sıfır veya daha fazla kısa çizgi, nokta veya sözcük karakteri birleşiminin sıfır veya daha fazla örneğini eşleştirin. Bu ilk yakalama grubudur.|  
|`@`|("\@") İşaretiyle Eşleştir.|  
  
 İkinci normal ifade deseninin `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`, pozitif bir geriye yönelik onaylama işlemi kullanır. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin Yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğiyle çağrıldığı için bu karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`[-.\w]*`|Bir kısa çizgi, nokta veya sözcük karakterinin sıfır, bir veya daha fazla örneğini eşleştirin.|  
|`(?<=[0-9A-Z])`|Son eşleşen karaktere geriye doğru bakın ve alfasayısal ise eşleştirmeyi devam ettirin. Alfasayısal karakterlerin, nokta, kısa çizgi ve tüm sözcük karakterlerinden oluşan kümenin bir alt kümesi olduğunu unutmayın.|  
|`@`|("\@") İşaretiyle Eşleştir.|  
  
<a name="Lookahead"></a>   
### <a name="lookahead-assertions"></a>İleriye Yönelik Onaylar  
 .Net, giriş dizesindeki sonraki karakterle `(?=`veya karakterlerle `(?!`eşleşen iki dil öğesi, alt *ifade* `)` ve alt *ifade*`)`içerir. Her iki dil öğesi de sıfır genişlikli onaylardır; Yani, geçerli karakteri hemen izleyen karakter veya karakterlerin, gelişmiş veya geri izleme olmadan alt *ifade*ile eşleştirilemeyeceğini tespit ederler.  
  
 `(?=`alt *ifade* pozitif bir ileriye yönelik onaylama onaydır; Yani, geçerli konumdan sonraki karakter veya karakterlerin alt ifadeyle eşleşmesi gerekir. `)` `(?!`*alt ifade* `)` negatif bir ileriye yönelik onaydır; Yani, geçerli konumdan sonraki karakter veya karakterler alt *ifade*ile eşleşmemelidir. Hem pozitif hem de negatif ileriye yönelik Onaylamalar, alt *ifade* sonraki alt ifadenin bir alt kümesi olduğunda faydalıdır.  
  
 Aşağıdaki örnekte, tam olarak belirtilen bir tür adını doğrulayan iki denk normal ifade deseni kullanılmaktadır. Birinci desen, aşırı geri izleme nedeniyle yetersiz performansa maruz kalır. İkincisi, iç içe bir miktar niteleyiciyi pozitif bir ileriye yönelik onayla değiştirerek birinci normal ifadeyi değiştirir. Örneğin çıktısı, <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yönteminin yürütme süresini gösterir.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 İlk normal ifade deseninin `^(([A-Z]\w*)+\.)*[A-Z]\w*$`, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`([A-Z]\w*)+\.`|Ardından bir nokta gelen sıfır veya daha fazla sözcük karakterinin bir veya birden çok kez ardından geldiği bir alfabetik karakterle (A-Z) eşleştirin. Yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğiyle çağrıldığı için bu karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`(([A-Z]\w*)+\.)*`|Önceki desenle sıfır veya daha çok kez eşleştirin.|  
|`[A-Z]\w*`|Ardından sıfır veya daha fazla karakter gelen alfabetik bir karakterle eşleştirin.|  
|`$`|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 İkinci normal ifade deseninin `^((?=[A-Z])\w+\.)*[A-Z]\w*$`pozitif bir ileri yönlü onaylama işlemi kullanır. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`(?=[A-Z])`|İleriye yönelik olarak birinci karaktere bakın ve alfabetik (A-Z) ise eşleştirmeyi devam ettirin. Yöntemi <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneğiyle çağrıldığı için bu karşılaştırma büyük/küçük harfe duyarlıdır.|  
|`\w+\.`|Ardından bir nokta gelen bir veya daha fazla sözcük karakterini eşleştirin.|  
|`((?=[A-Z])\w+\.)*`|Ardından sıfır veya daha çok kez bir nokta gelen bir veya birden çok sözcük karakteri desenini eşleştirin. İlk sözcük karakterinin alfabetik olması gerekir.|  
|`[A-Z]\w*`|Ardından sıfır veya daha fazla karakter gelen alfabetik bir karakterle eşleştirin.|  
|`$`|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 [Başa dön](#top)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Niceleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)
- [Değişim Yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)
- [Gruplama Yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)

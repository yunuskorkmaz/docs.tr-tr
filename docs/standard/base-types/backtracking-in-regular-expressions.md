---
title: .NET normal ifadelerde geri dönüş
description: Geri izlemenin normal ifade deseni eşleştirme içinde denetlemeyi öğrenin.
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
ms.openlocfilehash: dcfa029f3feeafd9d75cd6cd19b36d32b0d5fce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951066"
---
# <a name="backtracking-in-regular-expressions"></a>Normal İfadelerde Geri Dönüş
<a name="top"></a> Geri izlemenin normal ifade deseni isteğe bağlı içerdiğinde gerçekleşir [miktar belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md) veya [değişim yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md), normal ifade altyapısı devam etmek için önceki kaydedilen bir duruma döndürür, bir eşleşme arayın. Geri izleme, normal ifadelerin gücü bakımından çok önemlidir; ifadelerin güçlü ve esnek olmasına ve çok karmaşık desenlerle eşleşmelerine olanak sağlar. Aynı zamanda, bu güç bir maliyetle birlikte gelir. Geri izleme, genellikle normal ifade altyapısının performansını etkileyen tek önemli etmendir. Neyse ki, geliştirici, normal ifade motorunun davranışını ve geri izlemeyi nasıl kullandığını denetleyebilir. Bu konu, geri izlemenin nasıl çalıştığını ve nasıl kontrol edilebileceğini açıklar.  
  
> [!NOTE]
>  Genel olarak, .NET normal ifade altyapısı gibi bir belirleyici olmayan sonlu Otomasyon (NFA) altyapısı sorumluluğunu geliştiriciye verimli ve hızlı normal ifadeler kaynaklı yerleştirir.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Geri izleme olmadan doğrusal karşılaştırma](#linear_comparison_without_backtracking)  
  
- [İsteğe bağlı miktar belirleyiciler veya değişim yapıları ile geri izleme oluşturur.](#backtracking_with_optional_quantifiers_or_alternation_constructs)  
  
- [İç içe geçmiş isteğe bağlı miktar Belirleyicilerle geri izleme](#backtracking_with_nested_optional_quantifiers)  
  
- [Geri izlemeyi denetleme](#controlling_backtracking)  
  
<a name="linear_comparison_without_backtracking"></a>   
## <a name="linear-comparison-without-backtracking"></a>Geri İzleme Olmadan Doğrusal Karşılaştırma  
 Bir normal ifade deseninin isteğe bağlı miktar niceleyicileri yoksa, normal ifade altyapısı doğrusal zamanda çalışır. Diğer bir deyişle, normal ifade altyapısı desendeki ilk dil öğesini giriş dizesindeki metinle eşleştirdikten sonra, it desende sonraki dil öğesini giriş dizesindeki sonraki karakterle veya karakter grubuyla eşleştirir. Bu, eşleştirme başarılı veya başarısız oluncaya kadar devam eder. Her iki durumda da, normal ifade altyapısı giriş dizesinde bir kerede bir karakter ilerler.  
  
 Aşağıdaki örnek, bir gösterim sağlar. Normal ifade `e{2}\w\b` herhangi bir sözcük karakteri ve ardından "e" harfi iki örneğini arar ve ardından bir sözcük sınırı.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 Bu normal ifade miktar Belirleyicisini içerse de `{2}`, doğrusal bir şekilde değerlendirilir. Normal ifade altyapısı için geri izleme yapmaz `{2}` bir isteğe bağlı miktar Belirleyicisi; değil bir tam sayı ve olmayan bir değişken sayısı önceki alt ifade ile eşleşmelidir belirtir. Sonuç olarak, normal ifade altyapısı, aşağıdaki tabloda gösterildiği gibi, normal ifade desenini giriş dizesiyle eşleştirmeye çalışır.  
  
|Çalışma|Desendeki konum|Dizedeki konum|Sonuç|  
|---------------|-------------------------|------------------------|------------|  
|1.|e|"needing a reed" (dizin 0)|Eşleşme yok.|  
|2|e|"eeding a reed" (dizin 1)|Olası eşleşme.|  
|3|E{2}|"eding a reed" (dizin 2)|Olası eşleşme.|  
|4|\w|"al gerekli" (dizin 3)|Olası eşleşme.|  
|5|\b|"ing a reed" (dizin 4)|Olası eşleşme başarısız olur.|  
|6|e|"eding a reed" (dizin 2)|Olası eşleşme.|  
|7|E{2}|"al gerekli" (dizin 3)|Olası eşleşme başarısız olur.|  
|8|e|"al gerekli" (dizin 3)|Eşleme başarısız olur.|  
|9|e|"ing a reed" (dizin 4)|Eşleşme yok.|  
|10|e|"ng a reed" (dizin 5)|Eşleşme yok.|  
|11|e|"g a reed" (dizin 6)|Eşleşme yok.|  
|12|e|"a reed" (dizin 7)|Eşleşme yok.|  
|13|e|"a reed" (dizin 8)|Eşleşme yok.|  
|14|e|"reed" (dizin 9)|Eşleşme yok.|  
|15|e|"reed" (dizin 10)|Eşleşme yok|  
|16|e|"eed" (dizin 11)|Olası eşleşme.|  
|17|E{2}|"ed" (dizin 12)|Olası eşleşme.|  
|18|\w|"d" (dizin 13)|Olası eşleşme.|  
|19|\b|"" (dizin 14)|Eşleşme.|  
  
 Bir normal ifade deseni isteğe bağlı miktar niceleyiciler veya değişim yapıları içermiyorsa, normal ifade desenini giriş dizesiyle eşleştirmek için gereken en fazla karşılaştırma sayısı, kabaca giriş dizesindeki karakter sayısına eşittir. Bu durumda, normal ifade altyapısı, 13 karakterlik bu dizedeki olası eşleşmeleri tanımlamak için 19 karşılaştırma kullanır.  Diğer bir deyişle, isteğe bağlı miktar niceleyiciler veya değişim yapıları içermiyorsa, normal ifade altyapısı doğrusala yakın bir zamanda çalışır.  
  
 [Başa dön](#top)  
  
<a name="backtracking_with_optional_quantifiers_or_alternation_constructs"></a>   
## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>İsteğe Bağlı Miktar Niceleyiciler veya Değişim Yapıları ile Geri İzleme  
 Normal bir ifade isteğe bağlı miktar niceleyiciler veya değişim yapıları içerdiğinde, giriş dizesinin değerlendirilmesi artık doğrusal değildir. Bir NFA altyapısıyla desen eşleştirme, giriş dizesinde eşleştirilecek karakterlerle değil, normal ifadedeki dil öğeleriyle yönlendirilir. Bu nedenle, normal ifade altyapısı, isteğe bağlı veya alternatif alt ifadeleri tam olarak eşleştirmeye çalışır. Alt ifadede sonraki dil öğesine ilerlediğinde ve eşleştirme başarısız olduğunda, normal ifade altyapısı, normal ifadeyi giriş dizesiyle bir bütün olarak eşleştirmek amacıyla, başarılı eşleştirmesinin bir bölümünü bırakır ve daha önce kaydedilen bir duruma geri döner. Bir eşleştirme bulmak üzere daha önce kaydedilen bir duruma bu şekilde geri dönme işlemi, geri izleme olarak bilinir.  
  
 Örneğin, normal ifade desenini düşünün `.*(es)`, "es" karakterleriyle ve tüm karakterleri, önünde bu. Aşağıdaki örnekte gösterildiği gibi, giriş dizesi "Essential services are provided by regular expressions." ise, desen, "expressions"daki "es"a kadar ve "es" dahil olmak üzere tüm dizeyle eşleşir.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 Bunu yapmak için, normal ifade altyapısı aşağıdaki gibi geri izlemeyi kullanır:  
  
- Eşleşecek `.*` (eşleşen sıfır, bir veya daha fazla tekrar herhangi bir karakterin) tüm giriş dizesiyle.  
  
- Normal ifade deseninde "e"yi eşleştirmeyi dener. Ancak, giriş dizesinde eşleştirilebilecek başka karakter kalmamıştır.  
  
- En son başarılı eşleştirmesi olan "Essential services are provided by regular expressions" dizesine geri izleme yapar ve "e"yi cümlenin sonundaki nokta ile eşleştirmeyi dener. Eşleştirme başarısız olur.  
  
- Geçici olarak eşleştirilen "Essential services are provided by regular expr" alt dizesine kadar, bir kerede bir karakter olacak şekilde, daha önceki başarılı bir eşleştirmeye geri izleme yapmaya devam eder. Ardından, desendeki "e"yi "expressions"daki ikinci "e" ile karşılaştırır ve bir eşleştirme bulur.  
  
- Desendeki "s" ile, eşleştirilen "e" karakterini izleyen "s"yi ("expressions"daki ilk "s") karşılaştırır. Eşleştirme başarılıdır.  
  
 Geri izleme kullandığınızda, normal ifade desenini 55 karakter uzunluğundaki giriş dizesiyle eşleştirmek, 67 karşılaştırma işlemi gerektirir. Genellikle, normal bir ifade deseninin tek bir değişim yapısı veya tek bir isteğe bağlı miktar niteleyicisi varsa, deseni eşleştirmek için gereken karşılaştırma işlemlerinin sayısı, giriş dizesindeki karakterlerin sayısının iki katıdır.  
  
 [Başa dön](#top)  
  
<a name="backtracking_with_nested_optional_quantifiers"></a>   
## <a name="backtracking-with-nested-optional-quantifiers"></a>İç İçe Geçmiş İsteğe Bağlı Miktar Niceleyicilerle Geri İzleme  
 Desen çok sayıda değişim yapıları içeriyorsa, iç içe değişim yapıları içeriyorsa veya en yaygın olasılık olarak iç içe isteğe bağlı miktar niceleyiciler içeriyorsa, normal bir ifade desenini eşleştirmek için gereken karşılaştırma işlemlerinin sayısı katlanarak artabilir. Örneğin, normal ifade deseni `^(a+)+$` bir veya daha fazla "a" karakteri içeren tam bir dizeyle eşleştirme için tasarlanmıştır. Örnek, aynı uzunlukta iki giriş dizesi sağlar, fakat yalnızca ilk dize desenle eşleşir. <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> Sınıfı, eşleştirme işleminin ne kadar süreceğini belirlemek için kullanılır.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 Örnekteki çıktının gösterdiği gibi, normal ifade altyapısının, bir giriş dizesinin desenle eşleşmediğini bulması, eşleşen bir dize tanımlamasına göre iki kat daha uzun sürdü. Bunun nedeni, başarısız bir eşleştirmenin her zaman bir kötü durum senaryosunu temsil etmesidir. Eşleştirmenin başarısız olduğu sonucuna varabilmesinden ve iç içe parantezlerin veri içinde birçok ek yol oluşturmasından önce, normal ifade altyapısının veri içinde olası tüm yolları izlemek için normal ifadeyi kullanması gerekir. Normal ifade altyapısı, aşağıdakileri yaparak ikinci dizenin desenle eşleşmediği sonucuna varır:  
  
- Dizenin başlangıcında olduğu ve ardından ilk beş eşleşme karakter dizesindeki deseni ile denetler `a+`. Ardından, dizede ek "a" karakteri grupları olmadığını belirler. Son olarak, dizenin sonu için sınama yapar. Dizede bir ek karakter kaldığından, eşleştirme başarısız olur. Bu hatalı eşleşme, 9 karşılaştırma gerektirir. Normal ifade altyapısı ayrıca, "a" (eşleştirme 1 olarak adlandırırız), "aa" (eşleştirme 2), "aaa" (eşleştirme 3) ve "aaaa" (eşleştirme 4) eşleştirmelerinden elde ettiği durum bilgisini de kaydeder.  
  
- Önceden kaydedilen eşleştirme 4'e döndürür. Ek bir yakalan gruba atamak için bir ek "a" karakteri olduğunu belirler. Son olarak, dizenin sonu için sınama yapar. Dizede bir ek karakter kaldığından, eşleştirme başarısız olur. Bu hatalı eşleşme 4 karşılaştırma gerektirir. Şu ana kadar toplam 13 karşılaştırma yapıldı.  
  
- Önceden kaydedilen eşleştirme 3 döndürür. Ek bir yakalanan gruba atamak için iki ek "a" karakteri olduğunu belirler. Ancak, dize sonu sınaması başarısız olur. Ardından, eşleştirme 3'e geri döner ve yakalanan iki ek gruptaki iki ek "a" karakterini eşleştirmeyi dener. Dize sonu sınaması hala başarısız olur. Bu başarısız eşleştirmeler 12 karşılaştırma gerektirir. Şu ana kadar toplam 25 karşılaştırma yapıldı.  
  
 Giriş dizesinin normal ifadeyle karşılaştırılması, normal ifade altyapısı tüm olası eşleştirme birleşimlerini deneyinceye kadar bu şekilde devam eder ve ardından eşleştirme olmadığı sonucuna ulaşır. İç içe geçmiş miktar belirleyiciler yüzünden, bu karşılaştırma bir O olduğu (2<sup>n</sup>) veya bir üstel işlemdir; burada *n* giriş dizesindeki karakterlerin sayısıdır. Bu, en kötü durumda, 30 karakterlik bir giriş dizesinin yaklaşık 1.073.741.824 karşılaştırma gerektirdiği ve 40 karakterlik bir giriş dizesinin yaklaşık 1,099,511,627,776 karşılaştırma gerektirdiği anlamına gelir. Bu uzunluklarda veya daha uzun dizeler kullanırsanız, normal ifade deseniyle eşleşmeyen giriş işlediklerinde, normal ifade yöntemlerinin tamamlanması çok uzun zaman alabilir.  
  
 [Başa dön](#top)  
  
<a name="controlling_backtracking"></a>   
## <a name="controlling-backtracking"></a>Geri İzlemeyi Denetleme  
 Geri izleme, güçlü ve esnek normal ifadeler oluşturmanıza olanak tanır. Ancak, önceki bölümde gösterildiği gibi, bu yararlar kabuk edilemeyecek kadar düşük performansla eşleştirilebilir. Başlattığınızda aşırı geri izleme yapılmasını önlemek için bir zaman aşımı aralığı tanımlamanız bir <xref:System.Text.RegularExpressions.Regex> nesne veya statik bir normal ifade eşleştirme yöntemi çağırın. Bu konu, sonraki bölümde açıklanmaktadır. Ayrıca, .NET, veya ve karmaşık normal ifadeleri çok az kayıpla veya hiç performans cezası ile destekleyen üç normal ifade dil öğesini destekler: [geri dönüşlü olmayan alt ifadeler](#Nonbacktracking), [geriye yönelik onaylar](#Lookbehind), ve [ileriye yönelik onaylar](#Lookahead). Her dil öğesi hakkında daha fazla bilgi için bkz: [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
<a name="Timeout"></a>   
### <a name="defining-a-time-out-interval"></a>Bir Zaman Aşımı Aralığı Tanımlama  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], normal ifade altyapısının, denemeden Vazgeçmeden ve önce tek bir eşleştirme için arama yapacağı en uzun aralığı gösteren bir zaman aşımı değeri ayarlayabilirsiniz bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> özel durum. Sağlayarak zaman aşımı aralığı belirttiğiniz bir <xref:System.TimeSpan> değerini <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> örnek normal ifadeler için oluşturucu. Ayrıca, her bir statik desen eşleştirme yönteminin bir aşırı yüklemesi vardır bir <xref:System.TimeSpan> parametresi bir zaman aşımı değeri belirtmenize olanak tanır. Varsayılan olarak, zaman aşımı aralığı ayarlamak <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> ve normal ifade altyapısı zaman aşımına uğramaz.  
  
> [!IMPORTANT]
>  Normal ifadeniz geri izlemeye dayalıysa, her zaman bir zaman aşımı aralığı ayarlamanızı öneririz.  
  
 A <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> özel durum gösterir ve normal ifade altyapısının belirtilen zaman aşımı aralığı içinde bir eşleşme bulamadı ancak özel durumun neden anlamına gelmez. Bunun nedeni aşırı geri izleme olabilir, fakat özel durumun oluştuğu zamandaki sistem yükü nedeniyle zaman aşımı aralığı çok düşük ayarlanmış da olabilir. Özel durumu işlediğinizde, giriş dizesiyle diğer eşleştirmeleri bırakmayı veya zaman aşımı aralığını artırarak eşleştirme işlemini yeniden denemeyi seçebilirsiniz.  
  
 Örneğin, aşağıdaki çağrıları kod <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> örneği oluşturmak için oluşturucu bir <xref:System.Text.RegularExpressions.Regex> bir saniyelik zaman aşımı değerini içeren nesne. Normal ifade deseni `(a+)+$`, bir veya daha fazla "a" karakteri bir satırın sonunda bir veya daha fazla dizileri eşleşen olduğu aşırı geri izlemeye maruz kalır. Varsa bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> olduğu durum, örnek en fazla üç saniye cinsinden zaman aşımı değerini artırır. Bundan sonra, deseni eşleştirme girişiminden vazgeçer.  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  
  
<a name="Nonbacktracking"></a>   
### <a name="nonbacktracking-subexpression"></a>Geri İzlemeli Olmayan Alt İfade  
 `(?>` *Subexpression* `)` dil öğesi bir alt ifadede geri izlemeyi bastırır. Başarısız eşleştirmelerle ilişkili performans sorunlarını önlemek için yararlıdır.  
  
 Aşağıdaki örnekte, iç içe miktar niceleyiciler kullanılırken geri izlemenin bastırılmasının performansı nasıl iyileştirdiği gösterilmektedir. Normal ifade altyapısının bir giriş dizesinin iki normal ifadeyle eşleşmediğini belirlemesi için gereken süreyi ölçer. İlk normal ifade, ardından bir iki nokta işareti, ardından bir veya daha fazla ondalık basamak, ardından iki iki nokta işareti gelen bir veya birden fazla ondalık basamağın bir veya birden fazla örneğini içeren bir dizeyle eşleştirme yapmayı denemek için geri izleme kullanır. İkinci normal ifade, geri izlemeyi devre dışı bırakması dışında, birincisiyle aynıdır. Örnekteki çıktının gösterdiği gibi, geri izlemeyi devre dışı bırakmanın sağladığı performans iyileşmesi önemlidir.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  
  
<a name="Lookbehind"></a>   
### <a name="lookbehind-assertions"></a>Geriye Yönelik Onaylar  
 .NET içeren iki dil öğesi `(?<=` *subexpression* `)` ve `(?<!` *subexpression*`)`, önceki karakterle veya karakterlerle eşleşen Giriş dizesi. Her iki dil öğesi de sıfır genişlikli onaylardır; diğer bir deyişle, bunlar geçerli karakter hemen önce gelen karakterin veya eşleştirilip olup olmadığını belirlemek *subexpression*karakterlerin ilerlemeden veya geri izleme yapmadan.  
  
 `(?<=` *alt ifade* `)` bir pozitif geriye yönelik onaydır; yani karakteri veya karakterleri geçerli konumu eşleşmelidir önce olduğundan *subexpression*. `(?<!`*alt ifade* `)` bir negatif geriye yönelik onaydır; yani karakteri veya karakterleri geçerli konumu eşleşmemelidir önce olduğundan *subexpression*. Her iki pozitif ve negatif geriye yönelik onaylar olduğunda en kullanışlı *subexpression* önceki alt ifade bir alt kümesidir.  
  
 Aşağıdaki örnek, bir e-posta adresi kullanıcı adını doğrulayan iki denk normal ifade deseni kullanır. Birinci desen, aşırı geri izleme nedeniyle yetersiz performansa maruz kalır. İkinci desen, iç içe bir miktar niteleyiciyi pozitif bir geriye yönelik onayla değiştirerek birinci normal ifadeyi değiştirir. Örnekteki çıktının yürütme zamanını görüntüler <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 Birinci normal ifade deseni `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`, aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin Bu karşılaştırma büyük/küçük harfe, çünkü <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği.|  
|`[-.\w]*`|Bir kısa çizgi, nokta veya sözcük karakterinin sıfır, bir veya daha fazla örneğini eşleştirin.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin|  
|`([-.\w]*[0-9A-Z])*`|Ardından alfasayısal bir karakter gelen sıfır veya daha fazla kısa çizgi, nokta veya sözcük karakteri birleşiminin sıfır veya daha fazla örneğini eşleştirin. Bu ilk yakalama grubudur.|  
|`@`|Eşleşme bir at işareti ("\@").|  
  
 İkinci normal ifade deseni `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`, pozitif bir geriye yönelik onay kullanır. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin Bu karşılaştırma büyük/küçük harfe, çünkü <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği.|  
|`[-.\w]*`|Bir kısa çizgi, nokta veya sözcük karakterinin sıfır, bir veya daha fazla örneğini eşleştirin.|  
|`(?<=[0-9A-Z])`|Son eşleşen karaktere geriye doğru bakın ve alfasayısal ise eşleştirmeyi devam ettirin. Alfasayısal karakterlerin, nokta, kısa çizgi ve tüm sözcük karakterlerinden oluşan kümenin bir alt kümesi olduğunu unutmayın.|  
|`@`|Eşleşme bir at işareti ("\@").|  
  
<a name="Lookahead"></a>   
### <a name="lookahead-assertions"></a>İleriye Yönelik Onaylar  
 .NET içeren iki dil öğesi `(?=` *subexpression* `)` ve `(?!` *subexpression*`)`, sonraki karakterle veya karakterlerle eşleşen Giriş dizesi. Her iki dil öğesi de sıfır genişlikli onaylardır; diğer bir deyişle, bunlar geçerli karakterden hemen izleyen karakterin veya eşleştirilip olup olmadığını belirlemek *subexpression*karakterlerin ilerlemeden veya geri izleme yapmadan.  
  
 `(?=` *alt ifade* `)` geçerli konumu eşleşmelidir sonra bir pozitif ileriye yönelik onaydır; yani karakterin veya karakter olduğu *subexpression*. `(?!`*alt ifade* `)` geçerli konumu eşleşmemelidir sonra bir negatif ileriye yönelik onaydır; yani karakterin veya karakter olduğu *subexpression*. Her iki pozitif ve negatif ileriye yönelik onaylar olduğunda en kullanışlı *subexpression* sonraki alt ifade bir alt kümesidir.  
  
 Aşağıdaki örnekte, tam olarak belirtilen bir tür adını doğrulayan iki denk normal ifade deseni kullanılmaktadır. Birinci desen, aşırı geri izleme nedeniyle yetersiz performansa maruz kalır. İkincisi, iç içe bir miktar niteleyiciyi pozitif bir ileriye yönelik onayla değiştirerek birinci normal ifadeyi değiştirir. Örnekteki çıktının yürütme zamanını görüntüler <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 Birinci normal ifade deseni `^(([A-Z]\w*)+\.)*[A-Z]\w*$`, aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`([A-Z]\w*)+\.`|Ardından bir nokta gelen sıfır veya daha fazla sözcük karakterinin bir veya birden çok kez ardından geldiği bir alfabetik karakterle (A-Z) eşleştirin. Bu karşılaştırma büyük/küçük harfe, çünkü <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği.|  
|`(([A-Z]\w*)+\.)*`|Önceki desenle sıfır veya daha çok kez eşleştirin.|  
|`[A-Z]\w*`|Ardından sıfır veya daha fazla karakter gelen alfabetik bir karakterle eşleştirin.|  
|`$`|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 İkinci normal ifade deseni `^((?=[A-Z])\w+\.)*[A-Z]\w*$`, pozitif bir ileriye yönelik onay kullanır. Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Eşleştirmeyi dizenin başlangıcında başlatın.|  
|`(?=[A-Z])`|İleriye yönelik olarak birinci karaktere bakın ve alfabetik (A-Z) ise eşleştirmeyi devam ettirin. Bu karşılaştırma büyük/küçük harfe, çünkü <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> seçeneği.|  
|`\w+\.`|Ardından bir nokta gelen bir veya daha fazla sözcük karakterini eşleştirin.|  
|`((?=[A-Z])\w+\.)*`|Ardından sıfır veya daha çok kez bir nokta gelen bir veya birden çok sözcük karakteri desenini eşleştirin. İlk sözcük karakterinin alfabetik olması gerekir.|  
|`[A-Z]\w*`|Ardından sıfır veya daha fazla karakter gelen alfabetik bir karakterle eşleştirin.|  
|`$`|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 [Başa dön](#top)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Niceleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)
- [Değişim Yapıları](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)
- [Gruplama Yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)

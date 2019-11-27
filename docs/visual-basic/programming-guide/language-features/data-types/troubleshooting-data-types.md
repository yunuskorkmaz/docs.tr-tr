---
title: Veri Türleri Sorunlarını Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 63b2513e420320742bf7e25314743f08404f46a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350507"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Veri Türleri Sorunlarını Giderme (Visual Basic)

Bu sayfada, iç veri türlerinde işlem gerçekleştirdiğinizde oluşabilecek bazı yaygın sorunlar listelenmektedir.

## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Kayan nokta Ifadeleri eşit olarak karşılaştırmaz

Kayan nokta numaralarıyla ([tek veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md)) çalışırken, bunların ikili kesirler olarak depolandığını unutmayın. Bu, ikili bir kesir olmayan miktarın (k/(2 ^ n) (k ve n tamsayıların tamsayılar) tam bir temsilini tutamayacağı anlamına gelir. Örneğin, 0,5 (= 1/2) ve 0,3125 (= 5/16) kesin değerler olarak tutulabilir, ancak 0,2 (= 1/5) ve 0,3 (= 3/10) yalnızca yaklaştırmalar olabilir.

Bu noktasında kesinlik eksikliği nedeniyle, kayan nokta değerlerinde işlem yaparken tam sonuçlara güvenebilirsiniz. Özellikle, teorik olarak eşit olan iki değerin biraz farklı gösterimleri olabilir.

| Kayan nokta miktarlarını karşılaştırmak için |
|---|
|1. <xref:System> ad alanındaki <xref:System.Math> sınıfının <xref:System.Math.Abs%2A> yöntemini kullanarak farkının mutlak değerini hesaplayın.<br />2. kabul edilebilir en yüksek farkı, aralarındaki fark daha büyük değilse pratik amaçlar için eşit olacak şekilde düşünebileceğiniz bir maksimum fark saptayın.<br />3. farkın mutlak değerini kabul edilebilir fark ile karşılaştırın.|

Aşağıdaki örnek, iki `Double` değerinin hem yanlış hem de doğru karşılaştırmasını gösterir.

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

Önceki örnekte, `CStr` anahtar sözcüğünün kullandığından daha iyi bir duyarlık belirleyebilmesi için <xref:System.Double> yapısının <xref:System.Double.ToString%2A> yöntemi kullanılmaktadır. Varsayılan değer 15 haneye sahiptir, ancak "G17" biçimi bunu 17 basamağa genişletir.

## <a name="mod-operator-does-not-return-accurate-result"></a>Mod Işleci doğru sonucu döndürmüyor

Kayan nokta depolama noktasında kesinlik eksikliği nedeniyle, en az bir işlenenin kayan nokta olduğu durumlarda [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md) beklenmeyen bir sonuç döndürebilir.

[Decimal veri türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) kayan nokta gösterimini kullanmaz. `Single` ve `Double` çok fazla sayıda sayı `Decimal`. (örneğin, 0,2 ve 0,3). Aritmetik, kayan noktalı `Decimal` daha yavaş olsa da, daha iyi duyarlık elde etmek için performansın azalmasına değer verebilir.

|Kayan noktalı miktarların tamsayı geri kalanını bulmak için|
|---|
|1. değişkenleri `Decimal`olarak bildirin.<br />2. değişmez değer türü karakter `D`, değerlerin `Long` veri türü için çok büyük olması olasılığına karşı, `Decimal`olarak sabitlerini zorlamak için kullanın.|

Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir.

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

Önceki örnekte, `CStr` anahtar sözcüğünün kullandığından daha iyi bir duyarlık belirleyebilmesi için <xref:System.Double> yapısının <xref:System.Double.ToString%2A> yöntemi kullanılmaktadır. Varsayılan değer 15 haneye sahiptir, ancak "G17" biçimi bunu 17 basamağa genişletir.

`zeroPointTwo` `Double`olduğundan, 0,2 için değeri, depolanan değeri 0.20000000000000001 olan sonsuz bir yinelenen ikili kesirdir. 2,0 bu miktara göre bölmek, 0.19999999999999991 'nin geri kalanı ile 9.9999999999999995 verir.

`decimalRemainder`ifadesinde, değişmez değer türü karakter `D` her iki işleneni de `Decimal`zorlar ve 0,2 kesin bir gösterimine sahiptir. Bu nedenle `Mod` işleci, 0,0 'in beklenen geri kalanını verir.

`decimalRemainder` `Decimal`olarak bildirmek için yeterli olmadığına unutmayın. Ayrıca, değişmez değerleri `Decimal`zorlamanız gerekir veya varsayılan olarak `Double` kullanırlar `decimalRemainder` aynı yanlış değeri `doubleRemainder`olarak alır.

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boole türü, doğru şekilde sayısal türe dönüştürülmüyor

[Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) değerleri sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır. Önceki sürümlerle uyumluluk için Visual Basic, `Boolean` ve sayısal türler arasında dönüştürme yapmak üzere dönüştürme anahtar kelimeleri ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`vb.) sağlar. Ancak, diğer diller bazen .NET Framework Yöntemler gibi bu dönüştürmeleri farklı şekilde gerçekleştirebilir.

`True` ve `False`için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız gerekir. Mümkün olduğunda, `Boolean` değişkenlerinin kullanımını, tasarlandıkları mantıksal değerlerle kısıtlamalısınız. `Boolean` ve sayısal değerleri karıştırmanız gerekiyorsa, seçtiğiniz dönüştürme yöntemini anladığınızdan emin olun.

### <a name="conversion-in-visual-basic"></a>Visual Basic dönüştürme

Sayısal veri türlerini `Boolean`dönüştürmek için `CType` veya `CBool` dönüştürme anahtar sözcüklerini kullandığınızda 0 `False` olur ve diğer tüm değerler `True`olur. Dönüştürme anahtar sözcüklerini kullanarak `Boolean` değerlerini sayısal türlere dönüştürdüğünüzde, `False` 0 olur ve `True`-1 olur.

### <a name="conversion-in-the-framework"></a>Çerçevede dönüştürme

<xref:System> ad alanındaki <xref:System.Convert> sınıfının <xref:System.Convert.ToInt32%2A> yöntemi `True` + 1 ' e dönüştürür.

Bir `Boolean` değerini sayısal veri türüne dönüştürmeniz gerekiyorsa, kullandığınız dönüştürme yöntemiyle ilgili dikkatli olun.

## <a name="character-literal-generates-compiler-error"></a>Karakter sabit değeri derleyici hatası oluşturuyor

Herhangi bir tür karakteri yokluğunda Visual Basic, değişmez değerler için varsayılan veri türlerini varsayar. Bir karakter sabiti için varsayılan tür, tırnak işaretleri (`" "`) gibi) `String`.

`String` veri türü, [char veri türüne](../../../../visual-basic/language-reference/data-types/char-data-type.md)genişlemez. Yani, bir `Char` değişkenine bir sabit değer atamak istiyorsanız, bir daraltma dönüştürmesi yapmanız veya hazır değeri `Char` türüne zorlamanız gerekir.

|Bir değişkene veya sabitine atanacak bir Char sabit değeri oluşturmak için|
|---|
|1. değişkeni veya sabiti `Char`olarak bildirin.<br />2. karakter değerini tırnak işaretleri (`" "`) içine alın.<br />3. hazır değeri `Char`zorlamak için `C` değişmez değer türü karakteriyle birlikte kapanış çift tırnak işaretini izleyin. Bu, tür denetimi anahtarı ([Option Strict deyimin](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `On`ve herhangi bir durumda istense gereklidir.|

Aşağıdaki örnek, `Char` değişkenine bir sabit değerin hem başarısız hem de başarılı atamalarını gösterir.

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

Çalışma zamanında başarısız olabileceğinden daraltma dönüştürmeleri kullanılırken her zaman bir risk vardır. Örneğin, `String` değeri birden fazla karakter içeriyorsa, `String` `Char` ' dan bir dönüştürme başarısız olabilir. Bu nedenle, `C` türü karakteri kullanmak daha iyi bir programdır.

## <a name="string-conversion-fails-at-run-time"></a>Çalışma zamanında dize dönüştürme başarısız oluyor

[Dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) , çok az genişleyen dönüşümlere katılır. widens yalnızca kendine ve `Object``String` ve yalnızca `Char` ve `Char()` (`Char` dizi) `String`için genişlemez. Bunun nedeni, `String` değişkenlerinin ve sabitlerin diğer veri türlerinin içeremeyeceği değerleri içerebildiği bir.

Tür denetleme anahtarı ([Option Strict deyimin](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `On`, derleyici tüm örtük daraltma dönüştürmelerine izin vermez. Bu, `String`ilgili olanları içerir. Kodunuz, dönüştürmeyi denemek için .NET Framework yönlendirecek `CStr` ve [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)gibi dönüştürme anahtar sözcüklerini kullanmaya devam edebilir.

> [!NOTE]
> Daraltma dönüştürme hatası, bir `For Each…Next` koleksiyonundaki öğelerden döngü denetim değişkenine dönüşümler için bastırılır. Daha fazla bilgi ve örnek için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).

### <a name="narrowing-conversion-protection"></a>Daraltma dönüştürme koruması

Daraltma dönüştürmelerinden sakıncası çalışma zamanında başarısız olabilir. Örneğin, bir `String` değişkeni "true" veya "false" dışında bir şey içeriyorsa, bu, `Boolean`dönüştürülemez. Noktalama karakterleri içeriyorsa, herhangi bir sayısal türe dönüştürme başarısız olur. `String` değişkeninizin her zaman hedef türün kabul edebileceği değerleri tuttuğunda, dönüştürmeyi denememelisiniz.

`String` ' den başka bir veri türüne dönüştürmeniz gerekiyorsa, en güvenli yordam, denemeye yapılan dönüştürmeyi TRY... içine almaktır [. Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Bu, bir çalışma zamanı hatasıyla ilgilenmenizi sağlar.

### <a name="character-arrays"></a>Karakter dizileri

Tek bir `Char` ve `Char` öğelerinden oluşan dizi `String`için de genişledir. Ancak, `String` `Char()`olarak genişlemez. Bir `String` değerini `Char` dizisine dönüştürmek için <xref:System.String?displayProperty=nameWithType> sınıfının <xref:System.String.ToCharArray%2A> yöntemini kullanabilirsiniz.

### <a name="meaningless-values"></a>Anlamlı değerler

Genel olarak, `String` değerleri diğer veri türlerinde anlamlı değildir ve dönüştürme yüksek oranda yapay ve tehlikeli olur. Mümkün olduğunda, `String` değişkenlerinin kullanımını, tasarlandıkları karakter dizileri ile kısıtlamalısınız. Başka türlerdeki eşdeğer değerlere bağlı olmayan hiçbir kodu asla yazmamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

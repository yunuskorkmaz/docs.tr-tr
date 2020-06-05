---
title: Veri Türü Sorunlarını Giderme
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
ms.openlocfilehash: 239e1c2f908a9023aeca6e92aff4633b60f27b69
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393409"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Veri Türleri Sorunlarını Giderme (Visual Basic)

Bu sayfada, iç veri türlerinde işlem gerçekleştirdiğinizde oluşabilecek bazı yaygın sorunlar listelenmektedir.

## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Kayan nokta Ifadeleri eşit olarak karşılaştırmaz

Kayan nokta numaralarıyla ([tek veri türü](../../../language-reference/data-types/single-data-type.md) ve [Double veri türü](../../../language-reference/data-types/double-data-type.md)) çalışırken, bunların ikili kesirler olarak depolandığını unutmayın. Bu, ikili bir kesir olmayan miktarın (k/(2 ^ n) (k ve n tamsayıların tamsayılar) tam bir temsilini tutamayacağı anlamına gelir. Örneğin, 0,5 (= 1/2) ve 0,3125 (= 5/16) kesin değerler olarak tutulabilir, ancak 0,2 (= 1/5) ve 0,3 (= 3/10) yalnızca yaklaştırmalar olabilir.

Bu noktasında kesinlik eksikliği nedeniyle, kayan nokta değerlerinde işlem yaparken tam sonuçlara güvenebilirsiniz. Özellikle, teorik olarak eşit olan iki değerin biraz farklı gösterimleri olabilir.

| Kayan nokta miktarlarını karşılaştırmak için |
|---|
|1. <xref:System.Math.Abs%2A> <xref:System.Math> ad alanındaki sınıfının yöntemini kullanarak farkının mutlak değerini hesaplayın <xref:System> .<br />2. kabul edilebilir en yüksek farkı, aralarındaki fark daha büyük değilse pratik amaçlar için eşit olacak şekilde düşünebileceğiniz bir maksimum fark saptayın.<br />3. farkın mutlak değerini kabul edilebilir fark ile karşılaştırın.|

Aşağıdaki örnek, iki değerin hem yanlış hem de doğru karşılaştırmasını gösterir `Double` .

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

Önceki örnek, <xref:System.Double.ToString%2A> <xref:System.Double> anahtar sözcüğünün kullandığından daha iyi bir duyarlık belirleyebilmesi için yapının yöntemini kullanır `CStr` . Varsayılan değer 15 haneye sahiptir, ancak "G17" biçimi bunu 17 basamağa genişletir.

## <a name="mod-operator-does-not-return-accurate-result"></a>Mod Işleci doğru sonucu döndürmüyor

Kayan nokta depolama noktasında kesinlik eksikliği nedeniyle, en az bir işlenenin kayan nokta olduğu durumlarda [Mod işleci](../../../language-reference/operators/mod-operator.md) beklenmeyen bir sonuç döndürebilir.

[Decimal veri türü](../../../language-reference/data-types/decimal-data-type.md) kayan nokta gösterimini kullanmaz. Ve ' de tam olarak tam sayılar `Single` `Double` `Decimal` (örneğin, 0,2 ve 0,3). Aritmetik, kayan nokta bakımından daha yavaş olsa da `Decimal` , daha iyi bir duyarlık elde etmek için performansın azalmasına değer verebilir.

|Kayan noktalı miktarların tamsayı geri kalanını bulmak için|
|---|
|1. değişkenleri olarak bildirin `Decimal` .<br />2. değişmez değer türü karakterini, `D` `Decimal` değerlerinin, veri türü için çok büyük olması olasılığına karşı, değerlerini zorlamak için kullanın `Long` .|

Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir.

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

Önceki örnek, <xref:System.Double.ToString%2A> <xref:System.Double> anahtar sözcüğünün kullandığından daha iyi bir duyarlık belirleyebilmesi için yapının yöntemini kullanır `CStr` . Varsayılan değer 15 haneye sahiptir, ancak "G17" biçimi bunu 17 basamağa genişletir.

Olduğundan `zeroPointTwo` `Double` , 0,2 için değeri, depolanan bir 0.20000000000000001 değeri olan sonsuz bir yinelenen ikili kesirdir. 2,0 bu miktara göre bölmek, 0.19999999999999991 'nin geri kalanı ile 9.9999999999999995 verir.

İfadesinde `decimalRemainder` , değişmez değer türü karakteri `D` her iki işleneni olarak zorlar `Decimal` ve 0,2 kesin bir gösterimine sahiptir. Bu nedenle, `Mod` işleç beklenen 0,0 kalanı verir.

Olarak bildirmek için yeterli olmadığına unutmayın `decimalRemainder` `Decimal` . Ayrıca, değişmez değerleri için de zorlamanız gerekir `Decimal` ya da `Double` Varsayılan olarak kullanır ve `decimalRemainder` aynı yanlış değeri ile aynı şekilde alır `doubleRemainder` .

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boole türü, doğru şekilde sayısal türe dönüştürülmüyor

[Boole veri türü](../../../language-reference/data-types/boolean-data-type.md) değerleri sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır. Önceki sürümlerle uyumluluk için Visual Basic,[CType Function](../../../language-reference/functions/ctype-function.md) `CBool` `CInt` `Boolean` ve sayısal türleri dönüştürmek için dönüştürme anahtar sözcükleri (CType işlevi,,, vb.) sağlar. Ancak, diğer diller bazen .NET Framework Yöntemler gibi bu dönüştürmeleri farklı şekilde gerçekleştirebilir.

Ve için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız `True` gerekir `False` . Mümkün olduğunda, `Boolean` değişkenlerin kullanımını tasarlandıkları mantıksal değerlerle kısıtlamalısınız. Değer karıştırmanız `Boolean` ve sayısal değerler gerekiyorsa, seçtiğiniz dönüştürme yöntemini anladığınızdan emin olun.

### <a name="conversion-in-visual-basic"></a>Visual Basic dönüştürme

`CType` `CBool` Sayısal veri türlerini öğesine dönüştürmek için veya dönüştürme anahtar sözcüklerini kullandığınızda `Boolean` 0 olur `False` ve diğer tüm değerler olur `True` . `Boolean`Dönüştürme anahtar sözcüklerini kullanarak değerleri sayısal türlere dönüştürdüğünüzde `False` 0 olur ve `True` -1 olur.

### <a name="conversion-in-the-framework"></a>Çerçevede dönüştürme

<xref:System.Convert.ToInt32%2A> <xref:System.Convert> <xref:System> Ad alanındaki sınıfının yöntemi `True` + 1 ' e dönüştürülür.

Bir `Boolean` değeri sayısal veri türüne dönüştürmeniz gerekiyorsa kullandığınız dönüştürme yöntemiyle ilgili dikkatli olun.

## <a name="character-literal-generates-compiler-error"></a>Karakter sabit değeri derleyici hatası oluşturuyor

Herhangi bir tür karakteri yokluğunda Visual Basic, değişmez değerler için varsayılan veri türlerini varsayar. Bir karakter sabiti için varsayılan tür, tırnak işaretleri ( `" "` ) — olur `String` .

`String`Veri türü, [char veri türüne](../../../language-reference/data-types/char-data-type.md)genişlemez. Yani, bir değişkene bir sabit değer atamak istiyorsanız `Char` , bir daraltma dönüştürmesi yapmanız veya sabit değeri türe zorlamanız gerekir `Char` .

|Bir değişkene veya sabitine atanacak bir Char sabit değeri oluşturmak için|
|---|
|1. değişkeni veya sabiti olarak bildirin `Char` .<br />2. karakter değerini tırnak işaretleri () içine alın `" "` .<br />3. `C` sabit değere zorlamak için sabit değer türü karakteriyle birlikte kapanış çift tırnak işaretini izleyin `Char` . Tür denetimi anahtarı ([Option Strict deyimdir](../../../language-reference/statements/option-strict-statement.md)) ise bu gereklidir `On` ve herhangi bir durumda istenebilir.|

Aşağıdaki örnek, bir değişken için hem başarısız hem de başarılı bir sabit değer atamalarını gösterir `Char` .

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

Çalışma zamanında başarısız olabileceğinden daraltma dönüştürmeleri kullanılırken her zaman bir risk vardır. Örneğin, `String` `Char` değeri birden fazla karakter içeriyorsa, öğesinden bir dönüştürme başarısız olabilir `String` . Bu nedenle, tür karakterini kullanmak daha iyi bir programdır `C` .

## <a name="string-conversion-fails-at-run-time"></a>Çalışma zamanında dize dönüştürme başarısız oluyor

[Dize veri türü](../../../language-reference/data-types/string-data-type.md) , çok az genişleyen dönüşümlere katılır. `String`widens yalnızca kendi kendine ve `Object` ' a ve `Char` `Char()` (bir `Char` dizi) öğesini olarak Genişlet `String` . Bunun nedeni, `String` değişkenlerin ve sabitlerin diğer veri türlerinin içeremeyeceği değerleri içerebildiği bir.

Tür denetleme anahtarı ([Option Strict deyimin](../../../language-reference/statements/option-strict-statement.md)) olduğunda `On` , derleyici tüm örtük daraltma dönüştürmelerine izin vermez. Bu, ilgili olanları içerir `String` . Kodunuz `CStr` ve [CType işlevi](../../../language-reference/functions/ctype-function.md)gibi dönüştürme anahtar sözcüklerini kullanmaya devam edebilir, bu da dönüştürmeyi denemek için .NET Framework yönlendirir.

> [!NOTE]
> Daraltma dönüştürme hatası, bir `For Each…Next` koleksiyondaki öğelerden döngü denetim değişkenine dönüşümler için bastırılır. Daha fazla bilgi ve örnek için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](../../../language-reference/statements/for-each-next-statement.md).

### <a name="narrowing-conversion-protection"></a>Daraltma dönüştürme koruması

Daraltma dönüştürmelerinden sakıncası çalışma zamanında başarısız olabilir. Örneğin, bir `String` değişken "true" veya "false" dışında bir şey içeriyorsa, öğesine dönüştürülemez `Boolean` . Noktalama karakterleri içeriyorsa, herhangi bir sayısal türe dönüştürme başarısız olur. `String`Değişkeninizin hedef türün kabul edebileceği değerleri tuttuğundan haberdar olmadığınız takdirde, dönüştürmeyi denememelisiniz.

`String`' Den başka bir veri türüne dönüştürmeniz gerekiyorsa, en güvenli yordam TRY dönüştürme denemesi Için [TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md). Bu, bir çalışma zamanı hatasıyla ilgilenmenizi sağlar.

### <a name="character-arrays"></a>Karakter dizileri

Tek bir `Char` ve öğelerinden oluşan bir dizi `Char` her ikisi de olarak `String` . Ancak, `String` olarak genişlemez `Char()` . Bir `String` değeri diziye dönüştürmek için `Char` , <xref:System.String.ToCharArray%2A> sınıfının yöntemini kullanabilirsiniz <xref:System.String?displayProperty=nameWithType> .

### <a name="meaningless-values"></a>Anlamlı değerler

Genel olarak, `String` değerler diğer veri türlerinde anlamlı değildir ve dönüştürme yüksek oranda yapay ve tehlikeli olur. Mümkün olduğunda, `String` değişkenlerin kullanımını tasarlandıkları karakter dizileri ile kısıtlamalısınız. Başka türlerdeki eşdeğer değerlere bağlı olmayan hiçbir kodu asla yazmamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Tür Karakterleri](type-characters.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../language-reference/functions/type-conversion-functions.md)
- [Veri Türlerinin Etkili Kullanımı](efficient-use-of-data-types.md)

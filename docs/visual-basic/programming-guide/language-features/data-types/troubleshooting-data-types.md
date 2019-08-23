---
title: Veri Türleri Sorunlarını Giderme (Visual Basic)
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
ms.openlocfilehash: 5b2cb0d5270b7e14c3462aeaf54942f939511fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933226"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Veri Türleri Sorunlarını Giderme (Visual Basic)
Bu sayfada, iç veri türlerinde işlem gerçekleştirdiğinizde oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Kayan nokta Ifadeleri eşit olarak karşılaştırmaz  
 Kayan nokta numaralarıyla ([tek veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md)) çalışırken, bunların ikili kesirler olarak depolandığını unutmayın. Bu, ikili bir kesir olmayan miktarın (k/(2 ^ n) (k ve n tamsayıların tamsayılar) tam bir temsilini tutamayacağı anlamına gelir. Örneğin, 0,5 (= 1/2) ve 0,3125 (= 5/16) kesin değerler olarak tutulabilir, ancak 0,2 (= 1/5) ve 0,3 (= 3/10) yalnızca yaklaştırmalar olabilir.  
  
 Bu noktasında kesinlik eksikliği nedeniyle, kayan nokta değerlerinde işlem yaparken tam sonuçlara güvenebilirsiniz. Özellikle, teorik olarak eşit olan iki değerin biraz farklı gösterimleri olabilir.  
  
| Kayan nokta miktarlarını karşılaştırmak için | 
|---| 
|1.  Ad alanındaki <xref:System.Math.Abs%2A> <xref:System.Math> sınıfının yöntemini kullanarak farkıdaki mutlak değeri hesaplayın. <xref:System><br />2.  Farkları daha büyük değilse, pratik amaçlar için iki miktarı eşit olacak şekilde düşünebileceğiniz kabul edilebilir maksimum farkı belirleme.<br />3.  Farkın mutlak değerini kabul edilebilir farkla karşılaştırın.|  
  
 Aşağıdaki örnek, iki `Double` değerin hem yanlış hem de doğru karşılaştırmasını gösterir.  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 Önceki örnek, <xref:System.Double.ToString%2A> `CStr` anahtar sözcüğünün kullandığından daha iyi <xref:System.Double> bir duyarlık belirleyebilmesi için yapının yöntemini kullanır. Varsayılan değer 15 haneye sahiptir, ancak "G17" biçimi bunu 17 basamağa genişletir.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod Işleci doğru sonucu döndürmüyor  
 Kayan nokta depolama noktasında kesinlik eksikliği nedeniyle, en az bir işlenenin kayan nokta olduğu durumlarda [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md) beklenmeyen bir sonuç döndürebilir.  
  
 [Decimal veri türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) kayan nokta gösterimini kullanmaz. Ve `Single` `Double` 'detamolaraktamsayılar(örneğin,0,2`Decimal` ve 0,3). Aritmetik, kayan nokta bakımından `Decimal` daha yavaş olsa da, daha iyi bir duyarlık elde etmek için performansın azalmasına değer verebilir.  
  
|Kayan noktalı miktarların tamsayı geri kalanını bulmak için|  
|---|  
|1.  Değişkenleri olarak `Decimal`bildirin.<br />2.  Değerleri `Decimal`, `Long` veri türü için `D` çok büyük olması durumunda, değişmez değer türü karakterini ' ya zorlamak için kullanın.|  
  
 Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir.  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 Önceki örnek, <xref:System.Double.ToString%2A> `CStr` anahtar sözcüğünün kullandığından daha iyi <xref:System.Double> bir duyarlık belirleyebilmesi için yapının yöntemini kullanır. Varsayılan değer 15 haneye sahiptir, ancak "G17" biçimi bunu 17 basamağa genişletir.  
  
 Olduğundan `zeroPointTwo`,0,2için değeri,depolananbir0.20000000000000001değeriolansonsuzbiryinelenenikilikesirdir.`Double` 2,0 bu miktara göre bölmek, 0.19999999999999991 'nin geri kalanı ile 9.9999999999999995 verir.  
  
 İfadesinde `decimalRemainder`, değişmez değer türü karakteri `D` her iki işleneni olarak `Decimal`zorlar ve 0,2 kesin bir gösterimine sahiptir. Bu nedenle `Mod` , işleç beklenen 0,0 kalanı verir.  
  
 `decimalRemainder` Olarak`Decimal`bildirmek için yeterli olmadığına unutmayın. Ayrıca, `Decimal`değişmez değerleri için de zorlamanız gerekir ya da varsayılan olarak kullanır `Double` ve `decimalRemainder` aynı yanlış değeri ile aynı şekilde `doubleRemainder`alır.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boole türü, doğru şekilde sayısal türe dönüştürülmüyor  
 [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) değerleri sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır. Önceki sürümlerle uyumluluk için Visual Basic, `Boolean` ve sayısal türleri dönüştürmek için dönüştürme anahtar sözcükleri ( `CBool`[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md), `CInt`,, vb.) sağlar. Ancak, diğer diller bazen .NET Framework Yöntemler gibi bu dönüştürmeleri farklı şekilde gerçekleştirebilir.  
  
 `True` Ve`False`için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız gerekir. Mümkün olduğunda, `Boolean` değişkenlerin kullanımını tasarlandıkları mantıksal değerlerle kısıtlamalısınız. Değer karıştırmanız `Boolean` ve sayısal değerler gerekiyorsa, seçtiğiniz dönüştürme yöntemini anladığınızdan emin olun.  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic dönüştürme  
 Sayısal veri türlerini öğesine `CType` `CBool` `Boolean`dönüştürmek için veya dönüştürme anahtar sözcüklerini kullandığınızda 0 olur `False` ve diğer tüm değerler olur `True`. Dönüştürme `Boolean` anahtarsözcüklerinikullanarakdeğerleri`True` sayısal türlere dönüştürdüğünüzde 0 olurve-1olur.`False`  
  
### <a name="conversion-in-the-framework"></a>Çerçevede dönüştürme  
 Ad alanındaki <xref:System.Convert> `True` sınıfının <xref:System.Convert.ToInt32%2A> yöntemi + 1 ' <xref:System> e dönüştürülür.  
  
 Bir `Boolean` değeri sayısal veri türüne dönüştürmeniz gerekiyorsa kullandığınız dönüştürme yöntemiyle ilgili dikkatli olun.  
  
## <a name="character-literal-generates-compiler-error"></a>Karakter sabit değeri derleyici hatası oluşturuyor  
 Herhangi bir tür karakteri yokluğunda Visual Basic, değişmez değerler için varsayılan veri türlerini varsayar. Bir karakter sabiti için varsayılan tür, tırnak işaretleri (`" "`) — olur. `String`  
  
 Veri türü, [char veri türüne](../../../../visual-basic/language-reference/data-types/char-data-type.md)genişlemez. `String` Yani, bir `Char` değişkene bir sabit değer atamak istiyorsanız, bir daraltma dönüştürmesi yapmanız veya sabit değeri `Char` türe zorlamanız gerekir.  

|Bir değişkene veya sabitine atanacak bir Char sabit değeri oluşturmak için|
|---|  
|1.  Değişkeni veya sabiti olarak `Char`bildirin.<br />2.  Karakter değerini tırnak işaretleri (`" "`) içine alın.<br />3.  Değişmez değer türü karakteriyle `C` birlikte sağ çift tırnak işaretini takip edin. `Char` Tür denetimi anahtarı ([Option Strict deyimdir](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) ise `On`bu gereklidir ve herhangi bir durumda istenebilir.|  
  
 Aşağıdaki örnek, bir `Char` değişken için hem başarısız hem de başarılı bir sabit değer atamalarını gösterir.  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 Çalışma zamanında başarısız olabileceğinden daraltma dönüştürmeleri kullanılırken her zaman bir risk vardır. Örneğin, `String` değeri birden fazla karakter `String` içeriyorsa `Char` , öğesinden bir dönüştürme başarısız olabilir. Bu nedenle, `C` tür karakterini kullanmak daha iyi bir programdır.  
  
## <a name="string-conversion-fails-at-run-time"></a>Çalışma zamanında dize dönüştürme başarısız oluyor  
 [Dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) , çok az genişleyen dönüşümlere katılır. `String`widens yalnızca `Object`kendi kendine ve ' a ve `Char` `Char()` (bir `Char` dizi) öğesini olarak Genişlet `String`. Bunun nedeni `String` , değişkenlerin ve sabitlerin diğer veri türlerinin içeremeyeceği değerleri içerebildiği bir.  
  
 Tür denetleme anahtarı ([Option Strict deyimin](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `On`olduğunda, derleyici tüm örtük daraltma dönüştürmelerine izin vermez. Bu, ilgili `String`olanları içerir. Kodunuz `CStr` ve [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)gibi dönüştürme anahtar sözcüklerini kullanmaya devam edebilir, bu da dönüştürmeyi denemek için .NET Framework yönlendirir.  
  
> [!NOTE]
> Daraltma dönüştürme hatası, bir `For Each…Next` koleksiyondaki öğelerden döngü denetim değişkenine dönüşümler için bastırılır. Daha fazla bilgi ve örnek için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Daraltma dönüştürme koruması  
 Daraltma dönüştürmelerinden sakıncası çalışma zamanında başarısız olabilir. Örneğin, bir değişken " `String` true" veya "false" dışında bir şey içeriyorsa, öğesine `Boolean`dönüştürülemez. Noktalama karakterleri içeriyorsa, herhangi bir sayısal türe dönüştürme başarısız olur. Değişkeninizin `String` hedef türün kabul edebileceği değerleri tuttuğundan haberdar olmadığınız takdirde, dönüştürmeyi denememelisiniz.  
  
 ' Den `String` başka bir veri türüne dönüştürmeniz gerekiyorsa, en güvenli yordam TRY dönüştürme denemesi için [TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Bu, bir çalışma zamanı hatasıyla ilgilenmenizi sağlar.  
  
### <a name="character-arrays"></a>Karakter dizileri  
 Tek `Char` bir ve öğelerinden oluşan `Char` bir dizi her ikisi de `String`olarak. Ancak, `String` olarak `Char()`genişlemez. Bir `String` değeri `Char` diziye dönüştürmek için <xref:System.String.ToCharArray%2A> , <xref:System.String?displayProperty=nameWithType> sınıfının yöntemini kullanabilirsiniz.  
  
### <a name="meaningless-values"></a>Anlamlı değerler  
 Genel olarak, `String` değerler diğer veri türlerinde anlamlı değildir ve dönüştürme yüksek oranda yapay ve tehlikeli olur. Mümkün olduğunda, `String` değişkenlerin kullanımını tasarlandıkları karakter dizileri ile kısıtlamalısınız. Başka türlerdeki eşdeğer değerlere bağlı olmayan hiçbir kodu asla yazmamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

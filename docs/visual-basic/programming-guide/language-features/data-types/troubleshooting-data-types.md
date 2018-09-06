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
ms.openlocfilehash: 9bbc7f51de9899354184d051d8f1a584651dd030
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745495"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Veri Türleri Sorunlarını Giderme (Visual Basic)
Bu sayfada, iç veri türlerinde işlemler gerçekleştirdiğinizde oluşabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Kayan nokta ifadelerinin eşit olarak karşılaştırılır değil  
 Kayan nokta sayıları ile çalışırken ([tek veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md)), ikili kesir olarak depolandığını unutmayın. Bu kullanılamaz oldukları ikili kesir değil herhangi bir miktarın tam bir temsilini anlamına gelir (k formun / (2 ^ n) k ve n olduğu tamsayı). Yalnızca anların 0.2 (1/5 =) ve (3/10 =) 0.3 olabilirken, 0,5 (= 1/2) ve (= 5/16) 0.3125 kesin değerler tutulur.  
  
 Kayan nokta değerleri üzerinde çalışır, bu nedenle kesinlik eksikliği, size tam sonuçlar güvenemezsiniz. Özellikle, teorik olarak eşit olan iki değerleri biraz farklı temsilleri olabilir.  
  
| Kayan nokta miktarlar karşılaştırmak için | 
|---| 
|1.  Kendi fark mutlak değerini hesaplamak <xref:System.Math.Abs%2A> yöntemi <xref:System.Math> sınıfını <xref:System> ad alanı.<br />2.  Kendi fark büyük ise pratik amacıyla eşit olacak şekilde iki miktarları göz önünde bulundurun, kabul edilebilir en büyük fark, belirleyin.<br />3.  Kabul edilebilir farka fark mutlak değerini karşılaştırın.|  
  
 Aşağıdaki örnek, iki hatalı ve doğru karşılaştırma gösterir `Double` değerleri.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 Önceki örnekte <xref:System.Double.ToString%2A> yöntemi <xref:System.Double> daha iyi duyarlılık belirtmek için yapı `CStr` anahtar sözcüğünü kullanır. Varsayılan 15 basamak olsa da, isteğe bağlı olarak "G17" biçimi için 17 basamaklı genişletir.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod işleci, doğru sonuç döndürmez  
 Kayan nokta depolama kesinlik eksikliği nedeniyle [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md) en az bir işlenen kayan nokta olduğunda beklenmeyen bir sonuç döndürebilir.  
  
 [Ondalık veri türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) kayan Noktası temsili kullanmaz. İçinde filtresinin birçok sayı `Single` ve `Double` içinde tam olan `Decimal` (örneğin, 0.2 ve 0,3). Aritmetik olsa da, daha yavaş `Decimal` daha kayan nokta, bunu daha iyi duyarlılık elde etmek için performans düşüşü olabilir.  
  
|Kayan nokta miktarlar tamsayı kalanını bulmak için|  
|---|  
|1.  Değişkenleri olarak `Decimal`.<br />2.  Değişmez değer türü karakteri kullanmak `D` değişmez değerlerine zorlamak için `Decimal`, bunların değerleri için çok büyük olduğu durumlarda `Long` veri türü.|  
  
 Aşağıdaki örnek, kayan nokta işlenenler kesinlik eksikliği olası gösterir.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 Önceki örnekte <xref:System.Double.ToString%2A> yöntemi <xref:System.Double> daha iyi duyarlılık belirtmek için yapı `CStr` anahtar sözcüğünü kullanır. Varsayılan 15 basamak olsa da, isteğe bağlı olarak "G17" biçimi için 17 basamaklı genişletir.  
  
 Çünkü `zeroPointTwo` olduğu `Double`, 0.2 için değeri bir sonsuz yinelenen ikili 0.20000000000000001 depolanmış değerini içeren bir bölümüdür. Bu miktar 2.0 bölme 9.9999999999999995 0.19999999999999991 kalan ile verir.  
  
 İçin ifadede `decimalRemainder`, değişmez değer türü karakteri `D` iki işlenen de zorlar `Decimal`, ve 0.2 kesin bir gösterimi. Bu nedenle `Mod` işlecini 0,0 beklenen geri kalanı verir.  
  
 Bildirmek yeterli olmadığını göz önünde bulundurun `decimalRemainder` olarak `Decimal`. Değişmez değerler için derleyiciyi `Decimal`, veya kullandıkları `Double` varsayılan olarak ve `decimalRemainder` aynı yanlış değere alır `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boole türü sayısal tür için doğru bir şekilde dönüştürmez  
 [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) değerlerini, sayı olarak depolanmaz ve depolanan değerler sayıya eşdeğer olması amaçlanmamıştır. Önceki sürümleriyle uyumluluk için Visual Basic dönüşüm anahtar sözcükleri sağlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, vb.) arasında dönüştürmek için `Boolean` ve sayısal türler. Ancak, diğer diller bazen bu dönüştürmeleri gibi farklı şekilde gerçekleştirmek [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yöntemleri.  
  
 Hiçbir zaman eşdeğer sayısal değerler için dayanan kod yazmanız gerekir `True` ve `False`. Mümkün olduğunda, kullanımını sınırlamanız gerekir `Boolean` kendisi için tasarlanan mantıksal değerleri değişkenlere. Karışık gerekir, `Boolean` ve sayısal değerler, seçtiğiniz dönüştürme yöntemi anladığınızdan emin olun.  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic'te dönüştürme  
 Kullanırken `CType` veya `CBool` sayısal veri türlerine dönüştürmek için dönüşüm anahtar sözcükleri `Boolean`, 0 olur `False` ve diğer tüm değerler `True`. Dönüştürürken `Boolean` değerlerine dönüşüm anahtar sözcükleri kullanarak sayısal türler `False` 0 olur ve `True` -1 olur.  
  
### <a name="conversion-in-the-framework"></a>Framework'te dönüştürme  
 <xref:System.Convert.ToInt32%2A> Yöntemi <xref:System.Convert> sınıfını <xref:System> ad alanı dönüştürür `True` + 1 için.  
  
 Dönüştürmeniz gerekir, bir `Boolean` değer için bir sayısal veri türü, dikkatli olun hakkında hangi dönüştürme yöntemini kullanırsınız.  
  
## <a name="character-literal-generates-compiler-error"></a>Derleyici Hatası karakter değişmez değeri oluşturur  
 Herhangi bir tür karakter olmaması durumunda, Visual Basic veri türleri değişmez değerleri için varsayılan varsayar. Bir karakter sabiti için varsayılan türü — tırnak işaretleri arasına (`" "`) — olan `String`.  
  
 `String` Veri türü için genişletmek değil [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md). Bir sabit değerine atamak istiyorsanız buna bir `Char` değişken, bir daraltma dönüştürmesi yapmak veya değişmez değer zorla `Char` türü.  

|Bir karakter sabit değeri bir değişken veya sabit değer atamak için oluşturmak için|
|---|  
|1.  Değişken veya sabit olarak bildirin `Char`.<br />2.  Karakter değeri tırnak içine alın (`" "`).<br />3.  Değişmez değer türü karakteri ile kapanış çift tırnak işareti izleyin `C` değişmez değer zorlamak için `Char`. Bu tür denetimi anahtarı gereklidir ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On`, ve her durumda tercih edilir.|  
  
 Aşağıdaki örnek, bir sabit değer için hem başarısız hem başarılı atamalarını gösterir. bir `Char` değişkeni.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Var. olduğundan her zaman bir risk daraltma dönüştürmelerini kullanarak çalışma zamanında başarısız olabilir. Örneğin, bir dönüştürme `String` için `Char` başarısız olabilir `String` değer birden fazla karakter içeriyor. Bu nedenle, daha iyi kullanmak için programlama `C` karakter yazın.  
  
## <a name="string-conversion-fails-at-run-time"></a>Çalışma zamanı sırasında dize dönüştürme başarısız  
 [Dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) çok az sayıda dönüştürmelerine katılır. `String` yalnızca kendisine widens ve `Object`ve yalnızca `Char` ve `Char()` (bir `Char` array) için genişletmek `String`. Bunun nedeni, `String` değişkenleri ve sabitleri diğer veri türleri bulunamaz değerleri içerebilir.  
  
 Tür denetleme ne zaman geçiş ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On`, derleyicinin tüm örtük daraltma dönüştürmelerini izin vermiyor. Bu, ilgili olanlar içerir `String`. Kodunuzu dönüşüm anahtar sözcükleri gibi kullanmaya devam edebilirsiniz `CStr` ve [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md), hangi doğrudan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dönüştürme denemek için.  
  
> [!NOTE]
>  Öğeleri dönüştürmelerinde daraltmaya dönüştürme hatası gizlenen bir `For Each…Next` döngü denetim değişkeni koleksiyonu. Daha fazla bilgi ve örnekler için "Daraltma dönüştürmeleri" bölümüne bakın. [her biri için... Sonraki deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Daraltma dönüşümü koruma  
 Daraltma dönüştürmeleri dezavantajı, çalışma zamanında başarısız olabilir ' dir. Örneğin, bir `String` değişkenini içeren herhangi bir şey "True" veya "False olarak" da dönüştürülemez dışında `Boolean`. Noktalama işaretleri içeren herhangi bir sayısal tür dönüştürme başarısız olur. Bilmiyorsanız, `String` değişken her zaman bir hedef türü kabul edebilen değerleri tutar, bir dönüştürme çalışmamanız gerekir.  
  
 Dönüştürmeniz gerekir, `String` başka bir veri türü için en güvenli denenen bir dönüştürme kapsamak için oluşan bir yordamdır [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Bu, bir çalışma zamanı hatası ile uğraşmak sağlar.  
  
### <a name="character-arrays"></a>Karakter dizileri  
 Tek bir `Char` ve bir dizi `Char` hem genişletmek için öğeleri `String`. Ancak, `String` için genişletmek değil `Char()`. Dönüştürülecek bir `String` değerini bir `Char` kullanabileceğiniz dizi <xref:System.String.ToCharArray%2A> yöntemi <xref:System.String?displayProperty=nameWithType> sınıfı.  
  
### <a name="meaningless-values"></a>Anlamsız değerleri  
 Genel olarak, `String` değerlerini diğer veri türlerini anlamlı değildir ve dönüştürme, yüksek oranda yapay ve tehlikeli. Mümkün olduğunda, kullanımını sınırlamanız gerekir `String` kendisi için tasarlanan karakter dizileri değişkenleri. Hiçbir zaman diğer türleri eşdeğer değerlere dayanır kod yazmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)  
 [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

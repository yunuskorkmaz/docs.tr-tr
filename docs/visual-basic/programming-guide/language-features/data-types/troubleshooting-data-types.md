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
ms.openlocfilehash: c5ff9d097c0660956a9751a23511d8273766227c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-data-types-visual-basic"></a>Veri Türleri Sorunlarını Giderme (Visual Basic)
Bu sayfada, iç veri türleri üzerinde işlemler gerçekleştirdiğinizde oluşabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Kayan nokta ifadeleri eşit olarak karşılaştırmak değil  
 Kayan nokta sayıları ile çalışırken ([tek bir veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md)), ikili kesir olarak depolandığını unutmayın. Bu olamaz tuttukları ikili kesir değil miktar tam bir gösterimi anlamına gelir (k formunun / (2 ^ n) k ve n nerede tamsayılar). Yalnızca yaklaşık değerler 0.2 (1/5 =) ve (3/10 =) 0.3 olabilirken örneğin 0,5 (1/2 =) ve (= 5/16) 0.3125 kesin değerler tutulabilir.  
  
 Kayan nokta değerlerine çalışmayabilir, bu nedenle imprecision, tam sonuçlarına bağlı olamaz. Özellikle, teorik olarak eşit iki değer biraz farklı sunumu olabilir.  
  
| Kayan nokta sayıları karşılaştırmak için | 
|---| 
|1.  Kullanarak kendi fark mutlak değeri hesaplama <xref:System.Math.Abs%2A> yöntemi <xref:System.Math> sınıfını <xref:System> ad alanı.<br />2.  Kendi fark büyük ise pratik amaçlar için eşit olacak şekilde iki miktarları düşünebilirsiniz şekilde bir kabul edilebilir maksimum fark belirler.<br />3.  Mutlak değeri kabul edilebilir farktan farkının karşılaştırın.|  
  
 Aşağıdaki örnek, iki hatalı ve doğru karşılaştırma gösterir `Double` değerleri.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 Önceki örnekte kullanılmaktadır <xref:System.Double.ToString%2A> yöntemi <xref:System.Double> böylece daha iyi duyarlılık belirleyebilirsiniz yapısı `CStr` anahtar sözcüğü kullanır. Varsayılan, 15 basamağa olmakla birlikte isteğe bağlı olarak "G17" biçimi için 17 basamaklı genişletir.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod işleci doğru sonuç döndürmüyor  
 Kayan nokta depolama imprecision nedeniyle [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md) işlenen en az biri kayan nokta olduğunda beklenmeyen bir sonuç geri dönebilirsiniz.  
  
 [Ondalık veri türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) kayan Noktası temsili kullanmaz. İçinde filtresinin birçok numaraları `Single` ve `Double` tam olarak olan `Decimal` (örneğin 0.2 ve 0.3). Aritmetik rağmen yavaş `Decimal` daha kayan nokta, bu daha iyi duyarlık elde etmek için performans düşüşünü olabilir.  
  
|Kayan nokta sayıları tamsayı kalanını bulmak için|  
|---|  
|1.  Bildirme değişkenleri olarak `Decimal`.<br />2.  Değişmez değer türü karakteri kullanmak `D` değişmez değerleri için zorlamak için `Decimal`, bunların değerleri için çok büyük olduğu durumlarda `Long` veri türü.|  
  
 Aşağıdaki örnek, kayan nokta işlenenleri imprecision olası gösterir.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 Önceki örnekte kullanılmaktadır <xref:System.Double.ToString%2A> yöntemi <xref:System.Double> böylece daha iyi duyarlılık belirleyebilirsiniz yapısı `CStr` anahtar sözcüğü kullanır. Varsayılan, 15 basamağa olmakla birlikte isteğe bağlı olarak "G17" biçimi için 17 basamaklı genişletir.  
  
 Çünkü `zeroPointTwo` olan `Double`, değeri 0.2 için bir sonsuz yinelenen ikili 0.20000000000000001 saklı değerine sahip bölümüdür. Bu miktar 2.0 bölerek 0.19999999999999991 kalanı ile 9.9999999999999995 verir.  
  
 İçin ifadede `decimalRemainder`, değişmez değer türü karakteri `D` her iki işlenen zorlar `Decimal`, ve 0.2 kesin bir gösterimi. Bu nedenle `Mod` işleci 0,0 beklenen geri kalanı verir.  
  
 Bunu bildirmek yeterli değildir `decimalRemainder` olarak `Decimal`. Değişmez değerler için zorlaması gerekir `Decimal`, veya kullandıkları `Double` varsayılan ve `decimalRemainder` aynı yanlış değerine alır `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Boolean türü sayısal türe doğru şekilde dönüştürmez  
 [Boole veri türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) değerlerini, sayı olarak depolanmaz ve depolanan değerlerin sayıya eşit olması amaçlanmamıştır. Önceki sürümlerle uyumluluk için Visual Basic dönüşüm anahtar sözcükleri sağlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, vb.) arasında dönüştürme yapma `Boolean` ve sayısal türler. Bununla birlikte, diğer diller bazen dönüştürmeler gibi farklı şekilde gerçekleştirmeniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yöntemleri.  
  
 Hiçbir zaman eşdeğer sayısal değerler için güvenen kod yazmanız gerekir `True` ve `False`. Mümkün olduğunda, kullanımını kısıtlamalısınız `Boolean` , bunlar tasarlanan mantıksal değerleri değişkenleri. Karışık gerekir, `Boolean` ve sayısal değerleri, seçtiğiniz dönüştürme yöntemi anladığınızdan emin olun.  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic'te dönüştürme  
 Kullandığınızda `CType` veya `CBool` sayısal veri türlerine dönüştürmek için dönüşüm anahtar sözcükleri `Boolean`, 0 olur `False` ve diğer tüm değerler duruma `True`. Dönüştürürken `Boolean` dönüşüm anahtar sözcükleri kullanarak sayısal türler değerlere `False` 0 olur ve `True` -1 olur.  
  
### <a name="conversion-in-the-framework"></a>Framework'te dönüştürme  
 <xref:System.Convert.ToInt32%2A> Yöntemi <xref:System.Convert> sınıfını <xref:System> ad alanı dönüştürür `True` + 1 için.  
  
 Dönüştürürseniz gerekir, bir `Boolean` değer sayısal veri türü için dikkatli olun hakkında hangi dönüştürme yöntemini kullanın.  
  
## <a name="character-literal-generates-compiler-error"></a>Derleyici Hatası karakter sabit değeri oluşturur  
 Herhangi bir tür karakteri olmaması durumunda, Visual Basic veri türleri değişmez değerleri için varsayılan varsayar. Değişmez değer bir karakteri için varsayılan türü — tırnak işaretleri içine (`" "`) — olduğu `String`.  
  
 `String` Veri türü için genişletmek değil [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md). Bunun anlamı bir hazır değer atamak istiyorsanız bir `Char` değişken, daraltma dönüştürme yapmak veya sabit zorla `Char` türü.  

|Bir Char değişkeni ya da sabit değer atamak için değişmez değer oluşturmak için|
|---|  
|1.  Değişken ya da sabit değer olarak bildirmek `Char`.<br />2.  Karakter değeri tırnak işaretleri içine alın (`" "`).<br />3.  Değişmez değer türü karakteri ile kapanış çift tırnak işareti izleyin `C` literal zorlamak için `Char`. Bu tür denetlemesi geçiş yaparsanız gereklidir ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On`, ve her durumda tercih edilir.|  
  
 Aşağıdaki örnek, bir hazır değer başarılı ve başarısız atamalarını gösterir bir `Char` değişkeni.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Her zaman bir riski yoktur daraltma dönüşümleri kullanarak çünkü çalışma zamanında başarısız. Örneğin, bir dönüştürme `String` için `Char` başarısız `String` değeri birden fazla karakter içeriyor. Bu nedenle, daha iyi kullanmak için programlama `C` karakteri yazın.  
  
## <a name="string-conversion-fails-at-run-time"></a>Dize dönüştürme çalışma zamanında başarısız olur  
 [Dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) çok az genişletme Dönüşümlerde katılır. `String` yalnızca kendisine widens ve `Object`, yalnızca ve `Char` ve `Char()` (bir `Char` array) için genişletmek `String`. Bunun nedeni, `String` değişkenleri ve sabitleri diğer veri türleri bulunamaz değerler içerebilir.  
  
 Tür denetleme zaman geçiş ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On`, tüm örtük daraltma dönüşümleri derleyici izin vermez. Bu ilgili olanlar içerir `String`. Kodunuzu dönüşüm anahtar sözcükleri gibi kullanmaya devam edebilirsiniz `CStr` ve [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md), hangi doğrudan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dönüştürme çalışır.  
  
> [!NOTE]
>  Daraltma dönüştürme hatası öğelerde bulunan dönüştürmeleri için gizlenen bir `For Each…Next` for döngüsü denetim değişkeni koleksiyonu. Daha fazla bilgi ve örnekler için "Daraltma dönüşümleri" bölümüne bakın [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Dönüştürme koruma daraltma  
 Daraltma dönüşümleri dezavantajı, çalışma zamanında yük devredebildiğini ' dir. Örneğin, bir `String` değişken içeriyor, herhangi bir şey, "True" veya "False" onu dönüştürülemiyor dışında `Boolean`. Noktalama karakterleri içeriyorsa, herhangi bir sayısal tür dönüştürme başarısız olur. Bilmiyorsanız, `String` değişken her zaman hedef türünü kabul edebilir değerlerini tutan, dönüştürme denemelisiniz değil.  
  
 Dönüştürürseniz gerekir, `String` başka bir veri türüne güvenli denenen dönüştürmede kapsamak için yordamdır [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Bu, bir çalışma zamanı hatası ile ilgilenir sağlar.  
  
### <a name="character-arrays"></a>Karakter dizileri  
 Tek bir `Char` ve bir dizi `Char` her ikisi de genişletmek için öğeleri `String`. Ancak, `String` için genişletmek değil `Char()`. Dönüştürülecek bir `String` değeri bir `Char` kullanabileceğiniz diziye <xref:System.String.ToCharArray%2A> yöntemi <xref:System.String?displayProperty=nameWithType> sınıfı.  
  
### <a name="meaningless-values"></a>Anlamsız değerleri  
 Genel olarak, `String` değerlerini diğer veri türleri anlamlı değildir ve dönüştürme, yüksek oranda yapay ve tehlikeli. Mümkün olduğunda, kullanımını kısıtlamalısınız `String` , bunlar tasarlanan karakter dizileri değişkenleri. Hiçbir zaman diğer türleri eşdeğer değerleri dayanan kod yazmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

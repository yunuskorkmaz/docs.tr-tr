---
title: Sayısal Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 72cdca295e209935687f67ad290e816775d9fe13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393682"
---
# <a name="numeric-data-types-visual-basic"></a>Sayısal Veri Türleri (Visual Basic)
Visual Basic, çeşitli temsillerde sayıları işlemek için birkaç *sayısal veri türü* sağlar. *İntegral* türleri yalnızca tam sayıları temsil eder (pozitif, negatif ve sıfır) ve *İntegral olmayan* türler hem tamsayı hem de kesir parçaları olan sayıları temsil eder.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını gösteren bir tablo için bkz. [veri türleri](../../../language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Integral sayısal türleri  
 *Integral veri türleri* yalnızca kesirli parçalar olmadan sayıları temsil eden olanlardır.  
  
 *İşaretli* integral veri türleri, [SByte veri türü](../../../language-reference/data-types/sbyte-data-type.md) (8 bit), [kısa veri türü](../../../language-reference/data-types/short-data-type.md) (16 bit), [tamsayı veri türü](../../../language-reference/data-types/integer-data-type.md) (32-bit) ve [uzun veri türü](../../../language-reference/data-types/long-data-type.md) (64-bit). Bir değişken kesirli sayılar yerine her zaman tamsayılar depoluyorsa, bu türlerden biri olarak bildirin.  
  
 *İşaretsiz* Integral türleri [Byte veri türü](../../../language-reference/data-types/byte-data-type.md) (8 bit), [ushort Veri türü](../../../language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Veri türü](../../../language-reference/data-types/uinteger-data-type.md) (32-bit) ve [ulong veri türü](../../../language-reference/data-types/ulong-data-type.md) (64-bit). Bir değişken ikili veriler veya bilinmeyen doğa verileri içeriyorsa, bu türlerden biri olarak bildirin.  
  
### <a name="performance"></a>Performans  
 Aritmetik işlemler, diğer veri türleriyle daha hızlı bir şekilde integral türleridir. Visual Basic, ve türleri en hızlı bir şekilde bulunur `Integer` `UInteger` .  
  
### <a name="large-integers"></a>Büyük tamsayılar  
 Veri türünün tutabileceğinden daha büyük bir tamsayıyı tutmanız gerekiyorsa `Integer` , `Long` bunun yerine veri türünü kullanabilirsiniz. `Long`değişkenler-9223372036854775808 ila 9.223.372.036.854.775.807 arasında sayılar tutabilir. İle işlemler, `Long` ile biraz daha yavaştır `Integer` .  
  
 Daha büyük bir değere ihtiyacınız varsa, [ondalık veri türünü](../../../language-reference/data-types/decimal-data-type.md)de kullanabilirsiniz. `Decimal`Herhangi bir ondalık basamak kullanmıyorsanız, bir değişkende-79228162514264337593543950335 ile 79228162514264337593543950335 arasında sayılar tutabilirsiniz. Ancak, sayı içeren işlemler, `Decimal` diğer herhangi bir sayısal veri türüyle önemli ölçüde daha yavaştır.  
  
### <a name="small-integers"></a>Küçük tamsayılar  
 Veri türü için tam aralığa ihtiyacınız yoksa, `Integer` `Short` -32.768 ile 32.767 arasında tamsayılar içerebilen veri türünü kullanabilirsiniz. En küçük tamsayı aralığı için `SByte` veri türü-128 ile 127 arasında tamsayılar tutar. Küçük tamsayılar tutan çok sayıda değişkeniniz varsa, ortak dil çalışma zamanı bazen `Short` ve `SByte` değişkenlerinizi daha verimli bir şekilde saklayabilir ve bellek tüketimini kaydedebilir. Ancak, ve ile olan işlemler `Short` `SByte` ile biraz daha yavaştır `Integer` .  
  
### <a name="unsigned-integers"></a>İşaretsiz tamsayılar  
 Değişkeninizin negatif bir sayı tutması gerekmediğini biliyorsanız,, ve *imzasız türlerini*kullanabilirsiniz `Byte` `UShort` `UInteger` `ULong` . Bu veri türlerinin her biri, karşılık gelen imzalı türü ( `SByte` ,, `Short` `Integer` ve) kadar büyük pozitif bir tam sayı iki kez tutabilir `Long` . Performans açısından, her imzasız tür, kendisine karşılık gelen imzalı tür kadar etkilidir. Özellikle, `UInteger` `Integer` Tüm elemensel sayısal veri türlerinin en verimli şekilde ayırım ile paylaşır.  
  
## <a name="nonintegral-numeric-types"></a>İntegral olmayan sayısal türler  
 *Integral olmayan veri türleri* , hem tam sayı hem de kesirli parçalar içeren sayıları temsil eden olanlardır.  
  
 İntegral olmayan sayısal veri türleri şunlardır `Decimal` (128 bit sabit nokta), [tek veri türü](../../../language-reference/data-types/single-data-type.md) (32-bit kayan nokta) ve [Double veri türü](../../../language-reference/data-types/double-data-type.md) (64-bit kayan nokta). Bunlar tüm imzalı türlerdir. Bir değişken bir kesir içeriyorsa, bu türlerden biri olarak bildirin.  
  
 `Decimal`kayan nokta veri türü değil. `Decimal`sayıların bir ikili tamsayı değeri ve değerin hangi kısmının ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörü vardır.  
  
 `Decimal`Para değerleri için değişkenleri kullanabilirsiniz. Avantaj, değerlerin duyarlığından yararlanır. `Double`Veri türü daha hızlıdır ve daha az bellek gerektirir, ancak yuvarlama hatalarına tabidir. `Decimal`Veri türü, 28 ondalık basamağa kadar olan tüm doğruluğu korur.  
  
 Kayan nokta ( `Single` ve `Double` ) sayıları rakamlardan daha büyük aralıklar `Decimal` , ancak yuvarlama hatalarına tabi olabilir. Kayan nokta türleri daha az sayıda önemli basamağı destekler `Decimal` ancak daha fazla büyüklük değerlerini temsil edebilir.  
  
 Tamsayı olmayan sayı değerleri mmmEeee olarak ifade edilebilir, burada aaa, *Mantis* (önemli basamaklar) ve Eee ise *üs* (10 ' un bir kuvvetidir). İntegral olmayan türlerin en yüksek pozitif değerleri için 7.9228162514264337593543950335 E + 28, `Decimal` 3.4028235 e + 38 for `Single` , ve 1.79769313486231570 e + 308 için `Double` .  
  
### <a name="performance"></a>Performans  
 `Double`, geçerli platformlardaki işlemciler çift duyarlıklı kayan nokta işlemleri gerçekleştirtiğinden kesirli veri türlerinin en etkili olması. Ancak, ile işlemler, gibi `Double` integral türleriyle kadar hızlı değildir `Integer` .  
  
### <a name="small-magnitudes"></a>Küçük magnitudes  
 Olası en küçük boyuta (0 ' a yakın) sahip sayılar için, `Double` değişkenler negatif değerler için 4.94065645841246544 e-324 ve pozitif değerler için 4.94065645841246544 e-324 olan sayıları içerebilir.  
  
### <a name="small-fractional-numbers"></a>Küçük kesirli sayılar  
 Veri türü için tam aralığa ihtiyacınız yoksa, `Double` `Single` -3.4028235 e + 38 Ile 3.4028235 e + 38 arasında kayan noktalı sayılar tutan veri türünü kullanabilirsiniz. Değişkenler için en küçük magnitudes, `Single` negatif değerler için-1.401298 e-45 ve pozitif değerler için 1.401298 e-45 ' dir. Küçük kayan noktalı sayıları tutan çok sayıda değişkeniniz varsa, ortak dil çalışma zamanı bazen `Single` değişkenlerinizi daha verimli bir şekilde saklayabilir ve bellek tüketimini kaydedebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Karakter Veri Türleri](character-data-types.md)
- [Çeşitli Veri Türleri](miscellaneous-data-types.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)

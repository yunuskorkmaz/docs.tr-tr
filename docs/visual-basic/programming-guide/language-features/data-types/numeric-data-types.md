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
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346318"
---
# <a name="numeric-data-types-visual-basic"></a>Sayısal Veri Türleri (Visual Basic)
Visual Basic, çeşitli temsillerde sayıları işlemek için birkaç *sayısal veri türü* sağlar. *İntegral* türleri yalnızca tam sayıları temsil eder (pozitif, negatif ve sıfır) ve *İntegral olmayan* türler hem tamsayı hem de kesir parçaları olan sayıları temsil eder.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını gösteren bir tablo için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Integral sayısal türleri  
 *Integral veri türleri* yalnızca kesirli parçalar olmadan sayıları temsil eden olanlardır.  
  
 *İşaretli* integral veri türleri, [SByte veri türü](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bit), [kısa veri türü](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16 bit), [tamsayı veri türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit) ve [uzun veri türü](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit). Bir değişken kesirli sayılar yerine her zaman tamsayılar depoluyorsa, bu türlerden biri olarak bildirin.  
  
 *İşaretsiz* Integral türleri [Byte veri türü](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bit), [ushort Veri türü](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Veri türü](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit) ve [ulong veri türü](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit). Bir değişken ikili veriler veya bilinmeyen doğa verileri içeriyorsa, bu türlerden biri olarak bildirin.  
  
### <a name="performance"></a>Performans  
 Aritmetik işlemler, diğer veri türleriyle daha hızlı bir şekilde integral türleridir. Visual Basic `Integer` ve `UInteger` türleriyle en hızlı olurlar.  
  
### <a name="large-integers"></a>Büyük tamsayılar  
 `Integer` veri türünden tutabileceğinden büyük bir tamsayıyı tutmanız gerekiyorsa, bunun yerine `Long` veri türünü kullanabilirsiniz. `Long` değişkenler,-9223372036854775808 ile 9.223.372.036.854.775.807 arasında sayılar tutabilir. `Long` olan işlemler `Integer`biraz daha yavaştır.  
  
 Daha büyük bir değere ihtiyacınız varsa, [ondalık veri türünü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)de kullanabilirsiniz. Herhangi bir ondalık basamak kullanmıyorsanız, `Decimal` değişkende-79228162514264337593543950335 ile 79228162514264337593543950335 arasında sayılar tutabilirsiniz. Ancak, `Decimal` numaralarına sahip işlemler diğer herhangi bir sayısal veri türüyle önemli ölçüde daha yavaştır.  
  
### <a name="small-integers"></a>Küçük tamsayılar  
 `Integer` veri türünün tam aralığına ihtiyacınız yoksa,-32.768 ile 32.767 arasında tamsayılar içerebilen `Short` veri türünü kullanabilirsiniz. En küçük tamsayı aralığı için `SByte` veri türü-128 ile 127 arasında tamsayılar tutar. Küçük tamsayılar tutan çok sayıda değişkeniniz varsa, ortak dil çalışma zamanı bazen `Short` ve `SByte` değişkenlerini daha verimli bir şekilde saklayabilir ve bellek tüketimini kaydedebilir. Ancak, `Short` ve `SByte` işlemler `Integer`ile biraz daha yavaştır.  
  
### <a name="unsigned-integers"></a>İşaretsiz tamsayılar  
 Değişkeninizin negatif bir sayı tutması gerekmediğini biliyorsanız,`Byte`, `UShort`, `UInteger`ve `ULong`*işaretsiz türlerini* kullanabilirsiniz. Bu veri türlerinin her biri, karşılık gelen imzalı türü (`SByte`, `Short`, `Integer`ve `Long`) kadar büyük pozitif bir tamsayı tutabilir. Performans açısından, her imzasız tür, kendisine karşılık gelen imzalı tür kadar etkilidir. Özellikle, tüm temel sayısal veri türlerinin en verimli şekilde `UInteger` paylaşımlar `Integer`.  
  
## <a name="nonintegral-numeric-types"></a>İntegral olmayan sayısal türler  
 *Integral olmayan veri türleri* , hem tam sayı hem de kesirli parçalar içeren sayıları temsil eden olanlardır.  
  
 İntegral olmayan sayısal veri türleri `Decimal` (128 bit sabit nokta), [tek veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bit kayan nokta) ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit kayan nokta). Bunlar tüm imzalı türlerdir. Bir değişken bir kesir içeriyorsa, bu türlerden biri olarak bildirin.  
  
 `Decimal` kayan nokta veri türü değil. `Decimal` sayıların bir ikili tamsayı değeri ve değerin hangi kısmının ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörü vardır.  
  
 `Decimal` değişkenlerini, para değerleri için kullanabilirsiniz. Avantaj, değerlerin duyarlığından yararlanır. `Double` veri türü daha hızlıdır ve daha az bellek gerektirir, ancak yuvarlama hatalarına tabidir. `Decimal` veri türü, 28 ondalık basamağa kadar olan tüm doğruluğu korur.  
  
 Kayan nokta (`Single` ve `Double`) sayıları `Decimal` sayıdan daha büyük aralıklar vardır ancak yuvarlama hatalarına tabi olabilir. Kayan nokta türleri `Decimal` kıyasla daha az önemli basamağı destekler, ancak daha fazla büyüklük değerlerini temsil edebilir.  
  
 Tamsayı olmayan sayı değerleri mmmEeee olarak ifade edilebilir, burada aaa, *Mantis* (önemli basamaklar) ve Eee ise *üs* (10 ' un bir kuvvetidir). İntegral olmayan türlerin en yüksek pozitif değerleri, `Decimal`için 7.9228162514264337593543950335 E + 28, `Single`için 3.4028235 E + 38 ve `Double`için 1.79769313486231570 E + 308 ' dir.  
  
### <a name="performance"></a>Performans  
 `Double`, geçerli platformlardaki işlemciler çift duyarlıklı kayan nokta işlemleri gerçekleştirtiğinden, kesirli veri türlerinin en etkili olduğu. Ancak, `Double` olan işlemler, `Integer`gibi integral türleri kadar hızlı değildir.  
  
### <a name="small-magnitudes"></a>Küçük magnitudes  
 Olası en küçük boyuta (0 ' a yakın) sahip sayılar için `Double` değişkenler, sayıları negatif değerler için 4.94065645841246544 E-324 ve pozitif değerler için 4.94065645841246544 E-324 olarak tutabilir.  
  
### <a name="small-fractional-numbers"></a>Küçük kesirli sayılar  
 `Double` veri türü için tam aralığa ihtiyaç duymadıysanız,-3.4028235 E + 38 ile 3.4028235 E + 38 arasında kayan noktalı sayılar içerebilen `Single` veri türünü kullanabilirsiniz. `Single` değişkenleri için en küçük magnitudes, negatif değerler için-1.401298 E-45 ve pozitif değerler için 1.401298 E-45 ' dir. Küçük kayan noktalı sayıları tutan çok sayıda değişkeniniz varsa, ortak dil çalışma zamanı bazen `Single` değişkenlerinizi daha verimli bir şekilde saklayabilir ve bellek tüketimini kaydedebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Karakter Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Çeşitli Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)

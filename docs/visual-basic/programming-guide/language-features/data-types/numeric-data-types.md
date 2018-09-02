---
title: Sayısal Veri Türleri (Visual Basic)
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
ms.openlocfilehash: 6578a410e389a313b0bad70f043691240e288887
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391708"
---
# <a name="numeric-data-types-visual-basic"></a>Sayısal Veri Türleri (Visual Basic)
Visual Basic sağlayan birkaç *sayısal veri türleri* çeşitli gösterimlerini numaraları işlemek için. *İntegral* türleri yalnızca (pozitif, negatif ve sıfır) tamsayılar, temsil ve *nonintegral* türleri tamsayı ve kesirli bölümleri ile sayıları temsil eder.  
  
 Visual Basic veri türleri yan yana karşılaştırmasını gösteren bir tablo için bkz: [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Tamsayı sayısal türleri  
 *Tam sayı veri türleri* kesirli bölümleri olmadan yalnızca sayıları temsil eden olanlardır.  
  
 *İmzalı* tam sayı veri türleri [SByte veri türü](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bit) [kısa veri türü](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit) [tamsayı veri türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit) ve [ Long veri türü](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit). Kesirli sayılar yerine tamsayı her zaman bir değişken depoluyorsa, şu türlerden biri olarak bildirin.  
  
 *İşaretsiz* integral türleri [Byte veri türü](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bit) [UShort veri türü](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit) [Uınteger veri türü](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit) ve [ ULong veri türü](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit). Bir değişken ikili verileri veya bilinmeyen Doğa veri içeriyorsa, bu türlerden biri olarak bildirin.  
  
### <a name="performance"></a>Performans  
 Aritmetik işlemler, diğer veri türlerine sahip tam sayı türlerinden daha hızlıdır. İle hızlı oldukları `Integer` ve `UInteger` Visual Basic'te türler.  
  
### <a name="large-integers"></a>Büyük tamsayı  
 Daha büyük bir tamsayı tutmak gerekirse `Integer` veri türü tutabilir, kullanabileceğiniz `Long` veri türü yerine. `Long` değişkenleri-9,223,372,036,854,775,808 9.223.372.036.854.775.807 ile sayılar içerebilir. İşlemleriyle `Long` biraz daha yavaş çalışır ile `Integer`.  
  
 Daha da büyük değerler gerekiyorsa, kullanabileceğiniz [ondalık veri türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). İçinde 79,228,162,514,264,337,593,543,950,335 aracılığıyla-79,228,162,514,264,337,593,543,950,335 gelen sayıları tutabilir bir `Decimal` herhangi bir ondalık basamak kullanmazsanız değişkeni. Ancak, işlemleriyle `Decimal` sayılardır herhangi bir sayısal veri türü ile oldukça yavaştır.  
  
### <a name="small-integers"></a>Küçük tamsayı  
 Tam aralığının gerekmiyorsa `Integer` kullanabileceğiniz veri türü `Short` -32.768 32.767 aracılığıyla tam tutabilen veri türü. En küçük tamsayı aralığı için `SByte` -128 ile 127'den tamsayı veri türü tutar. Ortak dil çalışma zamanı değişkenlerinin küçük tamsayının tutulması çok büyük bir sayı varsa, bazen depolayabilir, `Short` ve `SByte` değişkenleri daha verimli bir şekilde ve bellek tüketimi kaydedin. Ancak, işlemleriyle `Short` ve `SByte` biraz daha yavaş çalışır ile `Integer`.  
  
### <a name="unsigned-integers"></a>İşaretsiz tamsayı  
 Biliyorsanız, negatif bir sayı tutmak, değişkeni hiçbir zaman işlemesi gerekmez, kullanabileceğiniz *imzasız türler*`Byte`, `UShort`, `UInteger`, ve `ULong`. Bu veri türlerinin her biri bir pozitif tamsayı iki kez büyük, karşılık gelen türü işaretli olarak tutabilir (`SByte`, `Short`, `Integer`, ve `Long`). Performans açısından her bir işaretsiz türe karşılık gelen imzalı türü olarak tam olarak etkilidir. Özellikle, `UInteger` paylaşır `Integer` tüm basit sayısal veri türleri en verimli olmanın farkı.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral sayısal türler  
 *Nonintegral veri türleri* hem tamsayı hem de kesirli bölümleri sayıları temsil eden olanlardır.  
  
 Nonintegral sayısal veri türleri `Decimal` (128-bit sabit nokta), [tek veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32 bit kayan nokta), ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit kayan nokta). Bunların tümü imzalı türleridir. Bir değişken bir kesir içeriyorsa bu türlerinden biri olarak bildirin.  
  
 `Decimal` bir kayan nokta veri türü değil. `Decimal` ikili bir tamsayı ve ondalık kesir değeri hangi kısmı olduğunu belirten bir tamsayı Ölçeklendirme çarpanı numarasına sahip.  
  
 Kullanabileceğiniz `Decimal` para değerleri değişkenleri. Duyarlılık değerlerinin avantajlarındandır. `Double` Veri türü daha hızlı ve daha az bellek gerektirir, ancak yuvarlama hataları tabi olduğu. `Decimal` Veri türünü tam doğruluk ondalık basamak 28 korur.  
  
 Kayan nokta (`Single` ve `Double`) daha büyük aralıklar sağlayamayacaksınız `Decimal` numaraları ancak yuvarlama hataları tabi olabilir. Kayan nokta türlerini destekleyen değerinden daha az önemli basamak `Decimal` ancak büyük büyüklük değerini temsil edebilir.  
  
 Nonintegral sayı değerleri ifade edilemez mmmEeee içinde AAA olan *Mantis* (önemli basamak) ve eee *üs* (10 'un bir kuvveti). En yüksek pozitif nonintegral türlerinin 7.9228162514264337593543950335E + 28 için değerler `Decimal`, 3.4028235E + 38 `Single`ve 1.79769313486231570E + 308 `Double`.  
  
### <a name="performance"></a>Performans  
 `Double` geçerli platformda işlemci çift duyarlıklı kayan nokta işlemleri kesirli veri türleri en verimli olmasıdır. Ancak, işlemleriyle `Double` gibi tam sayı türleri gibi ile kısa sürede olmayan `Integer`.  
  
### <a name="small-magnitudes"></a>Küçük Massively  
 En küçük olası Büyüklük (yakın), 0 ile sayılar için `Double` değişkenleri tutabilir sayı kadar - 4.94065645841246544E küçük-324 negatif değerler ve 4.94065645841246544E-324 pozitif değerler için.  
  
### <a name="small-fractional-numbers"></a>Küçük kesirli sayılar  
 Tam aralığının gerekmiyorsa `Double` kullanabileceğiniz veri türü `Single` from - 3.4028235E + 38 3.4028235E + 38 aracılığıyla kayan nokta sayıları tutabilir veri türü. İçin en küçük massively `Single` değişkenleri şunlardır:-1.401298E-negatif değerler ve 1.401298E 45-45 pozitif değerler için. Çok sayıda küçük bir kayan noktalı sayıların tutan değişken varsa, ortak dil çalışma zamanı bazen depolayabilir, `Single` değişkenleri daha verimli bir şekilde ve bellek tüketimi kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Karakter Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Çeşitli Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)

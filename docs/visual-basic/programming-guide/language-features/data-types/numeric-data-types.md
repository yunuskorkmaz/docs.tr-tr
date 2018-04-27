---
title: Sayısal Veri Türleri (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5e7a5340f9b0d103acc14350f30f17d8d709de3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="numeric-data-types-visual-basic"></a>Sayısal Veri Türleri (Visual Basic)
Visual Basic sağlayan birkaç *sayısal veri türleri* çeşitli sunularını numaraları işlemek için. *Tam sayı* türleri yalnızca tam (pozitif, negatif ve sıfır) sayılar, temsil eder ve *nonintegral* türleri tamsayı ve kesirli bölümleri ile numaralarını temsil eder.  
  
 Visual Basic veri türleri yan yana karşılaştırmasını gösteren bir tablo için bkz: [veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="integral-numeric-types"></a>Tam Sayı sayısal türler  
 *Tam sayı veri türleri* kesirli bölümleri olmadan yalnızca sayılar temsil eden olanlardır.  
  
 *İmzalı* tam sayı veri türleri [SByte veri türü](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bit) [kısa veri türü](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit) [tamsayı veri türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit) ve [ Long veri türü](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bit). Kesirli sayılar yerine tamsayılar her zaman bir değişken depoluyorsa, şu türlerden birine olarak bildirin.  
  
 *İmzasız* tam sayı türleri [Byte veri türü](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bit) [UShort veri türü](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit) [Uınteger veri türü](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit) ve [ ULong veri türü](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bit). Bir değişken ikili veri veya bilinmeyen yapısı veri içeriyorsa, şu türlerden birine olarak bildirin.  
  
### <a name="performance"></a>Performans  
 Aritmetik işlemler, diğer veri türlerine sahip tam sayı türlerinden daha hızlıdır. İle hızlı `Integer` ve `UInteger` Visual Basic'te türler.  
  
### <a name="large-integers"></a>Büyük tamsayı  
 Daha büyük bir tamsayı tutmak gerekiyorsa `Integer` veri türü tutun, kullanabileceğiniz `Long` veri türü yerine. `Long` değişkenleri 9,223,372,036,854,775,807 aracılığıyla-9,223,372,036,854,775,808 sayılar içerebilir. İşlemlerle `Long` biraz daha yavaş çalışır ile `Integer`.  
  
 Daha da büyük değerler gerekiyorsa, kullanabileceğiniz [ondalık veri türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). İçinde 79,228,162,514,264,337,593,543,950,335 aracılığıyla-79,228,162,514,264,337,593,543,950,335 numaraları tutabilir bir `Decimal` ondalık basamak kullanmıyorsanız değişkeni. Ancak, işlemleriyle `Decimal` numaralarıdır diğer sayısal veri türüne sahip önemli ölçüde daha yavaş çalışır.  
  
### <a name="small-integers"></a>Küçük tamsayı  
 Tam aralığını gerekmiyorsa `Integer` veri türünü kullanabilir `Short` 32.767 aracılığıyla 32,768 tamsayılar tutabilen veri türü. En küçük tamsayı aralığı için `SByte` veri türü tamsayı 127 aracılığıyla -128'den tutar. Bir çok sayıda küçük tamsayı tutun değişkenleri varsa, ortak dil çalışma zamanı bazen depolayabilir, `Short` ve `SByte` değişkenleri daha verimli bir şekilde ve bellek tüketimi kaydedin. Ancak, işlemleriyle `Short` ve `SByte` biraz daha yavaş çalışır ile `Integer`.  
  
### <a name="unsigned-integers"></a>İmzasız tamsayılar  
 Biliyorsanız, değişken negatif bir sayı tutmak hiçbir zaman gerekiyor, kullanabileceğiniz *imzasız türleri*`Byte`, `UShort`, `UInteger`, ve `ULong`. Bu veri türleri pozitif bir tamsayı iki kez büyük türü, karşılık gelen imzalanmış olarak içerebilir (`SByte`, `Short`, `Integer`, ve `Long`). Performans açısından her imzasız tam karşılık gelen imzalı türü olarak verimli türüdür. Özellikle, `UInteger` ile paylaşır `Integer` tüm başlangıç sayısal veri türleri en etkili olma bir ayrımdır.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral sayısal türler  
 *Nonintegral veri türleri* tamsayı ve kesirli bölümleri numaralarıyla temsil eden olanlardır.  
  
 Nonintegral sayısal veri türleri: `Decimal` (128-bit sabit noktası), [tek bir veri türü](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32 bit kayan nokta), ve [Double veri türü](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit kayan nokta). Bunların tümü imzalı türleridir. Bir değişken kesir içeriyorsa, şu türlerden birine olarak bildirin.  
  
 `Decimal` kayan nokta veri türü değil. `Decimal` sayı ikili bir tamsayı ve hangi değer bir ondalık kesir bölümüdür belirten bir tamsayı ölçekleme faktörü vardır.  
  
 Kullanabileceğiniz `Decimal` para değerleri için değişkenleri. Avantajı değerlerinin duyarlık olmasıdır. `Double` Veri türü daha hızlıdır ve daha az bellek gerektirir, ancak hataları yuvarlama tabidir. `Decimal` Veri türü 28 ondalık tam tutarlılık korur.  
  
 Kayan nokta (`Single` ve `Double`) numarasına sahip daha büyük aralıkları `Decimal` sayılar ancak hatalar yuvarlama tabi olabilir. Kayan nokta türleri desteği daha az önemli basamak `Decimal` ancak büyük büyüklük değerlerini temsil edebilir.  
  
 Nonintegral sayı değerleri ifade edilir mmmEeee içinde AAA olan *Mantis* (önemli basamak) ve eee *üs* (10 güç). En yüksek pozitif nonintegral türleri 7.9228162514264337593543950335E + 28 için değerleri `Decimal`, 3.4028235E + 38 `Single`ve 1.79769313486231570E + 308 `Double`.  
  
### <a name="performance"></a>Performans  
 `Double` Geçerli platformlarda işlemci çift duyarlıklı kayan nokta işlemleri nedeniyle kesirli veri türleri en etkili yoldur. Ancak, işlemleriyle `Double` gibi tam sayı türleri gibi ile kadar hızlı değildir `Integer`.  
  
### <a name="small-magnitudes"></a>Küçük Magnitudes  
 Sayılar (0 olarak en yakın), en küçük olası Büyüklük ile `Double` değişkenleri tutun numaraları olabildiğince küçük - 4.94065645841246544E-negatif değerler ve 4.94065645841246544E 324-324 pozitif değerler için.  
  
### <a name="small-fractional-numbers"></a>Küçük kesirli sayılar  
 Tam aralığını gerekmiyorsa `Double` veri türünü kullanabilir `Single` from - 3.4028235E + 38 3.4028235E + 38 aracılığıyla kayan nokta sayıları tutabilen veri türü. İçin en küçük magnitudes `Single` değişkenleri şunlardır:-1.401298E-45 negatif değerler ve 1.401298E-45 pozitif değerler için. Kayan nokta sayıları küçük tutun değişkenleri çok fazla sayıda varsa, ortak dil çalışma zamanı bazen depolayabilir, `Single` değişkenleri daha verimli bir şekilde ve bellek tüketimi kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Karakter Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Çeşitli Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)

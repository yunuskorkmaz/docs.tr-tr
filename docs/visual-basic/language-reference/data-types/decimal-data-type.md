---
title: Onluk Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243329"
---
# <a name="decimal-data-type-visual-basic"></a>Onluk Veri Türü (Visual Basic)

10 değişken gücüyle ölçeklenmiş 96 bit (12 bayt) tamsayı numaralarını temsil eden imzalı 128 bit (16 bayt) değerleri tutar. Ölçekleme faktörü ondalık noktanın sağındaki basamak sayısını belirtir; 0 ile 28 arasında değişir. 0 ölçeği (ondalık basamak yok) ile, mümkün olan en büyük değer +/-79.228.162.514.264.337.593.543.950.335 (+/-7228162514264337593544395035E+28' dir. 28 ondalık basamakile en büyük değer +/-7228162514264337593543950335 ve en küçük sıfır olmayan değer +/-0.0000000000000000000000000000000000000000000000 (+/-1E-28).

## <a name="remarks"></a>Açıklamalar

Veri `Decimal` türü, bir sayı için en çok önemli basamak sayısını sağlar. 29'a kadar önemli basamağı destekler ve 7,9228 x 10^28'i aşan değerleri temsil edebilir. Özellikle çok sayıda basamak gerektiren ancak yuvarlama hatalarını tolere edemeyen finansal hesaplamalar için uygundur.

Varsayılan değeri `Decimal` 0'dır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Hassas.** `Decimal`kayan nokta veri türü değildir. Yapı, `Decimal` bir işaret biti ve değerin hangi bölümünün ondalık kesir olduğunu belirten bir tamsayı ölçeklendirme faktörüyle birlikte ikili bir tamsayı değeri tutar. Bu nedenle, `Decimal` sayılar kayan nokta türlerine göre bellekte`Single` `Double`daha kesin bir gösterime sahiptir ( ve).

- **Performans.** Veri `Decimal` türü tüm sayısal türlerin en yavaşıdır. Bir veri türünü seçmeden önce performansın performansını tartmalısınız.

- **Genişletme.** Veri `Decimal` türü `Single` genişletir `Double`veya . Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> `Decimal` hatayla karşılaşmadan bu türlerden herhangi birini dönüştürebileceğiniz anlamına gelir.

- **Sıfırları Takip Ediyor.** Visual Basic, sondaki sıfırları `Decimal` gerçek bir şekilde depolamaz. Ancak, `Decimal` bir değişken hesaplamalı olarak edinilen sondaki sıfırları korur. Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  Önceki `MsgBox` örnekte çıktı aşağıdaki gibidir:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Karakterleri yazın.** Gerçek tür karakterini `D` bir edebi karaktere ekler, `Decimal` onu veri türüne zorlar. Tanımlayıcı türü karakterini `@` herhangi bir tanımlayıcıya `Decimal`ekolarak .

- **Çerçeve Türü.** .NET Framework'de karşılık gelen <xref:System.Decimal?displayProperty=nameWithType> tür yapıdır.

## <a name="range"></a>Aralık

 Bir `Decimal` değişkene veya `D` sabite büyük bir değer atamak için tür karakterini kullanmanız gerekebilir. Derleyici, aşağıdaki örnekte görüldüğü gibi, `Long` edebi türü bir karakter aşağıdaki gibi, bir edebi karakter aşağıdaki gibi aşağıdaki gibi değilse, bir literal olarak yorumluyor olmasıdır.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

Buna atanan `bigDec1` değer `Long`için aralık içinde düştüğünden, taşma oluşturmaz. Değer `Long` `Decimal` değişkene atanabilir.

Ona atanan `bigDec2` değer `Long`için çok büyük olduğundan, bir taşma hatası oluşturur. Sayısal edebi ilk olarak `Long`yorumlanamayacağıiçin, `Decimal` değişkene atanamaz.

Çünkü, `bigDec3`edebi türde `D` karakter derleyiciyi literal'ı bir ' `Decimal` yerine "" `Long`olarak yorumlamaya zorlayarak sorunu çözer.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

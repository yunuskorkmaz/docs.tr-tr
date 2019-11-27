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
ms.openlocfilehash: 6d62bcc1d043b45c0fc30154d9dc633b998f97b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344039"
---
# <a name="decimal-data-type-visual-basic"></a>Onluk Veri Türü (Visual Basic)

, 10 ' un bir değişken gücüne göre ölçeklendirilmiş 96 bit (12 baytlık) tamsayı sayılarını temsil eden imzalı 128 bitlik (16 baytlık) değerleri barındırır. Ölçeklendirme faktörü, ondalık noktanın sağ tarafındaki basamak sayısını belirtir; 0 ile 28 arasında değişir. 0 ölçeğinde (ondalık basamak yok), olası en büyük değer +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28) olur. 28 ondalık basamakla, en büyük değer +/-7.9228162514264337593543950335 ve sıfır olmayan en küçük değer +/-0,0000000000000000000000000001 (+/-1E-28) olur.

## <a name="remarks"></a>Açıklamalar

`Decimal` veri türü, bir sayı için en çok önemli basamak sayısını sağlar. 29 ' dan fazla önemli basamağı destekler ve 7,9228 x 10 ^ 28 değerinden fazla değeri temsil edebilir. Çok sayıda basamak gerektiren, ancak yuvarlama hatalarını kabul edemeyecek finansal gibi hesaplamalar için özellikle uygundur.

`Decimal` varsayılan değeri 0 ' dır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Duyarlılık.** `Decimal` kayan nokta veri türü değil. `Decimal` yapısı bir ikili tamsayı değerini, bir işaret biti ve değerin hangi kısmının ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörüyle birlikte tutar. Bu nedenle, `Decimal` sayıların bellekte kayan nokta türlerinden (`Single` ve `Double`) daha kesin bir temsili vardır.

- **Mının.** `Decimal` veri türü, tüm sayısal türlerin en yavaş türüdür. Veri türü seçmeden önce, performans için duyarlık önem derecesine sahip olmanız gerekir.

- **Kan.** `Decimal` veri türü `Single` veya `Double`için widens. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Decimal` bu türlerden birine dönüştürebileceğiniz anlamına gelir.

- **Sondaki sıfırlar.** Visual Basic sondaki sıfırları bir `Decimal` değişmez değerinde depolamaz. Ancak, `Decimal` bir değişken sondaki tüm sıfırları elde edilen hesaplama sırasında korur. Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  Önceki örnekteki `MsgBox` çıkışı aşağıdaki gibidir:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Tür karakterleri.** Değişmez değer türü karakter `D` bir sabit değere eklenmesi, `Decimal` veri türüne zorlar. Tanımlayıcı türü karakter `@` herhangi bir tanımlayıcıya eklemek bunu `Decimal`zorlar.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Decimal?displayProperty=nameWithType> yapısıdır.

## <a name="range"></a>Aralık

 Bir `Decimal` değişkenine veya sabitine büyük bir değer atamak için `D` türü karakterini kullanmanız gerekebilir. Bu gereksinim, derleyicinin değişmez değer türü karakteri, aşağıdaki örnekte gösterildiği gibi değişmez değer bir karakter ile aynı olmadığı sürece `Long` olarak bir sabit değeri yorumlaması.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

`bigDec1` için bildirim bir taşma oluşturmaz çünkü kendisine atanan değer `Long`aralığı içinde yer almamıştı. `Long` değeri `Decimal` değişkenine atanabilir.

`bigDec2` için bildirim, kendisine atanan değer `Long`için çok büyük olduğundan bir taşma hatası oluşturuyor. Sayısal sabit değer ilk olarak bir `Long`olarak yorumlanamadığı için, `Decimal` değişkenine atanamaz.

`bigDec3`için, değişmez değer türü karakter `D` derleyicinin değeri `Long`yerine bir `Decimal` olarak yorumlamasını zorlayarak sorunu çözer.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

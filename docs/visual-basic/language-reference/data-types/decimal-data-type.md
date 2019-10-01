---
title: Onluk Veri Türü (Visual Basic)
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
ms.openlocfilehash: 892824b61cfb6a0172361d220c638cab0a78565d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700872"
---
# <a name="decimal-data-type-visual-basic"></a>Onluk Veri Türü (Visual Basic)

, 10 ' un bir değişken gücüne göre ölçeklendirilmiş 96 bit (12 baytlık) tamsayı sayılarını temsil eden imzalı 128 bitlik (16 baytlık) değerleri barındırır. Ölçeklendirme faktörü, ondalık noktanın sağ tarafındaki basamak sayısını belirtir; 0 ile 28 arasında değişir. 0 ölçeğinde (ondalık basamak yok), olası en büyük değer +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28) olur. 28 ondalık basamakla, en büyük değer +/-7.9228162514264337593543950335 ve sıfır olmayan en küçük değer +/-0,0000000000000000000000000001 (+/-1E-28) olur.

## <a name="remarks"></a>Açıklamalar

@No__t-0 veri türü, bir sayı için en çok önemli basamak sayısını sağlar. 29 ' dan fazla önemli basamağı destekler ve 7,9228 x 10 ^ 28 değerinden fazla değeri temsil edebilir. Çok sayıda basamak gerektiren, ancak yuvarlama hatalarını kabul edemeyecek finansal gibi hesaplamalar için özellikle uygundur.

@No__t-0 ' ın varsayılan değeri 0 ' dır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Duyarlılık.** `Decimal` bir kayan nokta veri türü değil. @No__t-0 yapısı bir ikili tamsayı değerini, bir işaret biti ve değerin hangi bölümünün ondalık kesir olduğunu belirten bir tamsayı ölçekleme faktörüyle birlikte tutar. Bu nedenle, `Decimal` sayıları bellek içinde kayan nokta türlerinden daha kesin bir gösterimine sahiptir (`Single` ve `Double`).

- **Mının.** @No__t-0 veri türü, tüm sayısal türlerin en yavaş türüdür. Veri türü seçmeden önce, performans için duyarlık önem derecesine sahip olmanız gerekir.

- **Kan.** @No__t-0 veri türü `Single` veya `Double` ' widens. Bu, <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan `Decimal` ' y i bu türlerden birine dönüştürebileceğiniz anlamına gelir.

- **Sondaki sıfırlar.** Visual Basic sondaki sıfırları bir `Decimal` değişmez değerinde depolamaz. Ancak, `Decimal` değişkeni sondaki tüm sıfırları elde edilen hesaplama sırasında korur. Aşağıdaki örnek bunu göstermektedir.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  Yukarıdaki örnekte `MsgBox` çıkışı aşağıdaki gibidir:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Tür karakterleri.** Değişmez değer türü karakterini bir hazır @no__t eklemek, `Decimal` veri türüne zorlar. Tanımlayıcı türü karakterini herhangi bir tanımlayıcıya eklemek @no__t `Decimal` ' e zorlar.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Decimal?displayProperty=nameWithType> yapısıdır.

## <a name="range"></a>Aralık
 Bir `Decimal` değişkenine veya sabitine büyük bir değer atamak için `D` tür karakterini kullanmanız gerekebilir. Bu gereksinim, bir sabit değer türü karakteri değişmez değer olarak, aşağıdaki örnekte gösterildiği gibi, bir sabit değerin `Long` olarak yorumlaması derleyicisidir.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

@No__t-0 ' a yönelik bildirim bir taşma oluşturmaz çünkü kendisine atanan değer `Long` aralığı içinde. @No__t-0 değeri `Decimal` değişkenine atanabilir.

@No__t-0 ' a yönelik bildirim, kendisine atanan değer `Long` için çok büyük olduğundan bir taşma hatası oluşturuyor. Sayısal sabit değer öncelikle `Long` olarak yorumlanamadığından, `Decimal` değişkenine atanamaz.

@No__t-0 için, değişmez değer türü karakteri `D`, derleyicinin sabit değeri `Long` yerine `Decimal` olarak yorumlamasını zorlayarak sorunu çözer.

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

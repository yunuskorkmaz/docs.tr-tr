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
ms.openlocfilehash: ffc1cd141ba624d2ce26e4b1c070431ff0ddd6fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390905"
---
# <a name="decimal-data-type-visual-basic"></a>Onluk Veri Türü (Visual Basic)
Ayrı tutma 128-bit (16 baytlık) değerler tarafından 10 değişken güç ölçeği 96 bit (12-bayt) tamsayıları temsil eden imzalı. Ölçeklendirme çarpanı ondalık noktasının sağındaki basamak sayısını belirtir; 0 ile 28 arasında çeşitlilik gösterir. İle bir ölçek 0 (ondalık basamak) 79,228,162,514,264,337,593,543,950,335 +/-olası en büyük değer olan (7 +/-.9228162514264337593543950335E + 28). 28 ondalık basamakları olan en büyük değeri 7.9228162514264337593543950335 +/-, ise sıfır olmayan en küçük değeri +/-0.0000000000000000000000000001 (+/-1E-28).  
  
## <a name="remarks"></a>Açıklamalar  
 `Decimal` Veri türü, bir sayı için en fazla belirtici basamak sayısını sağlar. 29 önemli basamak destekler ve 7.9228 x 10 aşan değerleri temsil edebilen ^ 28. Gibi özellikle hesaplamalar için uygun Finans, çok sayıda basamak gerektirir ancak yuvarlama hataları tolere olamaz.  
  
 Varsayılan değer olan `Decimal` 0'dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Duyarlık.** `Decimal` bir kayan nokta veri türü değil. `Decimal` Yapısı tutan bir imza biti ve Ölçeklendirme çarpanı ondalık kesir değeri hangi kısmı olduğunu belirten bir tamsayı ile birlikte bir ikili tamsayı değeri. Bu nedenle, `Decimal` numarasına sahip daha kesin bir gösterimi kayan nokta türleri daha bellekte (`Single` ve `Double`).  
  
-   **Performans.** `Decimal` Veri türü, tüm sayısal türlerin en yavaş. Bir veri türü seçmeden önce performans karşı duyarlılığı önemini tartmanız gerekir.  
  
-   **Genişletme.** `Decimal` Widens veri türü için `Single` veya `Double`. Yani dönüştürebilirsiniz `Decimal` karşılaşmadan bu türlerden birine bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Sondaki sıfırlar.** Visual Basic sıfırları depolamaz bir `Decimal` değişmez. Ancak, bir `Decimal` değişkeni hesaplama açısından alınan sonundaki sıfırları korur. Aşağıdaki örnek bunu göstermektedir.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     Çıkışı `MsgBox` önceki örnekte aşağıdaki gibidir:  
  
     D1 2.375, d2 = 1.625, d3 = 4.000, d4 = 4 =  
  
-   **Tür karakterleri.** Değişmez değer türü karakterinin `D` sabit değerine zorlar `Decimal` veri türü. Tanımlayıcı türü karakteri ekleme `@` herhangi bir tanımlayıcı zorlar `Decimal`.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Decimal?displayProperty=nameWithType> yapısı.  
  
## <a name="range"></a>Aralık  
 Kullanmanız gerekebilir `D` türü için büyük bir değer atamak için karakteri bir `Decimal` değişken veya sabit. Bu gereksinim olduğundan derleyici değişmez değer olarak yorumlar `Long` sürece bir değişmez değer türü karakteri aşağıdaki örnekte gösterildiği gibi değişmez değer izler.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 Bildirimi `bigDec1` kendisine atanmış değer aralığında kaldığından taşma üretemez `Long`. `Long` Değer atanabilen `Decimal` değişkeni.  
  
 Bildirimi `bigDec2` kendisine atanmış değer için çok büyük olduğundan overflow hata üretir `Long`. Sayısal sabit değer ilk olarak yorumlanamıyor çünkü bir `Long`, için atanamaz `Decimal` değişkeni.  
  
 İçin `bigDec3`, değişmez değer türü karakteri `D` değişmez değer olarak yorumlamak üzere zorlayarak sorunu çözer bir `Decimal` yerine olarak bir `Long`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

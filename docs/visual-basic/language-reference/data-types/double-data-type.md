---
title: Double Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: c2d3d7d360ccb240bafbe0e19e9f396adfba7f7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590270"
---
# <a name="double-data-type-visual-basic"></a>Double Veri Türü (Visual Basic)
Ayrı tutma imzalı değerinden - 1.79769313486231570E + 308 ile - değişen IEEE 64-bit (8-bayt) çift duyarlıklı kayan nokta sayıları 4.94065645841246544E-324 negatif değerler ve 4.94065645841246544E-324 1.79769313486231570E + 308 aracılığıyla pozitif değerler. Çift duyarlıklı sayılar yaklaşık gerçek bir sayı olarak depolar.  
  
## <a name="remarks"></a>Açıklamalar  
 `Double` Veri türü için bir sayı en büyük ve küçük olası magnitudes sağlar.  
  
 Varsayılan değer olan `Double` 0'dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Hassasiyet.** Kayan nokta sayıları ile çalışırken, bunlar her zaman kesin bir gösterimi belleğe sahip olmadığını unutmayın. Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve `Mod` işleci. Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Sondaki sıfırlar.** Kayan nokta veri türleri sondaki sıfır karakterleri herhangi iç temsilini gerekmez. Örneğin, bunlar 4.2000 4.2 arasında ayrım değil. Sonuç olarak, sondaki sıfır karakterleri görünmez görüntülediğinizde veya yazdırma kayan nokta değerleri.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `R` bir hazır değer zorlar `Double` veri türü. Örneğin, bir tamsayı değeri tarafından izlediyseniz `R`, değeri değiştirilmiş olan bir `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Tanımlayıcı türü karakteri ekleme `#` herhangi bir tanımlayıcı zorlar `Double`. Aşağıdaki örnekte, değişken `num` olarak yazılan bir `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Double?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Double?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)

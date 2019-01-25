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
ms.openlocfilehash: 456383dd2f38e96a8ff18472ff44c65ba7b4a341
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626491"
---
# <a name="double-data-type-visual-basic"></a>Double Veri Türü (Visual Basic)
Ayrı tutma değeri - 1.79769313486231570E + 308 - aracılığıyla aralığındaki IEEE 64-bit (8 bayt) çift duyarlıklı kayan noktalı sayıların imzalı 4.94065645841246544E-324 negatif değerleri ve 4.94065645841246544E-324 1.79769313486231570E + 308 aracılığıyla pozitif değerler. Çift duyarlıklı sayılar yaklaşık bir gerçek sayı olarak depolar.  
  
## <a name="remarks"></a>Açıklamalar  
 `Double` Veri türü, bir sayı için en büyük ve küçük olası massively sağlar.  
  
 Varsayılan değer olan `Double` 0'dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Duyarlık.** Kayan noktalı sayı ile çalıştığınızda, bunlar her zaman kesin bir gösterimi bellekte olmadığını unutmayın. Değer karşılaştırması gibi bazı işlemleri öğesinden bu beklenmeyen sonuçlara neden olabilir ve `Mod` işleci. Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Sondaki sıfırlar.** Kayan nokta veri türleri, sondaki sıfır karakterleri, herhangi bir iç gösterimi yoktur. Örneğin, bunlar 4.2 4.2000 arasında ayrılmaz. Sonuç olarak, sıfır karakter sondaki görünmez görüntülediğinizde veya yazdırma kayan nokta değerleri.  
  
-   **Tür karakterleri.** Değişmez değer türü karakterinin `R` sabit değerine zorlar `Double` veri türü. Örneğin, bir tamsayı değeri tarafından izlediyseniz `R`, değer değiştirilecek bir `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     Tanımlayıcı türü karakteri ekleme `#` herhangi bir tanımlayıcı zorlar `Double`. Aşağıdaki örnekte, değişken `num` olarak yazılmış bir `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Double?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Double?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single Veri Türü](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)

---
title: Single Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 98433c0f1d1008664bb994f3b43fe48a753a432c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324133"
---
# <a name="single-data-type-visual-basic"></a>Single Veri Türü (Visual Basic)
Ayrı tutma IEEE 32-bit (4-bayt) tek duyarlıklı kayan nokta sayı değerini - 3.4028235E + 38 arasında değişen imzalı ile - 1.401298E-45 negatif değerleri ve 1.401298E-45 3.4028235E + 38 pozitif değerler için aracılığıyla. Tek duyarlıklı sayılar yaklaşık bir gerçek sayı olarak depolar.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Single` veri türü, tam veri genişliği gerektirmeyen kayan nokta değerleri içerecek şekilde `Double`. Bazı durumlarda ortak dil çalışma zamanı paketi mümkün olabilir, `Single` değişkenleri yakından birlikte ve bellek tüketimi.  
  
 Varsayılan değer olan `Single` 0'dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Duyarlık.** Kayan noktalı sayı ile çalıştığınızda, bunlar her zaman kesin bir gösterimi bellekte olmadığını aklınızda bulundurun. Değer karşılaştırması gibi bazı işlemleri öğesinden bu beklenmeyen sonuçlara neden olabilir ve `Mod` işleci. Daha fazla bilgi için [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Genişletme.** `Single` Widens veri türü için `Double`. Yani dönüştürebilirsiniz `Single` için `Double` karşılaşmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Sondaki sıfırlar.** Kayan nokta veri türleri, sondaki 0 karakterleri, herhangi bir iç gösterimi yoktur. Örneğin, bunlar 4.2 4.2000 arasında ayrılmaz. Sonuç olarak, sondaki 0 karakterleri görüntülediğinizde veya kayan nokta değerlerini yazdırma görünmez.  
  
-   **Tür karakterleri.** Değişmez değer türü karakterinin `F` sabit değerine zorlar `Single` veri türü. Tanımlayıcı türü karakteri ekleme `!` herhangi bir tanımlayıcı zorlar `Single`.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Single?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Single?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [Decimal Veri Türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double Veri Türü](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)

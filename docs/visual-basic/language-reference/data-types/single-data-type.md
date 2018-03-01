---
title: "Single Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c91dbdf73ed1e26393518001ec8651557e5b780f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="single-data-type-visual-basic"></a>Single Veri Türü (Visual Basic)
Ayrı tutma imzalı IEEE 32-bit (4-bayt) tek duyarlıklı kayan nokta sayıları değerinden - 3.4028235E + 38 arasında değişen ile - 1.401298E-45 negatif değerler ve 1.401298E-45 3.4028235E + 38 pozitif değerler için aracılığıyla. Tek duyarlıklı sayılar yaklaşık gerçek bir sayı olarak depolar.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Single` veri türü tam veri genişliği gerektirmeyen kayan nokta değerlerini içeren `Double`. Bazı durumlarda ortak dil çalışma zamanı paketi olabilir, `Single` değişkenleri yakın işbirliği içinde ve bellek tüketimi.  
  
 Varsayılan değer olan `Single` 0'dır.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Hassasiyet.** Kayan nokta sayıları ile çalışırken, her zaman kesin gösterimi bellekte olmadığı olduğunu aklınızda bulundurun. Değer karşılaştırması gibi bazı işlemleri alanından bu beklenmeyen sonuçlara neden ve `Mod` işleci. Daha fazla bilgi için bkz: [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Genişletme.** `Single` Veri türü widens için `Double`. Bu dönüştürebilirsiniz anlamına gelir `Single` için `Double` karşılaşmadan olmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
-   **Sondaki sıfırlar.** Kayan nokta veri türleri sondaki 0 karakterleri iç herhangi gösterimi yok. Örneğin, bunlar 4.2000 4.2 arasında ayrım değil. Sonuç olarak, görüntülediğinizde veya kayan nokta değerlerini yazdırmak sondaki 0 karakterleri görünmez.  
  
-   **Karakterleri yazın.** Değişmez değer türü karakteri ekleme `F` bir hazır değer zorlar `Single` veri türü. Tanımlayıcı türü karakteri ekleme `!` herhangi bir tanımlayıcı zorlar `Single`.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Single?displayProperty=nameWithType> yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Single?displayProperty=nameWithType>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Ondalık veri türü](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)

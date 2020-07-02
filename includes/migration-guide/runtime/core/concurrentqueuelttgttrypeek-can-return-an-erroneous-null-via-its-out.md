---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622143"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue &lt; T &gt; . Trtypeınfo ek, out parametresi aracılığıyla hatalı bir null döndürebilir

#### <a name="details"></a>Ayrıntılar

Çok iş parçacıklı senaryolarda, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> true döndürebilir, ancak out parametresini boş bir değerle (doğru, atılamıyor değeri yerine) doldurabilirsiniz.

#### <a name="suggestion"></a>Öneri

Bu sorun .NET Framework 4.5.1 düzeltilmiştir. Bu çerçeveye yükseltmek sorunu çözmeyecektir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

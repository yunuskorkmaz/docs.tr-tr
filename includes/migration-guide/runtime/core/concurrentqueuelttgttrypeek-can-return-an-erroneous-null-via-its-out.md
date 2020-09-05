---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497121"
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
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->

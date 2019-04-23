---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805276"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue\<T >. TryPeek, out parametresinin hatalı bir null döndürebilir

|   |   |
|---|---|
|Ayrıntılar|Çok iş parçacıklı bazı senaryolarda <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> true döndürür ancak out parametresi (doğru baktı değeri) yerine null bir değerle doldurun.|
|Öneri|.NET Framework 4.5.1 Bu sorun düzeltilmiştir. Bu çerçeve için yükseltme sorunu çözün.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

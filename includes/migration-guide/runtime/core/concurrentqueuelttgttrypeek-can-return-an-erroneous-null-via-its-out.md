---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236717"
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

---
ms.openlocfilehash: 9084c135769f595491d645e49d24cf507f5f6070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235882"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Dizeler gömülü null değerlere sahip EventListener keser

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> dizeler gömülü null değerlere sahip keser. Boş karakterler tarafından desteklenmez <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> sınıfı. Bu değişiklik yalnızca kullanan uygulamaları etkiler <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okunacak <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> işlemdeki veri ve sınırlayıcı olarak null karakterleri kullanın.|
|Öneri|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> Veri mümkün olduğunda, gömülü null karakterleri kullanmayacak şekilde güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

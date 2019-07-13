---
ms.openlocfilehash: eab476a1d3f275e851e5af4198c30b60ad0c17b8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858609"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners açık anahtar sözcükleri (örneğin, TPL sağlayıcısı) sağlayıcılarıyla olaylardan yakalamayın

|   |   |
|---|---|
|Ayrıntılar|ETW EventListeners boş anahtar sözcüğü maskesiyle açık anahtar sözcükleri sağlayıcılarıyla olaylardan düzgün yakalamayın. .NET Framework 4.5, TPL sağlayıcısı açık anahtar sağlama başladı ve bu sorunu tetiklendi. .NET Framework 4.6, EventListeners artık bu sorunu sağlamak için güncelleştirildi.|
|Öneri|Bu sorunu gidermek için çağrı değiştirin <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> açıkça belirten EnableEvents aşırı çağrılarıyla &quot;her anahtar sözcük&quot; kullanılacak maskesi: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|`Scope`|Kenar|
|Version|4,5|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|


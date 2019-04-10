---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235951"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners açık anahtar sözcükleri (örneğin, TPL sağlayıcısı) sağlayıcılarıyla olaylardan yakalamayın

|   |   |
|---|---|
|Ayrıntılar|ETW EventListeners boş anahtar sözcüğü maskesiyle açık anahtar sözcükleri sağlayıcılarıyla olaylardan düzgün yakalamayın. .NET Framework 4.5, TPL sağlayıcısı açık anahtar sağlama başladı ve bu sorunu tetiklendi. .NET Framework 4.6, EventListeners artık bu sorunu sağlamak için güncelleştirildi.|
|Öneri|Bu sorunu gidermek için çağrı değiştirin <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> açıkça belirten EnableEvents aşırı çağrılarıyla &quot;her anahtar sözcük&quot; kullanılacak maskesi: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

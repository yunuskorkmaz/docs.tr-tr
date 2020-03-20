---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858609"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners açık anahtar kelimeler (TPL sağlayıcısı gibi) sağlayıcılardan olayları yakalamak yok

|   |   |
|---|---|
|Ayrıntılar|Boş bir anahtar kelime maskesi olan ETW EventListeners, açık anahtar kelimelere sahip sağlayıcılardan gelen olayları düzgün bir şekilde yakalamaz. .NET Framework 4.5'te, TPL sağlayıcısı açık anahtar kelimeler sağlamaya başladı ve bu sorunu tetikledi. .NET Framework 4.6'da, EventListener'lar artık bu soruna sahip olmayacak şekilde güncelleştirildi.|
|Öneri|Bu <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> sorunu aşmak için, kullanılacak &quot;anahtar kelime&quot; maskesini açıkça belirten EnableEvents aşırı yüklemesine <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>yapılan çağrıları değiştirin: . Alternatif olarak, bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.|
|Kapsam|Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

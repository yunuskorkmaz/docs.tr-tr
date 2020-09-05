---
ms.openlocfilehash: 5a96b40e5e0df6a47415acecab410444a713632b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496691"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners açık anahtar sözcüklere sahip sağlayıcılardan olayları yakalamaz (TPL sağlayıcısı gibi)

#### <a name="details"></a>Ayrıntılar

Boş bir anahtar sözcük maskesine sahip ETW EventListeners, açık anahtar sözcüklere sahip sağlayıcılardan olayları düzgün bir şekilde yakalamaz. .NET Framework 4,5 ' de, TPL sağlayıcısı açık anahtar sözcükler sağlamaya başladı ve bu sorunu tetikledi. .NET Framework 4,6 ' de EventListeners artık bu soruna sahip olmayacak şekilde güncelleştirilmiştir.

#### <a name="suggestion"></a>Öneri

Bu sorunu geçici olarak çözmek için, ile yapılan çağrıları, <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> &quot; kullanım için herhangi bir anahtar sözcük maskesini açıkça belirten EnableEvents aşırı yüklemesiyle değiştirin &quot; : <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code> . Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`

-->

---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620573"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

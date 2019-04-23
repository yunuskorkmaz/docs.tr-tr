---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805305"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>Aynı aldığı parametreleri (artı kimliği) EventSource.WriteEvent impls WriteEvent geçmelidir

|   |   |
|---|---|
|Ayrıntılar|Çalışma zamanı, artık aşağıdaki belirten sözleşmenin uygular: Öğesinden türetilen bir sınıf <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> tanımlayan bir ETW olay yöntemi temel sınıf çağırmalıdır <code>EventSource.WriteEvent</code> olay kimliği yöntemiyle ETW olay yöntemine geçilen aynı bağımsız değişkenleri tarafından izlenen.|
|Öneri|Bir <xref:System.IndexOutOfRangeException?displayProperty=name> , özel durum bir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> okur <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> bu sözleşmeyi ihlal eden bir olay kaynağı için işlem verileri.|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

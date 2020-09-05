---
ms.openlocfilehash: 99a7fa0fcfce6d490a182f85709b5dd0e0e8c86f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497775"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource. WriteEvent IMPLS 'ın aynı parametreleri aldığı aynı parametreleri (artı ID) iletmeli olması gerekir

#### <a name="details"></a>Ayrıntılar

Çalışma zamanı şimdi aşağıdakileri belirten sözleşmeyi zorluyor: <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> BIR ETW olay yöntemi tanımlayan öğesinden türetilmiş bir sınıf, <code>EventSource.WriteEvent</code> olay kimliği ile bırlıkte, ETW olay yönteminin geçirildiği bağımsız değişkenlerle birlikte temel sınıf metodunu çağırmalıdır.

#### <a name="suggestion"></a>Öneri

<xref:System.IndexOutOfRangeException?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> Bu sözleşmeyi ihlal eden bir olay kaynağı için işlemdeki verileri okuduğunda bir özel durum oluşturulur.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

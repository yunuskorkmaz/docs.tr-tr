---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620574"
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

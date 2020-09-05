---
ms.openlocfilehash: 51ac10e6b4cc9c757cb7f68d7d665982bcb57d4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496943"
---
### <a name="systemactivities-is-now-aptca"></a>System. Activities şimdi APTCA

#### <a name="details"></a>Ayrıntılar

Derleme, <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> özniteliğiyle işaretlenir.

#### <a name="suggestion"></a>Öneri

Türetilmiş sınıflar ile işaretlenemez <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> . Daha önce, türetilmiş türlerin ile işaretlenmiş olması gerekiyordu <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName> . Ancak, bu değişikliğin gerçek bir etkisi olmaması gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

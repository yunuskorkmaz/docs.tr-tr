---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609146"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>ASP.NET StateServer ile oturum durumunu paylaşma, Web grubundaki tüm sunucuların aynı .NET Framework sürümünü kullanmasını gerektirir

#### <a name="details"></a>Ayrıntılar

<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>Oturum durumunu etkinleştirirken, belirtilen Web grubundaki tüm sunucuların, durumun düzgün paylaşılması için .NET Framework aynı sürümünü kullanması gerekir.

#### <a name="suggestion"></a>Öneri

Durumu paylaşan Web sunucularındaki .NET Framework sürümlerini aynı anda yükseltdiğinizden emin olun.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->

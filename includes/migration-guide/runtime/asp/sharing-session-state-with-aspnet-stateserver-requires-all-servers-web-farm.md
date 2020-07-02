---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620544"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Asp.Net StateServer ile oturum durumunu paylaşma, Web grubundaki tüm sunucuların aynı .NET Framework sürümünü kullanmasını gerektirir

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

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|

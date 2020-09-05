---
ms.openlocfilehash: 76425ca03c98cd6a23b8366257f9e0d53b486edb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497486"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="1075b-101">Asp.Net StateServer ile oturum durumunu paylaşma, Web grubundaki tüm sunucuların aynı .NET Framework sürümünü kullanmasını gerektirir</span><span class="sxs-lookup"><span data-stu-id="1075b-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="1075b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1075b-102">Details</span></span>

<span data-ttu-id="1075b-103"><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>Oturum durumunu etkinleştirirken, belirtilen Web grubundaki tüm sunucuların, durumun düzgün paylaşılması için .NET Framework aynı sürümünü kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1075b-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1075b-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="1075b-104">Suggestion</span></span>

<span data-ttu-id="1075b-105">Durumu paylaşan Web sunucularındaki .NET Framework sürümlerini aynı anda yükseltdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1075b-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="1075b-106">Name</span><span class="sxs-lookup"><span data-stu-id="1075b-106">Name</span></span>    | <span data-ttu-id="1075b-107">Değer</span><span class="sxs-lookup"><span data-stu-id="1075b-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1075b-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1075b-108">Scope</span></span>   |<span data-ttu-id="1075b-109">Edge</span><span class="sxs-lookup"><span data-stu-id="1075b-109">Edge</span></span>|
|<span data-ttu-id="1075b-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1075b-110">Version</span></span>|<span data-ttu-id="1075b-111">4,5</span><span class="sxs-lookup"><span data-stu-id="1075b-111">4.5</span></span>|
|<span data-ttu-id="1075b-112">Tür</span><span class="sxs-lookup"><span data-stu-id="1075b-112">Type</span></span>|<span data-ttu-id="1075b-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="1075b-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1075b-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1075b-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->

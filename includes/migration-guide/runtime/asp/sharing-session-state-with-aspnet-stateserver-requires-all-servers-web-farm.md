---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609146"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="4a3a8-101">ASP.NET StateServer ile oturum durumunu paylaşma, Web grubundaki tüm sunucuların aynı .NET Framework sürümünü kullanmasını gerektirir</span><span class="sxs-lookup"><span data-stu-id="4a3a8-101">Sharing session state with ASP.NET StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="4a3a8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4a3a8-102">Details</span></span>

<span data-ttu-id="4a3a8-103"><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>Oturum durumunu etkinleştirirken, belirtilen Web grubundaki tüm sunucuların, durumun düzgün paylaşılması için .NET Framework aynı sürümünü kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a3a8-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4a3a8-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="4a3a8-104">Suggestion</span></span>

<span data-ttu-id="4a3a8-105">Durumu paylaşan Web sunucularındaki .NET Framework sürümlerini aynı anda yükseltdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4a3a8-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="4a3a8-106">Name</span><span class="sxs-lookup"><span data-stu-id="4a3a8-106">Name</span></span>    | <span data-ttu-id="4a3a8-107">Değer</span><span class="sxs-lookup"><span data-stu-id="4a3a8-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4a3a8-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4a3a8-108">Scope</span></span>   |<span data-ttu-id="4a3a8-109">Edge</span><span class="sxs-lookup"><span data-stu-id="4a3a8-109">Edge</span></span>|
|<span data-ttu-id="4a3a8-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4a3a8-110">Version</span></span>|<span data-ttu-id="4a3a8-111">4,5</span><span class="sxs-lookup"><span data-stu-id="4a3a8-111">4.5</span></span>|
|<span data-ttu-id="4a3a8-112">Tür</span><span class="sxs-lookup"><span data-stu-id="4a3a8-112">Type</span></span>|<span data-ttu-id="4a3a8-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4a3a8-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a3a8-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4a3a8-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->

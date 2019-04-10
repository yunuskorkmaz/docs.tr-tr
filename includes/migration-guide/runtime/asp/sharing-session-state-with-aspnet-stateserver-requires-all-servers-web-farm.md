---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235852"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="1c1d6-101">Oturum durumu Asp.Net StateServer ile paylaşımı aynı .NET Framework sürümünü kullanmak için web grubundaki tüm sunucuların gerektirir</span><span class="sxs-lookup"><span data-stu-id="1c1d6-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1c1d6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1c1d6-102">Details</span></span>|<span data-ttu-id="1c1d6-103">Etkinleştirilirken <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> oturum durumunu, belirli bir web grubundaki tüm sunucularda .NET Framework sürümüyle aynı sürümü durumu için sırayla düzgün bir şekilde paylaşılan için kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1c1d6-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="1c1d6-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="1c1d6-104">Suggestion</span></span>|<span data-ttu-id="1c1d6-105">.NET Framework sürümleri üzerinde aynı anda durum paylaşma web sunucuları yükseltme emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c1d6-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="1c1d6-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1c1d6-106">Scope</span></span>|<span data-ttu-id="1c1d6-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="1c1d6-107">Edge</span></span>|
|<span data-ttu-id="1c1d6-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1c1d6-108">Version</span></span>|<span data-ttu-id="1c1d6-109">4,5</span><span class="sxs-lookup"><span data-stu-id="1c1d6-109">4.5</span></span>|
|<span data-ttu-id="1c1d6-110">Tür</span><span class="sxs-lookup"><span data-stu-id="1c1d6-110">Type</span></span>|<span data-ttu-id="1c1d6-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="1c1d6-111">Runtime</span></span>|
|<span data-ttu-id="1c1d6-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1c1d6-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|

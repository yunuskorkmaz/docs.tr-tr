---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981627"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="b9cb0-101">Oturum durumu Asp.Net StateServer ile paylaşımı aynı .NET Framework sürümünü kullanmak için web grubundaki tüm sunucuların gerektirir</span><span class="sxs-lookup"><span data-stu-id="b9cb0-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b9cb0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b9cb0-102">Details</span></span>|<span data-ttu-id="b9cb0-103">Etkinleştirilirken <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> oturum durumunu, belirli bir web grubundaki tüm sunucularda .NET Framework sürümüyle aynı sürümü durumu için sırayla düzgün bir şekilde paylaşılan için kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b9cb0-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="b9cb0-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b9cb0-104">Suggestion</span></span>|<span data-ttu-id="b9cb0-105">.NET Framework sürümleri üzerinde aynı anda durum paylaşma web sunucuları yükseltme emin olun.</span><span class="sxs-lookup"><span data-stu-id="b9cb0-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="b9cb0-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b9cb0-106">Scope</span></span>|<span data-ttu-id="b9cb0-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="b9cb0-107">Edge</span></span>|
|<span data-ttu-id="b9cb0-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b9cb0-108">Version</span></span>|<span data-ttu-id="b9cb0-109">4,5</span><span class="sxs-lookup"><span data-stu-id="b9cb0-109">4.5</span></span>|
|<span data-ttu-id="b9cb0-110">Tür</span><span class="sxs-lookup"><span data-stu-id="b9cb0-110">Type</span></span>|<span data-ttu-id="b9cb0-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="b9cb0-111">Runtime</span></span>|
|<span data-ttu-id="b9cb0-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b9cb0-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|

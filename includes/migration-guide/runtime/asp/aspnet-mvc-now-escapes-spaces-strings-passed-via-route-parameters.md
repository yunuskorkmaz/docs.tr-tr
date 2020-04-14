---
ms.openlocfilehash: 7444ddbdd4a7c5f731fba8528ee2334374fc254e
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275326"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="279db-101">ASP.NET MVC artık rota parametreleri üzerinden geçirilen dizeleri alanlarda kaçar</span><span class="sxs-lookup"><span data-stu-id="279db-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="279db-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="279db-102">Details</span></span>|<span data-ttu-id="279db-103">RFC 2396'ya uymak için, bir rotadan eylem parametreleri doldurulurken rota yollarında boşluklar artık kaçmaktadır.</span><span class="sxs-lookup"><span data-stu-id="279db-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="279db-104">Bu nedenle, <code>/controller/action/some data</code> daha önce rota <code>/controller/action/{data}</code> eşleşen <code>some data</code> ve veri parametresi olarak <code>some%20data</code> sağlamak, şimdi yerine sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="279db-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="279db-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="279db-105">Suggestion</span></span>|<span data-ttu-id="279db-106">Kod, bir rotadan kaçış dize parametreleri için güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="279db-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="279db-107">Orijinal URI gerekirse, bu <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="279db-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="279db-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="279db-108">Scope</span></span>|<span data-ttu-id="279db-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="279db-109">Minor</span></span>|
|<span data-ttu-id="279db-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="279db-110">Version</span></span>|<span data-ttu-id="279db-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="279db-111">4.5.2</span></span>|
|<span data-ttu-id="279db-112">Tür</span><span class="sxs-lookup"><span data-stu-id="279db-112">Type</span></span>|<span data-ttu-id="279db-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="279db-113">Runtime</span></span>|
|<span data-ttu-id="279db-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="279db-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|

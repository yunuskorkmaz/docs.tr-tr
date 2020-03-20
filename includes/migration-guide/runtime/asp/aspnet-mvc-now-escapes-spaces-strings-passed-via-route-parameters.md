---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803195"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="e3daa-101">ASP.NET MVC artık rota parametreleri üzerinden geçirilen dizeleri alanlarda kaçar</span><span class="sxs-lookup"><span data-stu-id="e3daa-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e3daa-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e3daa-102">Details</span></span>|<span data-ttu-id="e3daa-103">RFC 2396'ya uymak için, bir rotadan eylem parametreleri doldurulurken rota yollarında boşluklar artık kaçmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3daa-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="e3daa-104">Bu nedenle, <code>/controller/action/some data</code> daha önce rota <code>/controller/action/{data}</code> eşleşen <code>some data</code> ve veri parametresi olarak <code>some%20data</code> sağlamak, şimdi yerine sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e3daa-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="e3daa-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e3daa-105">Suggestion</span></span>|<span data-ttu-id="e3daa-106">Kod, bir rotadan kaçış dize parametreleri için güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e3daa-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="e3daa-107">Orijinal URI gerekirse, bu <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="e3daa-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="e3daa-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e3daa-108">Scope</span></span>|<span data-ttu-id="e3daa-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="e3daa-109">Minor</span></span>|
|<span data-ttu-id="e3daa-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e3daa-110">Version</span></span>|<span data-ttu-id="e3daa-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="e3daa-111">4.5.2</span></span>|
|<span data-ttu-id="e3daa-112">Tür</span><span class="sxs-lookup"><span data-stu-id="e3daa-112">Type</span></span>|<span data-ttu-id="e3daa-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="e3daa-113">Runtime</span></span>|
|<span data-ttu-id="e3daa-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e3daa-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

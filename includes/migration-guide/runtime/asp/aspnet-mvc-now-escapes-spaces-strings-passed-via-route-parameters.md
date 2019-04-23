---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774279"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="a6722-101">ASP.NET MVC artık alanları dizelerinde de rota parametreleri aracılığıyla düğümlere geçirilir çıkışları</span><span class="sxs-lookup"><span data-stu-id="a6722-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a6722-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a6722-102">Details</span></span>|<span data-ttu-id="a6722-103">RFC 2396 uymak için rota yollarda alanları artık bir rota eylemi parametrelerinden doldurulurken atlanır.</span><span class="sxs-lookup"><span data-stu-id="a6722-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="a6722-104">Bu nedenle, oysa <code>/controller/action/some data</code> rota daha önce eşleşir <code>/controller/action/{data}</code> ve sağlayın <code>some data</code> veri parametre olarak, artık sağlayacak <code>some%20data</code> bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="a6722-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="a6722-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="a6722-105">Suggestion</span></span>|<span data-ttu-id="a6722-106">Kod bir rotadaki dizesi parametreleri unescape güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6722-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="a6722-107">Özgün bir URI gerekirse ile erişilebileceğini <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="a6722-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="a6722-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a6722-108">Scope</span></span>|<span data-ttu-id="a6722-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="a6722-109">Minor</span></span>|
|<span data-ttu-id="a6722-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a6722-110">Version</span></span>|<span data-ttu-id="a6722-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="a6722-111">4.5.2</span></span>|
|<span data-ttu-id="a6722-112">Tür</span><span class="sxs-lookup"><span data-stu-id="a6722-112">Type</span></span>|<span data-ttu-id="a6722-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="a6722-113">Runtime</span></span>|
|<span data-ttu-id="a6722-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a6722-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

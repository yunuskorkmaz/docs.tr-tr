---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236677"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="74e29-101">ASP.NET MVC artık alanları dizelerinde de rota parametreleri aracılığıyla düğümlere geçirilir çıkışları</span><span class="sxs-lookup"><span data-stu-id="74e29-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="74e29-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="74e29-102">Details</span></span>|<span data-ttu-id="74e29-103">RFC 2396 uymak için rota yollarda alanları artık bir rota eylemi parametrelerinden doldurulurken atlanır.</span><span class="sxs-lookup"><span data-stu-id="74e29-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="74e29-104">Bu nedenle, oysa <code>/controller/action/some data</code> rota daha önce eşleşir <code>/controller/action/{data}</code> ve sağlayın <code>some data</code> veri parametre olarak, artık sağlayacak <code>some%20data</code> bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="74e29-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="74e29-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="74e29-105">Suggestion</span></span>|<span data-ttu-id="74e29-106">Kod bir rotadaki dizesi parametreleri unescape güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="74e29-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="74e29-107">Özgün bir URI gerekirse ile erişilebileceğini <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="74e29-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="74e29-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="74e29-108">Scope</span></span>|<span data-ttu-id="74e29-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="74e29-109">Minor</span></span>|
|<span data-ttu-id="74e29-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="74e29-110">Version</span></span>|<span data-ttu-id="74e29-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="74e29-111">4.5.2</span></span>|
|<span data-ttu-id="74e29-112">Tür</span><span class="sxs-lookup"><span data-stu-id="74e29-112">Type</span></span>|<span data-ttu-id="74e29-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="74e29-113">Runtime</span></span>|
|<span data-ttu-id="74e29-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="74e29-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

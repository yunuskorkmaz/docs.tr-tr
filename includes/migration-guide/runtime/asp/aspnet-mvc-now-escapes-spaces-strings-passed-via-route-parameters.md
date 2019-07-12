---
ms.openlocfilehash: 8d058d3297471e67459164f18358b1d143465712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803195"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="0b36c-101">ASP.NET MVC artık alanları dizelerinde de rota parametreleri aracılığıyla düğümlere geçirilir çıkışları</span><span class="sxs-lookup"><span data-stu-id="0b36c-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0b36c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0b36c-102">Details</span></span>|<span data-ttu-id="0b36c-103">RFC 2396 uymak için rota yollarda alanları artık bir rota eylemi parametrelerinden doldurulurken atlanır.</span><span class="sxs-lookup"><span data-stu-id="0b36c-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="0b36c-104">Bu nedenle, oysa <code>/controller/action/some data</code> rota daha önce eşleşir <code>/controller/action/{data}</code> ve sağlayın <code>some data</code> veri parametre olarak, artık sağlayacak <code>some%20data</code> bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="0b36c-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="0b36c-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="0b36c-105">Suggestion</span></span>|<span data-ttu-id="0b36c-106">Kod bir rotadaki dizesi parametreleri unescape güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b36c-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="0b36c-107">Özgün bir URI gerekirse ile erişilebileceğini <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="0b36c-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="0b36c-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0b36c-108">Scope</span></span>|<span data-ttu-id="0b36c-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="0b36c-109">Minor</span></span>|
|<span data-ttu-id="0b36c-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0b36c-110">Version</span></span>|<span data-ttu-id="0b36c-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="0b36c-111">4.5.2</span></span>|
|<span data-ttu-id="0b36c-112">Tür</span><span class="sxs-lookup"><span data-stu-id="0b36c-112">Type</span></span>|<span data-ttu-id="0b36c-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="0b36c-113">Runtime</span></span>|
|<span data-ttu-id="0b36c-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0b36c-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|


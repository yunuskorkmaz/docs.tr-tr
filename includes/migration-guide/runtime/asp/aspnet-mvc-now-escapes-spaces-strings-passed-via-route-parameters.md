---
ms.openlocfilehash: afbf34710c75d0f0586ddfdb2e7937d8d76d5399
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497728"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="594a0-101">ASP.NET MVC şimdi yol parametreleri aracılığıyla geçirilen dizelerin içindeki boşlukları çıkar</span><span class="sxs-lookup"><span data-stu-id="594a0-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="594a0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="594a0-102">Details</span></span>

<span data-ttu-id="594a0-103">RFC 2396 ' e uymak için rota yollarındaki boşluklar artık bir rotadaki eylem parametreleri doldurulurken kaçışla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="594a0-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="594a0-104">Bu nedenle,  <code>/controller/action/some data</code> daha önce rotayla eşleşmekte <code>/controller/action/{data}</code> ve <code>some data</code> veri parametresi olarak sağlayacağından, artık <code>some%20data</code> bunun yerine sağlama yapılır.</span><span class="sxs-lookup"><span data-stu-id="594a0-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="594a0-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="594a0-105">Suggestion</span></span>

<span data-ttu-id="594a0-106">Kod, bir rotadaki kaçış dize parametrelerine karşı güncellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="594a0-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="594a0-107">Özgün URI gerekliyse, ile erişilebilir <xref:System.Net.HttpWebRequest.RequestUri> . OriginalString API 'SI.</span><span class="sxs-lookup"><span data-stu-id="594a0-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="594a0-108">Name</span><span class="sxs-lookup"><span data-stu-id="594a0-108">Name</span></span>    | <span data-ttu-id="594a0-109">Değer</span><span class="sxs-lookup"><span data-stu-id="594a0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="594a0-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="594a0-110">Scope</span></span>   |<span data-ttu-id="594a0-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="594a0-111">Minor</span></span>|
|<span data-ttu-id="594a0-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="594a0-112">Version</span></span>|<span data-ttu-id="594a0-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="594a0-113">4.5.2</span></span>|
|<span data-ttu-id="594a0-114">Tür</span><span class="sxs-lookup"><span data-stu-id="594a0-114">Type</span></span>|<span data-ttu-id="594a0-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="594a0-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="594a0-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="594a0-116">Affected APIs</span></span>

- <xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)>

<!--

#### Affected APIs

- `M:System.Web.Mvc.RouteAttribute.#ctor(System.String)`

-->

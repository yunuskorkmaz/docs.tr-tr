---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620536"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="bc8ab-101">ASP.NET MVC şimdi yol parametreleri aracılığıyla geçirilen dizelerin içindeki boşlukları çıkar</span><span class="sxs-lookup"><span data-stu-id="bc8ab-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="bc8ab-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bc8ab-102">Details</span></span>

<span data-ttu-id="bc8ab-103">RFC 2396 ' e uymak için rota yollarındaki boşluklar artık bir rotadaki eylem parametreleri doldurulurken kaçışla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="bc8ab-104">Bu nedenle, <code>/controller/action/some data</code> daha önce rotayla eşleşmekte <code>/controller/action/{data}</code> ve <code>some data</code> veri parametresi olarak sağlayacağından, artık <code>some%20data</code> bunun yerine sağlama yapılır.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bc8ab-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="bc8ab-105">Suggestion</span></span>

<span data-ttu-id="bc8ab-106">Kod, bir rotadaki kaçış dize parametrelerine karşı güncellenmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="bc8ab-107">Özgün URI gerekliyse, ile erişilebilir <xref:System.Net.HttpWebRequest.RequestUri> . OriginalString API 'SI.</span><span class="sxs-lookup"><span data-stu-id="bc8ab-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="bc8ab-108">Name</span><span class="sxs-lookup"><span data-stu-id="bc8ab-108">Name</span></span>    | <span data-ttu-id="bc8ab-109">Değer</span><span class="sxs-lookup"><span data-stu-id="bc8ab-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bc8ab-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bc8ab-110">Scope</span></span>   |<span data-ttu-id="bc8ab-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="bc8ab-111">Minor</span></span>|
|<span data-ttu-id="bc8ab-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bc8ab-112">Version</span></span>|<span data-ttu-id="bc8ab-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="bc8ab-113">4.5.2</span></span>|
|<span data-ttu-id="bc8ab-114">Tür</span><span class="sxs-lookup"><span data-stu-id="bc8ab-114">Type</span></span>|<span data-ttu-id="bc8ab-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="bc8ab-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bc8ab-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bc8ab-116">Affected APIs</span></span>

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|

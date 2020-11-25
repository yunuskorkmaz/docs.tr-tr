---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032772"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="e7e16-101">HTTP: yanıt gövdesi altyapı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e7e16-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="e7e16-102">Bir HTTP yanıt gövdesini yedekleyen altyapı değişti.</span><span class="sxs-lookup"><span data-stu-id="e7e16-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="e7e16-103">`HttpResponse`Doğrudan kullanıyorsanız, herhangi bir kod değişikliği yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e7e16-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="e7e16-104">Sarmalandıysanız veya değiştiriyorsanız daha fazla bilgi edinin `HttpResponse.Body` `HttpContext.Features` .</span><span class="sxs-lookup"><span data-stu-id="e7e16-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7e16-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e7e16-105">Version introduced</span></span>

<span data-ttu-id="e7e16-106">3,0</span><span class="sxs-lookup"><span data-stu-id="e7e16-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e7e16-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e7e16-107">Old behavior</span></span>

<span data-ttu-id="e7e16-108">HTTP yanıt gövdesi ile ilişkili üç API vardı:</span><span class="sxs-lookup"><span data-stu-id="e7e16-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="e7e16-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e7e16-109">New behavior</span></span>

<span data-ttu-id="e7e16-110">`HttpResponse.Body`' Yi değiştirirseniz, `IHttpResponseBodyFeature` `StreamResponseBodyFeature` tüm beklenen API 'ler için varsayılan uygulamalar sağlamak üzere, kullanarak, verilen akışın çevresindeki bir sarmalayıcı ile tamamen değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e7e16-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="e7e16-111">Özgün akışın geri ayarlanması bu değişikliği geri alır.</span><span class="sxs-lookup"><span data-stu-id="e7e16-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e7e16-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e7e16-112">Reason for change</span></span>

<span data-ttu-id="e7e16-113">Mosyon, yanıt gövdesi API 'Lerini tek bir yeni özellik arabirimi halinde birleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e16-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7e16-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e7e16-114">Recommended action</span></span>

<span data-ttu-id="e7e16-115">`IHttpResponseBodyFeature`Daha önce, veya kullandığınızı kullanın `IHttpResponseFeature.Body` `IHttpSendFileFeature` `IHttpBufferingFeature` .</span><span class="sxs-lookup"><span data-stu-id="e7e16-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="e7e16-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="e7e16-116">Category</span></span>

<span data-ttu-id="e7e16-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e7e16-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7e16-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e7e16-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->

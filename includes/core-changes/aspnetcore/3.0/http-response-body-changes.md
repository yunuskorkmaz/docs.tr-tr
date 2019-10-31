---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198589"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="a8321-101">HTTP: yanıt gövdesi altyapı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a8321-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="a8321-102">Bir HTTP yanıt gövdesini yedekleyen altyapı değişti.</span><span class="sxs-lookup"><span data-stu-id="a8321-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="a8321-103">`HttpResponse` doğrudan kullanıyorsanız, herhangi bir kod değişikliği yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a8321-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="a8321-104">`HttpResponse.Body` sardıysanız veya değiştiriyorsanız ya da `HttpContext.Features`erişimi varsa daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="a8321-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8321-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a8321-105">Version introduced</span></span>

<span data-ttu-id="a8321-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a8321-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a8321-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a8321-107">Old behavior</span></span>

<span data-ttu-id="a8321-108">HTTP yanıt gövdesi ile ilişkili üç API vardı:</span><span class="sxs-lookup"><span data-stu-id="a8321-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="a8321-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a8321-109">New behavior</span></span>

<span data-ttu-id="a8321-110">`HttpResponse.Body`değiştirirseniz, tüm `IHttpResponseBodyFeature`, tüm beklenen API 'Ler için varsayılan uygulamalar sağlamak üzere `StreamResponseBodyFeature` kullanarak verilen akışlarınızın etrafında bir sarmalayıcı ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a8321-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="a8321-111">Özgün akışın geri ayarlanması bu değişikliği geri alır.</span><span class="sxs-lookup"><span data-stu-id="a8321-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a8321-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a8321-112">Reason for change</span></span>

<span data-ttu-id="a8321-113">Mosyon, yanıt gövdesi API 'Lerini tek bir yeni özellik arabirimi halinde birleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8321-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8321-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a8321-114">Recommended action</span></span>

<span data-ttu-id="a8321-115">Daha önce `IHttpResponseFeature.Body`, `IHttpSendFileFeature` veya `IHttpBufferingFeature` ' ü kullandığınız `IHttpResponseBodyFeature` ' ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8321-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="a8321-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="a8321-116">Category</span></span>

<span data-ttu-id="a8321-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a8321-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8321-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a8321-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->

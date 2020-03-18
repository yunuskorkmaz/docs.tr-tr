---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198589"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="541fb-101">HTTP: Yanıt gövde altyapı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="541fb-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="541fb-102">BIR HTTP yanıt organını destekleyen altyapı değişti.</span><span class="sxs-lookup"><span data-stu-id="541fb-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="541fb-103">Doğrudan kullanıyorsanız, `HttpResponse` herhangi bir kod değişikliği yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="541fb-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="541fb-104">Sarma lıyor, değiştiriyor `HttpResponse.Body` veya erişiyorsanız `HttpContext.Features`daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="541fb-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="541fb-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="541fb-105">Version introduced</span></span>

<span data-ttu-id="541fb-106">3,0</span><span class="sxs-lookup"><span data-stu-id="541fb-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="541fb-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="541fb-107">Old behavior</span></span>

<span data-ttu-id="541fb-108">HTTP yanıt gövdesi ile ilişkili üç API vardı:</span><span class="sxs-lookup"><span data-stu-id="541fb-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="541fb-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="541fb-109">New behavior</span></span>

<span data-ttu-id="541fb-110">Değiştirirseniz, `HttpResponse.Body`beklenen API'lerin tümü için varsayılan uygulamaları `StreamResponseBodyFeature` sağlamak için verilen akışınızın etrafındaki bir sarmalayıcıyla tümünün `IHttpResponseBodyFeature` yerini alır.</span><span class="sxs-lookup"><span data-stu-id="541fb-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="541fb-111">Özgün akışı geri ayarlamak bu değişikliği geri döndürer.</span><span class="sxs-lookup"><span data-stu-id="541fb-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="541fb-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="541fb-112">Reason for change</span></span>

<span data-ttu-id="541fb-113">Motivasyon tek bir yeni özellik arabirimi içine yanıt gövdesi API'ler birleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="541fb-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="541fb-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="541fb-114">Recommended action</span></span>

<span data-ttu-id="541fb-115">Daha `IHttpResponseBodyFeature` önce kullandığınız `IHttpResponseFeature.Body` `IHttpSendFileFeature`yeri , `IHttpBufferingFeature`veya .</span><span class="sxs-lookup"><span data-stu-id="541fb-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="541fb-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="541fb-116">Category</span></span>

<span data-ttu-id="541fb-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="541fb-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="541fb-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="541fb-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->

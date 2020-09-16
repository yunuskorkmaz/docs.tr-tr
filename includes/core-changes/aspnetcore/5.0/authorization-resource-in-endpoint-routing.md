---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441562"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="e181e-101">Yetkilendirme: uç nokta yönlendirmesinde kaynak HttpContext 'dir</span><span class="sxs-lookup"><span data-stu-id="e181e-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="e181e-102">ASP.NET Core 3,1 ' de Endpoint Routing kullanılırken, yetkilendirme için kullanılan kaynak uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="e181e-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="e181e-103">Bu yaklaşım, yol verilerine () erişim kazanmak için yeterli değildi <xref:Microsoft.AspNetCore.Routing.RouteData> .</span><span class="sxs-lookup"><span data-stu-id="e181e-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="e181e-104">Daha önce MVC 'de, <xref:Microsoft.AspNetCore.Http.HttpContext> hem uç nokta () hem de yol verilerine erişim sağlayan bir kaynak geçirildi <xref:Microsoft.AspNetCore.Http.Endpoint> .</span><span class="sxs-lookup"><span data-stu-id="e181e-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="e181e-105">Bu değişiklik, yetkilendirmeye geçirilen kaynağın her zaman ' i olmasını sağlar `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="e181e-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e181e-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e181e-106">Version introduced</span></span>

<span data-ttu-id="e181e-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="e181e-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e181e-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e181e-108">Old behavior</span></span>

<span data-ttu-id="e181e-109">Endpoint Routing ve yetkilendirme ara yazılımı ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) veya [[Yetkilendir]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) öznitelikleri kullanılırken, yetkilendirme öğesine geçirilen kaynak eşleşen uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="e181e-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e181e-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e181e-110">New behavior</span></span>

<span data-ttu-id="e181e-111">Endpoint Routing, ' i `HttpContext` Yetkilendirmeyi geçirir.</span><span class="sxs-lookup"><span data-stu-id="e181e-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e181e-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e181e-112">Reason for change</span></span>

<span data-ttu-id="e181e-113">Uç noktasına öğesinden ulaşabilirsiniz `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="e181e-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="e181e-114">Ancak, uç noktadan yol verileri gibi şeylere kadar bir yöntem yoktu.</span><span class="sxs-lookup"><span data-stu-id="e181e-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="e181e-115">Uç nokta olmayan yönlendirmenin işlevselliğinde bir kayıp vardı.</span><span class="sxs-lookup"><span data-stu-id="e181e-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e181e-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e181e-116">Recommended action</span></span>

<span data-ttu-id="e181e-117">Uygulamanız uç nokta kaynağını kullanıyorsa, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` uç noktaya erişmeye devam etmek için üzerinde öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e181e-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="e181e-118">ASP.NET Core 5,0 Preview 8 ve üzeri sürümlerde, ile eski davranışa dönüştürebilirsiniz <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="e181e-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="e181e-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e181e-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="e181e-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="e181e-120">Category</span></span>

<span data-ttu-id="e181e-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e181e-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e181e-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e181e-122">Affected APIs</span></span>

<span data-ttu-id="e181e-123">Yok</span><span class="sxs-lookup"><span data-stu-id="e181e-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

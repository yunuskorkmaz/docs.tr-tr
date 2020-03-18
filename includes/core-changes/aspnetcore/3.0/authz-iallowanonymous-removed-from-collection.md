---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901635"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="c25a0-101">Yetkilendirme: IAllowAnonymous YetkilendirmeFilterContext.Filters kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="c25a0-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="c25a0-102">Core 3.0ASP.NET itibariyle MVC, denetleyiciler ve eylem yöntemleri üzerinde keşfedilen [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) öznitelikleri için [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) eklemez.</span><span class="sxs-lookup"><span data-stu-id="c25a0-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="c25a0-103">Bu değişiklik <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>türevleri için yerel olarak ele alınmıştır, ancak <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> bu ve uygulamalar için bir kırılma değişiklik' s.</span><span class="sxs-lookup"><span data-stu-id="c25a0-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="c25a0-104">[[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) özelliğine sarılmış bu tür uygulamalar, hem yapılandırma hem de bağımlılık enjeksiyonu gerektiğinde güçlü bir şekilde yazılmış, öznitelik tabanlı yetkilendirme elde etmenin [popüler](https://stackoverflow.com/a/41348219/608220) ve desteklenen bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="c25a0-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c25a0-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c25a0-105">Version introduced</span></span>

<span data-ttu-id="c25a0-106">3,0</span><span class="sxs-lookup"><span data-stu-id="c25a0-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c25a0-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c25a0-107">Old behavior</span></span>

<span data-ttu-id="c25a0-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>[AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) koleksiyonunda yer aldı.</span><span class="sxs-lookup"><span data-stu-id="c25a0-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="c25a0-109">Arabirimin varlığını sınamak, filtreyi tek tek denetleyici yöntemlerini geçersiz kılmak veya devre dışı etmek için geçerli bir yaklaşımdı.</span><span class="sxs-lookup"><span data-stu-id="c25a0-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c25a0-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c25a0-110">New behavior</span></span>

<span data-ttu-id="c25a0-111">`IAllowAnonymous``AuthorizationFilterContext.Filters` koleksiyonda artık görünmez.</span><span class="sxs-lookup"><span data-stu-id="c25a0-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="c25a0-112">`IAsyncAuthorizationFilter`eski davranışa bağlı olan uygulamalar genellikle aralıklı HTTP 401 Yetkisiz veya HTTP 403 Yasak yanıtlarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c25a0-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c25a0-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c25a0-113">Reason for change</span></span>

<span data-ttu-id="c25a0-114">Core 3.0'ASP.NET yeni bir uç nokta yönlendirme stratejisi tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="c25a0-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c25a0-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c25a0-115">Recommended action</span></span>

<span data-ttu-id="c25a0-116">Uç nokta meta verilerini `IAllowAnonymous`arama .</span><span class="sxs-lookup"><span data-stu-id="c25a0-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="c25a0-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c25a0-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="c25a0-118">Bu tekniğin bir örneği [bu HasAllowAnonymous yönteminde](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="c25a0-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="c25a0-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="c25a0-119">Category</span></span>

<span data-ttu-id="c25a0-120">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="c25a0-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c25a0-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c25a0-121">Affected APIs</span></span>

<span data-ttu-id="c25a0-122">None</span><span class="sxs-lookup"><span data-stu-id="c25a0-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

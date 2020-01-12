---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901635"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="60c1d-101">Yetkilendirme: ıallowanonymous, AuthorizationFilterContext. Filters öğesinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="60c1d-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="60c1d-102">ASP.NET Core 3,0 itibariyle, MVC, denetleyiciler ve eylem yöntemlerinde bulunan [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) öznitelikleri Için [allowanonymousfilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) eklemez.</span><span class="sxs-lookup"><span data-stu-id="60c1d-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="60c1d-103">Bu değişiklik, <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>türevleri için yerel olarak adreslenir, ancak <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> ve <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> uygulamalarına yönelik bir son değişiklik.</span><span class="sxs-lookup"><span data-stu-id="60c1d-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="60c1d-104">Bir [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) özniteliğinde Sarmalanan uygulamalar, hem yapılandırma hem de bağımlılık ekleme gerektiğinde kesin olarak belirlenmiş, öznitelik tabanlı yetkilendirme elde etmenin [popüler](https://stackoverflow.com/a/41348219/608220) ve desteklenen bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="60c1d-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="60c1d-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="60c1d-105">Version introduced</span></span>

<span data-ttu-id="60c1d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="60c1d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="60c1d-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="60c1d-107">Old behavior</span></span>

<span data-ttu-id="60c1d-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> [Authorizationfiltercontext. Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) koleksiyonunda göründü.</span><span class="sxs-lookup"><span data-stu-id="60c1d-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="60c1d-109">Arabirim varlığına yönelik test, tek tek denetleyici yöntemlerinde filtreyi geçersiz kılmak veya devre dışı bırakmak için geçerli bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="60c1d-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="60c1d-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="60c1d-110">New behavior</span></span>

<span data-ttu-id="60c1d-111">`IAllowAnonymous` artık `AuthorizationFilterContext.Filters` koleksiyonunda görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="60c1d-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="60c1d-112">Eski davranışa bağlı `IAsyncAuthorizationFilter` uygulamalar genellikle aralıklı HTTP 401 Yetkisiz veya HTTP 403 Yasak yanıtlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="60c1d-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="60c1d-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="60c1d-113">Reason for change</span></span>

<span data-ttu-id="60c1d-114">ASP.NET Core 3,0 ' de yeni bir uç nokta yönlendirme stratejisi sunuldu.</span><span class="sxs-lookup"><span data-stu-id="60c1d-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="60c1d-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="60c1d-115">Recommended action</span></span>

<span data-ttu-id="60c1d-116">`IAllowAnonymous`için uç nokta meta verilerinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="60c1d-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="60c1d-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60c1d-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="60c1d-118">Bu [HasAllowAnonymous yönteminde](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)bu tekniğin bir örneği görülür.</span><span class="sxs-lookup"><span data-stu-id="60c1d-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="60c1d-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="60c1d-119">Category</span></span>

<span data-ttu-id="60c1d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="60c1d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60c1d-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="60c1d-121">Affected APIs</span></span>

<span data-ttu-id="60c1d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="60c1d-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

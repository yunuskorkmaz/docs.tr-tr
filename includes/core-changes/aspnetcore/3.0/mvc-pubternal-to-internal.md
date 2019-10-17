---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394427"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="3f5bc-101">MVC: "Pubternal" türleri iç olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="3f5bc-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="3f5bc-102">ASP.NET Core 3,0 ' de, MVC içindeki tüm "pubternal" türleri desteklenen bir ad alanında `public` ya da uygun şekilde `internal` olarak güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3f5bc-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3f5bc-103">Change description</span></span>

<span data-ttu-id="3f5bc-104">ASP.NET Core, "pubternal" türleri `public` olarak belirtilir, ancak bir @no__t -1-sonfixed ad alanında yer alır.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="3f5bc-105">Bu türler `public` olsa da, destek ilkesi yoktur ve bu değişiklikler, son değişikliklere tabidir.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="3f5bc-106">Ne yazık ki, bu türlerin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f5bc-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3f5bc-107">Version introduced</span></span>

<span data-ttu-id="3f5bc-108">3.0</span><span class="sxs-lookup"><span data-stu-id="3f5bc-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3f5bc-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3f5bc-109">Old behavior</span></span>

<span data-ttu-id="3f5bc-110">MVC 'deki bazı türler `public`, ancak `.Internal` ad alanında.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="3f5bc-111">Bu türlerin destek ilkesi yoktu ve değişiklikler ortadan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3f5bc-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3f5bc-112">New behavior</span></span>

<span data-ttu-id="3f5bc-113">Bu tür türler desteklenen bir ad alanında `public` ya da `internal` olarak işaretlenmiş olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3f5bc-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3f5bc-114">Reason for change</span></span>

<span data-ttu-id="3f5bc-115">"Pubternal" türlerinin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f5bc-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3f5bc-116">Recommended action</span></span>

<span data-ttu-id="3f5bc-117">Gerçekten `public` olan ve yeni, desteklenen bir ad alanına taşınan türler kullanıyorsanız, başvurularınızı yeni ad alanlarıyla eşleşecek şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="3f5bc-118">@No__t-0 olarak işaretlenen türler kullanıyorsanız, alternatif bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="3f5bc-119">Daha önce "pubternal" türleri genel kullanım için hiçbir şekilde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="3f5bc-120">Bu ad alanlarında uygulamalarınız için kritik olan belirli türler varsa, [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues)' da bir sorun yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span> <span data-ttu-id="3f5bc-121">İstenen türlerin @no__t yapılması için dikkat edilmesi gereken noktalar-0.</span><span class="sxs-lookup"><span data-stu-id="3f5bc-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="3f5bc-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="3f5bc-122">Category</span></span>

<span data-ttu-id="3f5bc-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3f5bc-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f5bc-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3f5bc-124">Affected APIs</span></span>

<span data-ttu-id="3f5bc-125">Bu değişiklik aşağıdaki ad alanları türlerini içerir:</span><span class="sxs-lookup"><span data-stu-id="3f5bc-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->

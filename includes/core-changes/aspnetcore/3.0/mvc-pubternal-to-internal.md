---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901644"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="7aa5f-101">MVC: "Pubternal" türleri dahili olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="7aa5f-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="7aa5f-102">Core 3.0ASP.NET, MVC'deki tüm "pubternal" türleri `public` desteklenen bir ad `internal` alanında veya uygun şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7aa5f-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="7aa5f-103">Change description</span></span>

<span data-ttu-id="7aa5f-104">ASP.NET Core'da "pubternal" türleri `public` -suffixed `.Internal`ad alanında olduğu ancak ikamet ettiğini beyan eder.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="7aa5f-105">Bu tür `public`olmasına ne kadar , hiçbir destek ilkesi var ve kırılma değişikliklerine tabidir.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="7aa5f-106">Ne yazık ki, bu tür kazara kullanımı, bu projelerde değişiklikler kırma ve çerçeve korumak için yeteneği sınırlayan sonuçlanan yaygın olmuştur.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7aa5f-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="7aa5f-107">Version introduced</span></span>

<span data-ttu-id="7aa5f-108">3,0</span><span class="sxs-lookup"><span data-stu-id="7aa5f-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7aa5f-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7aa5f-109">Old behavior</span></span>

<span data-ttu-id="7aa5f-110">MVC bazı türleri `public` ama `.Internal` bir ad alanı vardı.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="7aa5f-111">Bu tür hiçbir destek ilkesi vardı ve kırılma değişikliklere tabi idi.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7aa5f-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7aa5f-112">New behavior</span></span>

<span data-ttu-id="7aa5f-113">Tüm bu tür desteklenen `public` bir ad alanında olmak üzere `internal`güncelleştirilir veya .</span><span class="sxs-lookup"><span data-stu-id="7aa5f-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7aa5f-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7aa5f-114">Reason for change</span></span>

<span data-ttu-id="7aa5f-115">"Pubternal" türlerinin kazara kullanımı yaygın olmuştur, bu projelerde değişiklikler kırma ve çerçeve korumak için yeteneğini sınırlayan sonuçlanan.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7aa5f-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7aa5f-116">Recommended action</span></span>

<span data-ttu-id="7aa5f-117">Gerçekten `public` olmuş ve yeni, desteklenen bir ad alanına taşınmış türleri kullanıyorsanız, başvurularınızı yeni ad alanlarıyla eşleşecek şekilde güncelleyin.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="7aa5f-118">Olarak işaretlenmiş türleri `internal`kullanıyorsanız, bir alternatif bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="7aa5f-119">Daha önce "pubternal" türleri kamu kullanımı için desteklenmedi.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="7aa5f-120">Bu ad alanlarında uygulamalarınız için kritik öneme sahip belirli türler varsa, [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)adresinden bir sorun dosyalayın.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="7aa5f-121">İstenen tiplerin `public`yapılmasında dikkat edilmesi gereken hususlar göz önünde bulundurulabilir.</span><span class="sxs-lookup"><span data-stu-id="7aa5f-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="7aa5f-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="7aa5f-122">Category</span></span>

<span data-ttu-id="7aa5f-123">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="7aa5f-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7aa5f-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7aa5f-124">Affected APIs</span></span>

<span data-ttu-id="7aa5f-125">Bu değişiklik, aşağıdaki ad alanlarındatürleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7aa5f-125">This change includes types in the following namespaces:</span></span>

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

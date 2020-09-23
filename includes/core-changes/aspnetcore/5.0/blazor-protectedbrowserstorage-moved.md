---
ms.openlocfilehash: a9545c66d3873b5114fe66e13c77ddc28e20020e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077611"
---
### <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="28670-101">Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı</span><span class="sxs-lookup"><span data-stu-id="28670-101">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="28670-102">ASP.NET Core 5,0 RC2 sürümünün bir parçası olarak, `ProtectedBrowserStorage` özellik ASP.NET Core paylaşılan çerçeveye taşınır.</span><span class="sxs-lookup"><span data-stu-id="28670-102">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="28670-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="28670-103">Version introduced</span></span>

<span data-ttu-id="28670-104">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="28670-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="28670-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="28670-105">Old behavior</span></span>

<span data-ttu-id="28670-106">ASP.NET Core 5,0 Preview 8 ' de, özelliği [Microsoft. AspNetCore. components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) paketinin bir parçası olarak kullanılabilir ancak yalnızca Blazor WebAssembly ' de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="28670-106">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="28670-107">ASP.NET Core 5,0 RC1 sürümünde, özelliği paylaşılan çerçeveye başvuran [Microsoft. AspNetCore. components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) paketinin bir parçası olarak kullanılabilir `Microsoft.AspNetCore.App` .</span><span class="sxs-lookup"><span data-stu-id="28670-107">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="28670-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="28670-108">New behavior</span></span>

<span data-ttu-id="28670-109">ASP.NET Core 5,0 RC2 'de, artık bu özelliği kullanmak için bir NuGet paket başvurusuna gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="28670-109">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="28670-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="28670-110">Reason for change</span></span>

<span data-ttu-id="28670-111">Paylaşılan çerçeveye taşıma, müşterilerin beklediği Kullanıcı deneyimi için daha iyi bir uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="28670-111">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="28670-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="28670-112">Recommended action</span></span>

<span data-ttu-id="28670-113">ASP.NET Core 5,0 RC1 'den yükseltme yapıyorsanız, aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="28670-113">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="28670-114">`Microsoft.AspNetCore.Components.ProtectedBrowserStorage`Paket başvurusunu projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="28670-114">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="28670-115">`using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.</span><span class="sxs-lookup"><span data-stu-id="28670-115">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="28670-116">Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="28670-116">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="28670-117">ASP.NET Core 5,0 Preview 8 ' den yükseltiyorsanız aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="28670-117">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="28670-118">`Microsoft.AspNetCore.Components.Web.Extensions`Paket başvurusunu projeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="28670-118">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="28670-119">`using Microsoft.AspNetCore.Components.Web.Extensions;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.</span><span class="sxs-lookup"><span data-stu-id="28670-119">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="28670-120">Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .</span><span class="sxs-lookup"><span data-stu-id="28670-120">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

#### <a name="category"></a><span data-ttu-id="28670-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="28670-121">Category</span></span>

<span data-ttu-id="28670-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="28670-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="28670-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="28670-123">Affected APIs</span></span>

<span data-ttu-id="28670-124">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="28670-124">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

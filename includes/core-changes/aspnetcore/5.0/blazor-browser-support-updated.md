---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804938"
---
### <a name="blazor-updated-browser-support"></a><span data-ttu-id="2b2d8-101">Blazor: tarayıcı desteği güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="2b2d8-101">Blazor: Updated browser support</span></span>

<span data-ttu-id="2b2d8-102">ASP.NET Core 5,0, bazıları eski tarayıcılarla uyumsuz olan [Yeni Blazor özellikleri](https://github.com/dotnet/aspnetcore/issues/21514)sunuyor.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-102">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="2b2d8-103">ASP.NET Core 5,0 ' de Blazor tarafından desteklenen tarayıcıların listesi, buna göre güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-103">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="2b2d8-104">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).</span><span class="sxs-lookup"><span data-stu-id="2b2d8-104">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b2d8-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2b2d8-105">Version introduced</span></span>

<span data-ttu-id="2b2d8-106">5.0</span><span class="sxs-lookup"><span data-stu-id="2b2d8-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2b2d8-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="2b2d8-107">Old behavior</span></span>

<span data-ttu-id="2b2d8-108">Blazor Server, yeterli polydolgular ile Microsoft Internet Explorer 11 ' i destekler.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-108">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="2b2d8-109">Blazor Server ve Blazor WebAssembly, [Microsoft Edge eski](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)sürümünde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-109">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2b2d8-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="2b2d8-110">New behavior</span></span>

<span data-ttu-id="2b2d8-111">ASP.NET Core 5,0 ' deki Blazor sunucusu Microsoft Internet Explorer 11 ile desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-111">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="2b2d8-112">Blazor Server ve Blazor WebAssembly, Microsoft Edge eski sürümünde tam olarak işlevsel değildir.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-112">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2b2d8-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="2b2d8-113">Reason for change</span></span>

<span data-ttu-id="2b2d8-114">ASP.NET Core 5,0 ' deki yeni Blazor özellikleri bu eski tarayıcılarla uyumsuzdur ve bu eski tarayıcıların kullanımı, bu eski tarayıcıların kullanımına karşı azalmış olur.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-114">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="2b2d8-115">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="2b2d8-115">For more information, see the following resources:</span></span>

* [<span data-ttu-id="2b2d8-116">Microsoft Edge için Windows desteği, Ayrıca 9 Mart 2021 ' de sona eriyor</span><span class="sxs-lookup"><span data-stu-id="2b2d8-116">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="2b2d8-117">Microsoft 365 uygulamalar ve hizmetler, Microsoft Internet Explorer 11 için 17 Ağustos 2021 ' de destek sona acaktır.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-117">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a><span data-ttu-id="2b2d8-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2b2d8-118">Recommended action</span></span>

<span data-ttu-id="2b2d8-119">Bu eski tarayıcılardan [Yeni, Kmuum tabanlı Microsoft Edge](https://www.microsoft.com/edge)'e yükseltin.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-119">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="2b2d8-120">Bu eski tarayıcıları desteklemesi gereken Blazor uygulamaları için ASP.NET Core 3,1 kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-120">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="2b2d8-121">ASP.NET Core 3,1 ' deki Blazor için desteklenen tarayıcılar listesi değişmemiştir ve [desteklenen platformlarda](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b2d8-121">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

#### <a name="category"></a><span data-ttu-id="2b2d8-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="2b2d8-122">Category</span></span>

<span data-ttu-id="2b2d8-123">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="2b2d8-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b2d8-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2b2d8-124">Affected APIs</span></span>

<span data-ttu-id="2b2d8-125">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2b2d8-125">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416281"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="da5ea-101">Blazor: NuGet paketlerinin hedef çerçevesi değiştirildi</span><span class="sxs-lookup"><span data-stu-id="da5ea-101">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="da5ea-102">Blazor 3,2 WebAssembly projeleri .NET Standard 2,1 () hedefine derlendi `<TargetFramework>netstandard2.1</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="da5ea-102">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="da5ea-103">ASP.NET Core 5,0 ' de, hem Blazor Server hem de Blazor WebAssembly projeleri .NET 5,0 () öğesini hedefleyin `<TargetFramework>net5.0</TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="da5ea-103">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="da5ea-104">Hedef Framework değişikliğine daha iyi uyum sağlamak için aşağıdaki Blazor paketleri artık .NET Standard 2,1 ' i hedeflemiyor:</span><span class="sxs-lookup"><span data-stu-id="da5ea-104">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="da5ea-105">Microsoft. AspNetCore. Components</span><span class="sxs-lookup"><span data-stu-id="da5ea-105">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="da5ea-106">Microsoft. AspNetCore. components. Authorization</span><span class="sxs-lookup"><span data-stu-id="da5ea-106">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="da5ea-107">Microsoft. AspNetCore. components. Forms</span><span class="sxs-lookup"><span data-stu-id="da5ea-107">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="da5ea-108">Microsoft. AspNetCore. components. Web</span><span class="sxs-lookup"><span data-stu-id="da5ea-108">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="da5ea-109">Microsoft. AspNetCore. components. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="da5ea-109">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="da5ea-110">Microsoft. AspNetCore. components. WebAssembly. Authentication</span><span class="sxs-lookup"><span data-stu-id="da5ea-110">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="da5ea-111">Microsoft.JSbirlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="da5ea-111">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="da5ea-112">Microsoft.JSInterop. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="da5ea-112">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="da5ea-113">Microsoft. Authentication. WebAssembly. msal</span><span class="sxs-lookup"><span data-stu-id="da5ea-113">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="da5ea-114">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).</span><span class="sxs-lookup"><span data-stu-id="da5ea-114">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da5ea-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="da5ea-115">Version introduced</span></span>

<span data-ttu-id="da5ea-116">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="da5ea-116">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da5ea-117">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="da5ea-117">Old behavior</span></span>

<span data-ttu-id="da5ea-118">Blazor 3,1 ve 3,2 ' de, paketler .NET Standard 2,1 ve .NET Core 3,1 ' i hedefler.</span><span class="sxs-lookup"><span data-stu-id="da5ea-118">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da5ea-119">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="da5ea-119">New behavior</span></span>

<span data-ttu-id="da5ea-120">ASP.NET Core 5,0 ' de, paketler .NET 5,0 ' i hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="da5ea-120">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da5ea-121">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="da5ea-121">Reason for change</span></span>

<span data-ttu-id="da5ea-122">.NET hedef Framework gereksinimleriyle daha iyi uyum sağlamak için değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="da5ea-122">The change was made to better align with .NET target framework requirements.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da5ea-123">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="da5ea-123">Recommended action</span></span>

<span data-ttu-id="da5ea-124">Blazor 3,2 WebAssembly projeleri, paket başvurularını 5. x.x. güncelleştirme kapsamında .NET 5,0 ' i hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="da5ea-124">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="da5ea-125">Bu paketlerin birine başvuran kitaplıklar, gereksinimlerine bağlı olarak .NET 5,0 veya birden çok hedef hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="da5ea-125">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

#### <a name="category"></a><span data-ttu-id="da5ea-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="da5ea-126">Category</span></span>

<span data-ttu-id="da5ea-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da5ea-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da5ea-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="da5ea-128">Affected APIs</span></span>

<span data-ttu-id="da5ea-129">Yok</span><span class="sxs-lookup"><span data-stu-id="da5ea-129">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

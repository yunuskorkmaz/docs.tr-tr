---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344297"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="4af07-101">Razor: Runtime derleme bir paket taşındı</span><span class="sxs-lookup"><span data-stu-id="4af07-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="4af07-102">Razor görünümleri ve Razor Pages çalışma zamanı derleme desteği ayrı bir pakettaşındı.</span><span class="sxs-lookup"><span data-stu-id="4af07-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4af07-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="4af07-103">Version introduced</span></span>

<span data-ttu-id="4af07-104">3,0</span><span class="sxs-lookup"><span data-stu-id="4af07-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4af07-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="4af07-105">Old behavior</span></span>

<span data-ttu-id="4af07-106">Runtime derleme ek paketler gerek kalmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4af07-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4af07-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="4af07-107">New behavior</span></span>

<span data-ttu-id="4af07-108">İşlevsellik [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) paketine taşındı.</span><span class="sxs-lookup"><span data-stu-id="4af07-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="4af07-109">Aşağıdaki API'ler daha `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` önce çalışma zamanı derlemesini desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4af07-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="4af07-110">API'ler artık `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span><span class="sxs-lookup"><span data-stu-id="4af07-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="4af07-111">`RazorViewEngineOptions.FileProviders`şimdi`MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="4af07-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="4af07-112">`RazorViewEngineOptions.AdditionalCompilationReferences`şimdi`MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="4af07-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="4af07-113">Buna ek `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` olarak, kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="4af07-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="4af07-114">Dosya değişikliklerinde yeniden `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` derleme, pakete başvurarak varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4af07-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4af07-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4af07-115">Reason for change</span></span>

<span data-ttu-id="4af07-116">Bu değişiklik, Core'un Roslyn'e olan ortak çerçeve bağımlılığını ASP.NET kaldırmak için gerekliydi.</span><span class="sxs-lookup"><span data-stu-id="4af07-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4af07-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4af07-117">Recommended action</span></span>

<span data-ttu-id="4af07-118">Razor dosyalarının çalışma zamanı derlemesi veya yeniden derlenmesine ihtiyaç duyan uygulamalar aşağıdaki adımları atmalıdır:</span><span class="sxs-lookup"><span data-stu-id="4af07-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="4af07-119">`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` Pakete bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4af07-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="4af07-120">Bir çağrı içerecek `Startup.ConfigureServices` şekilde projenin yöntemini `AddRazorRuntimeCompilation`güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4af07-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="4af07-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4af07-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="4af07-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="4af07-122">Category</span></span>

<span data-ttu-id="4af07-123">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="4af07-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4af07-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4af07-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

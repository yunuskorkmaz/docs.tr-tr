---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394160"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="24b6e-101">Razor: çalışma zamanı derlemesi bir pakete taşındı</span><span class="sxs-lookup"><span data-stu-id="24b6e-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="24b6e-102">Razor görünümlerinin ve Razor Pages çalışma zamanı derlenmesi desteği ayrı bir pakete taşındı.</span><span class="sxs-lookup"><span data-stu-id="24b6e-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24b6e-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="24b6e-103">Version introduced</span></span>

<span data-ttu-id="24b6e-104">3.0</span><span class="sxs-lookup"><span data-stu-id="24b6e-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="24b6e-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="24b6e-105">Old behavior</span></span>

<span data-ttu-id="24b6e-106">Çalışma zamanı derlemesi ek paketlere gerek olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24b6e-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="24b6e-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="24b6e-107">New behavior</span></span>

<span data-ttu-id="24b6e-108">İşlevsellik `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` paketine taşınmıştır.</span><span class="sxs-lookup"><span data-stu-id="24b6e-108">The functionality has been moved to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

<span data-ttu-id="24b6e-109">Aşağıdaki API 'Ler, çalışma zamanı derlemesini desteklemek için `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` ' da daha önce kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24b6e-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="24b6e-110">API 'Ler artık `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` yoluyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24b6e-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

<span data-ttu-id="24b6e-111">Ayrıca, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="24b6e-111">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="24b6e-112">Dosya değişikliklerinde yeniden derleme, `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` paketine başvurarak varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="24b6e-112">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="24b6e-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="24b6e-113">Reason for change</span></span>

<span data-ttu-id="24b6e-114">Bu değişiklik, Roslyn 'de ASP.NET Core paylaşılan çerçeve bağımlılığını kaldırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24b6e-114">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24b6e-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="24b6e-115">Recommended action</span></span>

<span data-ttu-id="24b6e-116">Razor dosyalarının çalışma zamanı derlemesini veya yeniden derlemesini gerektiren uygulamalar aşağıdaki adımları almalıdır:</span><span class="sxs-lookup"><span data-stu-id="24b6e-116">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="24b6e-117">@No__t-0 paketine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24b6e-117">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="24b6e-118">Projenin `Startup.ConfigureServices` yöntemini `AddMvcRazorRuntimeCompilation` ' e bir çağrı içerecek şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="24b6e-118">Update the project's `Startup.ConfigureServices` method to include a call to `AddMvcRazorRuntimeCompilation`.</span></span> <span data-ttu-id="24b6e-119">Örneğin, `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="24b6e-119">For example, in `Startup.ConfigureServices`:</span></span>

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="24b6e-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="24b6e-120">Category</span></span>

<span data-ttu-id="24b6e-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="24b6e-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24b6e-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="24b6e-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

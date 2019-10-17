---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394160"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: çalışma zamanı derlemesi bir pakete taşındı

Razor görünümlerinin ve Razor Pages çalışma zamanı derlenmesi desteği ayrı bir pakete taşındı.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Çalışma zamanı derlemesi ek paketlere gerek olmadan kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

İşlevsellik `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` paketine taşınmıştır.

Aşağıdaki API 'Ler, çalışma zamanı derlemesini desteklemek için `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` ' da daha önce kullanılabilir. API 'Ler artık `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` yoluyla kullanılabilir.

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Ayrıca, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` kaldırılmıştır. Dosya değişikliklerinde yeniden derleme, `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` paketine başvurarak varsayılan olarak etkinleştirilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Roslyn 'de ASP.NET Core paylaşılan çerçeve bağımlılığını kaldırmak için gereklidir.

#### <a name="recommended-action"></a>Önerilen eylem

Razor dosyalarının çalışma zamanı derlemesini veya yeniden derlemesini gerektiren uygulamalar aşağıdaki adımları almalıdır:

1. @No__t-0 paketine bir başvuru ekleyin.
1. Projenin `Startup.ConfigureServices` yöntemini `AddMvcRazorRuntimeCompilation` ' e bir çağrı içerecek şekilde güncelleştirin. Örneğin, `Startup.ConfigureServices`:

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

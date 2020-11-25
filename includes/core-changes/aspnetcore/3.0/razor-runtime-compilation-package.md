---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032852"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: çalışma zamanı derlemesi bir pakete taşındı

Razor görünümlerinin ve Razor Pages çalışma zamanı derlenmesi desteği ayrı bir pakete taşındı.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Çalışma zamanı derlemesi ek paketlere gerek olmadan kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

İşlevsellik, [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) paketine taşınmıştır.

Aşağıdaki API 'Ler, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` çalışma zamanı derlemesini desteklemek için daha önce ' de kullanılabilir. API 'Ler ile artık kullanılabilir `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` .

- `RazorViewEngineOptions.FileProviders` Artık `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` Artık `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Ayrıca, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` kaldırılmıştır. Dosya değişikliklerinde yeniden derleme, pakete başvurarak varsayılan olarak etkindir `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Roslyn 'de ASP.NET Core paylaşılan çerçeve bağımlılığını kaldırmak için gereklidir.

#### <a name="recommended-action"></a>Önerilen eylem

Razor dosyalarının çalışma zamanı derlemesini veya yeniden derlemesini gerektiren uygulamalar aşağıdaki adımları almalıdır:

1. Pakete bir başvuru ekleyin `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` .
1. `Startup.ConfigureServices`İçin bir çağrı içerecek şekilde projenin metodunu güncelleştirin `AddRazorRuntimeCompilation` . Örnek:

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

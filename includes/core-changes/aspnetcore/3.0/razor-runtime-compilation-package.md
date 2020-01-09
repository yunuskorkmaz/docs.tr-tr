---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344297"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: çalışma zamanı derlemesi bir pakete taşındı

Razor görünümlerinin ve Razor Pages çalışma zamanı derlenmesi desteği ayrı bir pakete taşındı.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Çalışma zamanı derlemesi ek paketlere gerek olmadan kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

İşlevsellik, [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) paketine taşınmıştır.

Aşağıdaki API 'Ler, çalışma zamanı derlemesini desteklemek için daha önce `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` ' de kullanıma sunulmuştur. API 'Ler artık `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`aracılığıyla kullanılabilir.

- `RazorViewEngineOptions.FileProviders` Şimdi `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` Şimdi `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Ayrıca, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` kaldırılmıştır. Dosya değişikliklerinde yeniden derleme, `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` paketine başvurarak varsayılan olarak etkinleştirilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Roslyn 'de ASP.NET Core paylaşılan çerçeve bağımlılığını kaldırmak için gereklidir.

#### <a name="recommended-action"></a>Önerilen eylem

Razor dosyalarının çalışma zamanı derlemesini veya yeniden derlemesini gerektiren uygulamalar aşağıdaki adımları almalıdır:

1. `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` paketine bir başvuru ekleyin.
1. Projenin `Startup.ConfigureServices` yöntemini `AddRazorRuntimeCompilation`çağrısı içerecek şekilde güncelleştirin. Örneğin:

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

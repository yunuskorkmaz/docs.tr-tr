---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344297"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: Runtime derleme bir paket taşındı

Razor görünümleri ve Razor Pages çalışma zamanı derleme desteği ayrı bir pakettaşındı.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Runtime derleme ek paketler gerek kalmadan kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

İşlevsellik [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) paketine taşındı.

Aşağıdaki API'ler daha `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` önce çalışma zamanı derlemesini desteklemek için kullanılabilir. API'ler artık `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders`şimdi`MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences`şimdi`MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

Buna ek `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` olarak, kaldırıldı. Dosya değişikliklerinde yeniden `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` derleme, pakete başvurarak varsayılan olarak etkinleştirilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Core'un Roslyn'e olan ortak çerçeve bağımlılığını ASP.NET kaldırmak için gerekliydi.

#### <a name="recommended-action"></a>Önerilen eylem

Razor dosyalarının çalışma zamanı derlemesi veya yeniden derlenmesine ihtiyaç duyan uygulamalar aşağıdaki adımları atmalıdır:

1. `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` Pakete bir başvuru ekleyin.
1. Bir çağrı içerecek `Startup.ConfigureServices` şekilde projenin yöntemini `AddRazorRuntimeCompilation`güncelleştirin. Örnek:

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

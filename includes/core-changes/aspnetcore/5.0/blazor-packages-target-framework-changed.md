---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416281"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor: NuGet paketlerinin hedef çerçevesi değiştirildi

Blazor 3,2 WebAssembly projeleri .NET Standard 2,1 () hedefine derlendi `<TargetFramework>netstandard2.1</TargetFramework>` . ASP.NET Core 5,0 ' de, hem Blazor Server hem de Blazor WebAssembly projeleri .NET 5,0 () öğesini hedefleyin `<TargetFramework>net5.0</TargetFramework>` . Hedef Framework değişikliğine daha iyi uyum sağlamak için aşağıdaki Blazor paketleri artık .NET Standard 2,1 ' i hedeflemiyor:

* [Microsoft. AspNetCore. Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft. AspNetCore. components. Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft. AspNetCore. components. Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft. AspNetCore. components. Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft. AspNetCore. components. WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft. AspNetCore. components. WebAssembly. Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSbirlikte çalışma](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop. WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft. Authentication. WebAssembly. msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 7

#### <a name="old-behavior"></a>Eski davranış

Blazor 3,1 ve 3,2 ' de, paketler .NET Standard 2,1 ve .NET Core 3,1 ' i hedefler.

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 5,0 ' de, paketler .NET 5,0 ' i hedefleyin.

#### <a name="reason-for-change"></a>Değişiklik nedeni

.NET hedef Framework gereksinimleriyle daha iyi uyum sağlamak için değişiklik yapılmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Blazor 3,2 WebAssembly projeleri, paket başvurularını 5. x.x. güncelleştirme kapsamında .NET 5,0 ' i hedeflemelidir. Bu paketlerin birine başvuran kitaplıklar, gereksinimlerine bağlı olarak .NET 5,0 veya birden çok hedef hedefleyebilir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Hiçbiri

<!--

#### Affected APIs

Not detectable via API analysis

-->

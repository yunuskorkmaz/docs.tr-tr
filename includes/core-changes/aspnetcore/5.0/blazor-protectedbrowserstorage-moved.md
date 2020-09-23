---
ms.openlocfilehash: a9545c66d3873b5114fe66e13c77ddc28e20020e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077611"
---
### <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a>Blazor: ProtectedBrowserStorage özelliği paylaşılan çerçeveye taşındı

ASP.NET Core 5,0 RC2 sürümünün bir parçası olarak, `ProtectedBrowserStorage` özellik ASP.NET Core paylaşılan çerçeveye taşınır.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core 5,0 Preview 8 ' de, özelliği [Microsoft. AspNetCore. components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) paketinin bir parçası olarak kullanılabilir ancak yalnızca Blazor WebAssembly ' de kullanılabilir.

ASP.NET Core 5,0 RC1 sürümünde, özelliği paylaşılan çerçeveye başvuran [Microsoft. AspNetCore. components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) paketinin bir parçası olarak kullanılabilir `Microsoft.AspNetCore.App` .

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 5,0 RC2 'de, artık bu özelliği kullanmak için bir NuGet paket başvurusuna gerek yoktur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Paylaşılan çerçeveye taşıma, müşterilerin beklediği Kullanıcı deneyimi için daha iyi bir uyum sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 5,0 RC1 'den yükseltme yapıyorsanız, aşağıdaki adımları izleyin:

1. `Microsoft.AspNetCore.Components.ProtectedBrowserStorage`Paket başvurusunu projeden kaldırın.
1. `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.
1. Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .

ASP.NET Core 5,0 Preview 8 ' den yükseltiyorsanız aşağıdaki adımları uygulayın:

1. `Microsoft.AspNetCore.Components.Web.Extensions`Paket başvurusunu projeden kaldırın.
1. `using Microsoft.AspNetCore.Components.Web.Extensions;` yerine `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;` yazın.
1. Sınıfınızı olan çağrısını kaldırın `AddProtectedBrowserStorage` `Startup` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Hiçbiri

<!--

#### Affected APIs

Not detectable via API analysis

-->

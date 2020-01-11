---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901831"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: JavaScript istemci paketi adı değiştirildi

ASP.NET Core 3,0 Preview 7 ' de, SignalR JavaScript istemci paketi adı `@aspnet/signalr` `@microsoft/signalr`olarak değiştirildi. Ad değişikliği, SignalR 'nin Azure SignalR hizmeti sayesinde yalnızca ASP.NET Core uygulamalardan daha fazla yararlı olduğunu yansıtır.

Bu değişikliğe tepki vermek için *Package. JSON* dosyalarınızda, `require` deyimlerinizin ve ECMAScript `import` deyiminizdeki başvuruları değiştirin. Bu yeniden adlandırma kapsamında hiçbir API değişmeyecektir.

Tartışma için bkz. [DotNet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

İstemci paketi `@aspnet/signalr`olarak adlandırılmıştı.

#### <a name="new-behavior"></a>Yeni davranış

İstemci paketine `@microsoft/signalr`adı verilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Ad değişikliği, SignalR 'nin Azure SignalR hizmeti için teşekkürler ASP.NET Core uygulamalar ötesinde yararlı olduğunu açıklığa kavuşturar.

#### <a name="recommended-action"></a>Önerilen eylem

Yeni pakete geçiş `@microsoft/signalr`.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

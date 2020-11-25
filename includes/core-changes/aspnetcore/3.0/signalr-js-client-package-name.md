---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032882"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: JavaScript istemci paketi adı değiştirildi

ASP.NET Core 3,0 Preview 7 ' de, SignalR JavaScript istemci paketi adı ' dan ' a değiştirilmiştir `@aspnet/signalr` `@microsoft/signalr` . Ad değişikliği, SignalR 'nin Azure SignalR hizmeti sayesinde yalnızca ASP.NET Core uygulamalardan daha fazla yararlı olduğunu yansıtır.

Bu değişikliğe tepki vermek için, dosyalar, *package.json* `require` deyimler ve ECMAScript deyimleriylepackage.jsbaşvuruları değiştirin `import` . Bu yeniden adlandırma kapsamında hiçbir API değişmeyecektir.

Tartışma için bkz. [DotNet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

İstemci paketi adı `@aspnet/signalr` .

#### <a name="new-behavior"></a>Yeni davranış

İstemci paketinin adı `@microsoft/signalr` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Ad değişikliği, SignalR 'nin Azure SignalR hizmeti için teşekkürler ASP.NET Core uygulamalar ötesinde yararlı olduğunu açıklığa kavuşturar.

#### <a name="recommended-action"></a>Önerilen eylem

Yeni pakete geçiş yapın `@microsoft/signalr` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

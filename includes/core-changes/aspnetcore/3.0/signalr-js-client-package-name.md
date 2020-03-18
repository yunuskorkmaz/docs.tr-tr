---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901831"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: JavaScript istemci paket adı değiştirildi

Core 3.0 Preview 7ASP.NET, SignalR JavaScript istemci `@aspnet/signalr` `@microsoft/signalr`paket adı . Ad değişikliği, Azure SignalR Hizmeti sayesinde SignalR'ın ASP.NET Core uygulamasından daha kullanışlı olduğu gerçeğini yansıtır.

Bu değişikliğe tepki vermek *için, paket.json* dosyalarınızdaki, `require` deyimlerinizdeki ve ECMAScript `import` deyimlerinizdeki başvuruları değiştirin. Bu yeniden adın bir parçası olarak hiçbir API değişmez.

Tartışma için [dotnet/aspnetcore#11637'ye](https://github.com/dotnet/aspnetcore/issues/11637)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

İstemci paketi `@aspnet/signalr`nin adı .

#### <a name="new-behavior"></a>Yeni davranış

İstemci paketi `@microsoft/signalr`nin adı .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Ad değişikliği, Azure SignalR Hizmeti sayesinde SignalR'ın ASP.NET Core uygulamalarının ötesinde yararlı olduğunu açıklar.

#### <a name="recommended-action"></a>Önerilen eylem

Yeni pakete `@microsoft/signalr`geçin.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

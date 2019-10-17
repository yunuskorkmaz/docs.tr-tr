---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394189"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: JavaScript istemci paketi adı değiştirildi

ASP.NET Core 3,0 Preview 7 ' de, SignalR JavaScript istemci paketi adı `@aspnet/signalr` ' dan `@microsoft/signalr` ' e değişti. Ad değişikliği, SignalR 'nin Azure SignalR hizmeti sayesinde yalnızca ASP.NET Core uygulamalardan daha fazla yararlı olduğunu yansıtır.

Bu değişikliğe tepki vermek için *Package. JSON* dosyalarınızda, `require` deyimlerinizin ve ECMAScript `import` deyiminizdeki başvuruları değiştirin. Bu yeniden adlandırma kapsamında hiçbir API değişmeyecektir.

Tartışma için bkz. [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

İstemci paketi `@aspnet/signalr` olarak adlandırılmıştı.

#### <a name="new-behavior"></a>Yeni davranış

İstemci paketinin adı `@microsoft/signalr` ' dır.

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

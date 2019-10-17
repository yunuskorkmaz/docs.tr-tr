---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393994"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: bağlantı bağdaştırıcıları kaldırıldı

"Pubternal" API 'Lerini `public` ' a taşımanın bir parçası olarak, `IConnectionAdapter` kavramı Kestrel ' den kaldırılmıştır. Bağlantı bağdaştırıcıları bağlantı ara yazılımı ile değiştiriliyor (ASP.NET Core işlem hattındaki HTTP ara hattına benzer ancak alt düzey bağlantılar için). HTTPS ve bağlantı günlüğü bağlantı bağdaştırıcılarından bağlantı ara yazılıma taşındı. Bu uzantı yöntemleri sorunsuz şekilde çalışmaya devam etmelidir, ancak uygulama ayrıntıları değişmiştir.

Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412). Tartışma için bkz. [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

@No__t-0 kullanılarak Kestrel genişletilebilirlik bileşenleri oluşturuldu.

#### <a name="new-behavior"></a>Yeni davranış

Kestrel genişletilebilirlik bileşenleri, [Ara yazılım](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)olarak oluşturulur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, daha esnek bir genişletilebilirlik mimarisi sağlamaya yöneliktir.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 ' ın tüm uygulamalarını, [burada](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)gösterildiği gibi yeni ara yazılım düzenlerini kullanacak şekilde dönüştürün.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->

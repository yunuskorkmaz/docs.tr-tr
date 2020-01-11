---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901714"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: bağlantı bağdaştırıcıları kaldırıldı

"Pubternal" API 'Lerini `public`'a taşıma kapsamında, bir `IConnectionAdapter` kavramı Kestrel ' den kaldırılmıştır. Bağlantı bağdaştırıcıları bağlantı ara yazılımı ile değiştiriliyor (ASP.NET Core işlem hattındaki HTTP ara hattına benzer ancak alt düzey bağlantılar için). HTTPS ve bağlantı günlüğü bağlantı bağdaştırıcılarından bağlantı ara yazılıma taşındı. Bu uzantı yöntemleri sorunsuz şekilde çalışmaya devam etmelidir, ancak uygulama ayrıntıları değişmiştir.

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412). Tartışma için bkz. [DotNet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`IConnectionAdapter`kullanılarak Kestrel genişletilebilirlik bileşenleri oluşturuldu.

#### <a name="new-behavior"></a>Yeni davranış

Kestrel genişletilebilirlik bileşenleri, [Ara yazılım](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)olarak oluşturulur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, daha esnek bir genişletilebilirlik mimarisi sağlamaya yöneliktir.

#### <a name="recommended-action"></a>Önerilen eylem

`IConnectionAdapter` tüm uygulamalarını, [burada](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)gösterildiği gibi yeni ara yazılım düzenlerini kullanacak şekilde dönüştürün.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->

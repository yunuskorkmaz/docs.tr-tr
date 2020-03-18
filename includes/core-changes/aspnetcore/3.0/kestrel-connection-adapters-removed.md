---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901714"
---
### <a name="kestrel-connection-adapters-removed"></a>Kerkenez: Bağlantı bağdaştırıcıları kaldırıldı

"Pubternal" API'leri taşımak için `public`hareketin bir `IConnectionAdapter` parçası olarak, bir kavramı Kerkenez kaldırıldı. Bağlantı bağdaştırıcıları bağlantı ara yazılımları ile değiştirilmektedir (ASP.NET Core ardışık lıktaki HTTP ara yazılımlarına benzer, ancak alt düzey bağlantılar için). HTTPS ve bağlantı günlüğü bağlantı bağdaştırıcılarından bağlantı ara yazılımlarına geçti. Bu uzantı yöntemleri sorunsuz çalışmaya devam etmelidir, ancak uygulama ayrıntıları değişti.

Daha fazla bilgi için [dotnet/aspnetcore#11412'ye](https://github.com/dotnet/aspnetcore/pull/11412)bakın. Tartışma için [dotnet/aspnetcore#11475'e](https://github.com/dotnet/aspnetcore/issues/11475)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Kerkenez ekstensibilite `IConnectionAdapter`bileşenleri kullanılarak oluşturuldu.

#### <a name="new-behavior"></a>Yeni davranış

Kerkenez ekstensibilite bileşenleri [ara yazılım](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)olarak oluşturulur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, daha esnek bir genişletilebilirlik mimarisi sağlamak için tasarlanmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Burada gösterildiği gibi `IConnectionAdapter` yeni ara yazılım deseni [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)kullanmak için herhangi bir uygulama dönüştürün.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->

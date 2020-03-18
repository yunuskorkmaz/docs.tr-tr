---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901687"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıkları kaldırıldı

ASP.NET Core'un oyun için daha `ObjectPoolProvider` fazla ödeme yapmasını sağlamanın bir parçası olarak, bu bağımlılıklar ana kümeden çıkarıldı. `ObjectPoolProvider` Şimdi güvenen belirli bileşenler kendilerini ekleyin.

Tartışma için [dotnet/aspnetcore#5944'e](https://github.com/dotnet/aspnetcore/issues/5944)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`WebHostBuilder`di `ObjectPoolProvider` kapsayıcıda varsayılan olarak sağlar.

#### <a name="new-behavior"></a>Yeni davranış

`WebHostBuilder`artık varsayılan `ObjectPoolProvider` olarak DI kapsayıcısında sağlar.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik ASP.NET Core oyun için daha fazla ödeme yapmak için yapıldı.

#### <a name="recommended-action"></a>Önerilen eylem

Bileşeniniz bunu `ObjectPoolProvider`gerektiriyorsa, `IServiceCollection`bağımlılıklarınıza .

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

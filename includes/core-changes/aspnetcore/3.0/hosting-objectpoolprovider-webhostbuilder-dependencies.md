---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901687"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı

ASP.NET Core yürütmek için daha fazla ödeme yapma kapsamında, `ObjectPoolProvider` ana bağımlılıklar kümesinden kaldırılmıştır. `ObjectPoolProvider` bağlı belirli bileşenler artık kendisini ekler.

Tartışma için bkz. [DotNet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`WebHostBuilder`, DI kapsayıcısında varsayılan olarak `ObjectPoolProvider` sağlar.

#### <a name="new-behavior"></a>Yeni davranış

`WebHostBuilder` artık varsayılan olarak DI kapsayıcısında `ObjectPoolProvider` sağlamaz.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik ASP.NET Core yürütmek için daha fazla ödeme yapmak üzere yapılmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Bileşeniniz `ObjectPoolProvider`gerektiriyorsa, `IServiceCollection`aracılığıyla bağımlılıklarınızın eklenmesi gerekir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

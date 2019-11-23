---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394317"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı

ASP.NET Core yürütmek için daha fazla ödeme yapma kapsamında, `ObjectPoolProvider` ana bağımlılıklar kümesinden kaldırılmıştır. `ObjectPoolProvider` bağlı belirli bileşenler artık kendisini ekler.

Tartışma için bkz. [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

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

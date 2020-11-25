---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032756"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı

Yürütme için ASP.NET Core daha fazla ödeme yapma kapsamında, `ObjectPoolProvider` ana bağımlılıklar kümesinden kaldırılmıştır. Artık bağlı olan belirli bileşenler kendisini `ObjectPoolProvider` ekler.

Tartışma için bkz. [DotNet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`WebHostBuilder``ObjectPoolProvider`dı kapsayıcısında varsayılan olarak sağlar.

#### <a name="new-behavior"></a>Yeni davranış

`WebHostBuilder` Artık `ObjectPoolProvider` Varsayılan olarak dı kapsayıcısında sağlamaz.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik ASP.NET Core yürütmek için daha fazla ödeme yapmak üzere yapılmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Bileşeniniz gerektiriyorsa `ObjectPoolProvider` , bağımlılıklarınızın aracılığıyla eklenmesi gerekir `IServiceCollection` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

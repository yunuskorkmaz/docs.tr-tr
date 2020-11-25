---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032724"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır

`Microsoft.Extensions.Caching.SqlServer`Paket, `Microsoft.Data.SqlClient` paket yerine yeni paketini kullanır `System.Data.SqlClient` . Bu değişiklik küçük davranışsal davranış değişikliklerine neden olabilir. Daha fazla bilgi için bkz. [Yeni Microsoft. Data. SqlClient tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.Extensions.Caching.SqlServer`Paket, paketi kullandı `System.Data.SqlClient` .

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.Extensions.Caching.SqlServer` Artık `Microsoft.Data.SqlClient` paketi kullanıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.Data.SqlClient` , ' den oluşturulan yeni bir pakettir `System.Data.SqlClient` . Bu, tüm yeni özellik işinin bundan sonra yapıldığı yerdir.

#### <a name="recommended-action"></a>Önerilen eylem

Müşterilerin, paket tarafından döndürülen türleri kullanmadıkları `Microsoft.Extensions.Caching.SqlServer` ve bunları türlere dönüştürmedikleri müddetçe, bu son değişiklik konusunda endişelenmeleri gerekmez `System.Data.SqlClient` . Örneğin, birisi, `DbConnection` [eski SqlConnection türünde](xref:System.Data.SqlClient.SqlConnection)bir olarak yayınlandıysa, dönüştürmeyi yeni türe dönüştürmeleri gerekir `Microsoft.Data.SqlClient.SqlConnection` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

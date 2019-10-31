---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198593"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır

`Microsoft.Extensions.Caching.SqlServer` paketi `System.Data.SqlClient` paketi yerine yeni `Microsoft.Data.SqlClient` paketini kullanır. Bu değişiklik küçük davranışsal davranış değişikliklerine neden olabilir. Daha fazla bilgi için bkz. [Yeni Microsoft. Data. SqlClient tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.Extensions.Caching.SqlServer` paketi `System.Data.SqlClient` paketini kullandı.

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.Extensions.Caching.SqlServer` artık `Microsoft.Data.SqlClient` paketini kullanıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.Data.SqlClient`, `System.Data.SqlClient` ' den oluşturulan yeni bir pakettir. Bu, tüm yeni özellik işinin bundan sonra yapıldığı yerdir.

#### <a name="recommended-action"></a>Önerilen eylem

Müşterilerin, `Microsoft.Extensions.Caching.SqlServer` paketi tarafından döndürülen türleri kullanmadıkları ve bunları `System.Data.SqlClient` türlerine dönüştürmedikleri müddetçe, bu son değişiklik hakkında kaygılanmaması gerekmez. Örneğin, birisi [eski SqlConnection türüne](xref:System.Data.SqlClient.SqlConnection)bir `DbConnection` dönüştürrsa, yeni `Microsoft.Data.SqlClient.SqlConnection` türüne dönüştürmeyi değiştirmesi gerekir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

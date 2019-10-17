---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393912"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır

@No__t-0 paketi `System.Data.SqlClient` paketi yerine yeni `Microsoft.Data.SqlClient` paketini kullanır. Bu değişiklik küçük davranışsal davranış değişikliklerine neden olabilir. Daha fazla bilgi için bkz. [Yeni Microsoft. Data. SqlClient tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

@No__t-0 paketi `System.Data.SqlClient` paketini kullandı.

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.Extensions.Caching.SqlServer` artık `Microsoft.Data.SqlClient` paketini kullanıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.Data.SqlClient`, `System.Data.SqlClient` ' den oluşturulan yeni bir pakettir. Bu, tüm yeni özellik işinin bundan sonra yapıldığı yerdir.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 paketi tarafından döndürülen türleri kullanmadıkları ve bunları `System.Data.SqlClient` türlerine aktarmadığı müddetçe müşterilerin bu son değişiklik hakkında endişelenmeleri gerekmez. Örneğin, birisi `DbConnection` ' ı [eski SqlConnection türüne](xref:System.Data.SqlClient.SqlConnection)alıyorsa, yeni @no__t 2 türüne dönüştürmeyi değiştirmesi gerekir. 

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

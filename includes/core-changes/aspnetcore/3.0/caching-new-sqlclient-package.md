---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198593"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Önbelleğe alma: Microsoft.Extensions.Caching.SqlServer yeni SqlClient paketi kullanır

Paket, `Microsoft.Extensions.Caching.SqlServer` `System.Data.SqlClient` paket yerine `Microsoft.Data.SqlClient` yeni paketi kullanacaktır. Bu değişiklik hafif davranışsal kırılma değişikliklerine neden olabilir. Daha fazla bilgi için [bkz.](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Paket `Microsoft.Extensions.Caching.SqlServer` `System.Data.SqlClient` paketi kullandı.

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.Extensions.Caching.SqlServer`şimdi `Microsoft.Data.SqlClient` paketi kullanıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`Microsoft.Data.SqlClient`kapalı inşa edilmiş yeni bir `System.Data.SqlClient`pakettir. Bundan sonra tüm yeni özellik çalışmaları burada yapılacak.

#### <a name="recommended-action"></a>Önerilen eylem

`Microsoft.Extensions.Caching.SqlServer` Müşteriler, paket tarafından döndürülen türleri kullanmadıkları ve bunları türe dönüştürmedikleri `System.Data.SqlClient` sürece bu kırılma değişikliği hakkında endişelenmelerine gerek yoktur. Örneğin, birisi [eski SqlConnection türüne](xref:System.Data.SqlClient.SqlConnection)a `DbConnection` atıyorduysa, kalıbı `Microsoft.Data.SqlClient.SqlConnection` yeni türe değiştirmesi gerekir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

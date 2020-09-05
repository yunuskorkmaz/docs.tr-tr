---
ms.openlocfilehash: c27c63e5bbd4a144b9482a0b1cb74250ae78d91c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497504"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Azure SQL veritabanları için bağlantı havuzu engelleme süresi kaldırıldı

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına yönelik bağlantı açık istekleri ( \* . Database.Windows.net, \* . Database.chinacloudapi.cn, \* . database.usgovcloudapi.net, \* . Database.cloudapi.de) için, bağlantı havuzu engelleme süresi kaldırılır ve bağlantı açma hataları önbelleğe alınmaz. Bağlantı açma isteklerini yeniden deneme girişimleri, geçici bağlantı hatalarından hemen sonra gerçekleşir. Bu değişiklik, bağlantı açma denemesinin Azure SQL veritabanları için hemen yeniden denenmeye olanak tanır ve böylece bulut özellikli uygulamaların performansını geliştirir. Diğer tüm bağlantı girişimleri için, bağlantı havuzu engelleme süresi zorlanmaya devam eder.<p/>.NET Framework 4.6.1 ve önceki sürümlerde, bir uygulama bir veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında bağlantı girişimi hızlı bir şekilde yeniden denenemez, çünkü bağlantı havuzu hatayı önbelleğe alır ve 5 saniye ile 1 dakikaya yeniden atar. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantı için sorunlu olur. Bağlantı havuzu engelleme özelliği, uygulamanın, veritabanı kullanılabilir olsa bile ve uygulamanın birkaç saniye içinde işlenmesi gerektiğinden kapsamlı bir süre için veritabanına bağlanamaması anlamına gelir.

#### <a name="suggestion"></a>Öneri

Bu davranış istenmeyen olursa, bağlantı havuzu engelleme süresi <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> .NET Framework 4.6.2 tarafından tanıtılan özellik ayarlanarak yapılandırılabilir. Özelliğinin değeri, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> üç değerden birini ele alan numaralandırmanın bir üyesidir:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Önceki davranış özelliği olarak ayarlanarak geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Common.DbConnection.OpenAsync`
- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->

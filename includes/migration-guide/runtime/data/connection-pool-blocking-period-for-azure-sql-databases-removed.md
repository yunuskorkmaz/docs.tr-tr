---
ms.openlocfilehash: 4a60f4b135d5710ad0cc4900337e2970ffb8dd58
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83435462"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Azure SQL veritabanları için bağlantı havuzu engelleme süresi kaldırıldı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına yönelik bağlantı açık istekleri ( \* . Database.Windows.net, \* . Database.chinacloudapi.cn, \* . database.usgovcloudapi.net, \* . Database.cloudapi.de) için, bağlantı havuzu engelleme süresi kaldırılır ve bağlantı açma hataları önbelleğe alınmaz. Bağlantı açma isteklerini yeniden deneme girişimleri, geçici bağlantı hatalarından hemen sonra gerçekleşir. Bu değişiklik, bağlantı açma denemesinin Azure SQL veritabanları için hemen yeniden denenmeye olanak tanır ve böylece bulut özellikli uygulamaların performansını geliştirir. Diğer tüm bağlantı girişimleri için, bağlantı havuzu engelleme süresi zorlanmaya devam eder.<p/>.NET Framework 4.6.1 ve önceki sürümlerde, bir uygulama bir veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında bağlantı girişimi hızlı bir şekilde yeniden denenemez, çünkü bağlantı havuzu hatayı önbelleğe alır ve 5 saniye ile 1 dakikaya yeniden atar. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantı için sorunlu olur. Bağlantı havuzu engelleme özelliği, uygulamanın, veritabanı kullanılabilir olsa bile ve uygulamanın birkaç saniye içinde işlenmesi gerektiğinden kapsamlı bir süre için veritabanına bağlanamaması anlamına gelir.|
|Öneri|Bu davranış istenmeyen olursa, bağlantı havuzu engelleme süresi <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> .NET Framework 4.6.2 tarafından tanıtılan özellik ayarlanarak yapılandırılabilir. Özelliğinin değeri, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> üç değerden birini ele alan numaralandırmanın bir üyesidir:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Önceki davranış özelliği olarak ayarlanarak geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> .|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

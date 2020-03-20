---
ms.openlocfilehash: 33c262ebe131aade2b32d824395721f098640cf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857539"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Azure SQL veritabanları için bağlantı havuzu engelleme süresi kaldırıldı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına (*.database.windows.net, *.database.chinacloudapi.cn, *.database.usgovcloudapi.net, *.database.cloudapi.de) bağlantı havuzu engelleme süresine bağlantı açık istekleri için kaldırılır ve bağlantı açık hataları önbelleğe alınmaz. Bağlantı açık isteklerini yeniden deneme girişimleri geçici bağlantı hatalarından hemen sonra gerçekleşir. Bu değişiklik, bağlantı açık girişiminin Azure SQL veritabanları için hemen yeniden denenmesine ve böylece bulut özellikli uygulamaların performansını artırmasına olanak tanır. Diğer tüm bağlantı denemeleri için bağlantı havuzu engelleme süresi zorlanmaya devam ediyor.<p/>.NET Framework 4.6.1 ve önceki sürümlerinde, bir uygulama veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında, bağlantı havuzu hatayı önbelleğe aldığından ve 5 saniyeden 1'e yeniden attığından, bağlantı denemesi hızlı bir şekilde yeniden denenemez Dakika. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md)adresine bakın. Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantılar için sorunludur. Bağlantı havuzu engelleme özelliği, veritabanı kullanılabilir olmasına ve uygulamanın birkaç saniye içinde işlemesi gerekmesine rağmen, uygulamanın veritabanına geniş bir süre bağlanamayacağı anlamına gelir.|
|Öneri|Bu davranış istenmiyorsa, bağlantı havuzu engelleme süresi .NET Framework 4.6.2'de tanıtılan <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> özellik ayarlayarak yapılandırılabilir. Özelliğin değeri, üç değerden <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> birini alabilecek numaralandırmanın bir üyesidir:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Önceki davranış <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> özelliği ' ne <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>ayarlayarak geri yüklenebilir.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

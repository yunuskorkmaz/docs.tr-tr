---
ms.openlocfilehash: 33c262ebe131aade2b32d824395721f098640cf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981922"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Azure SQL veritabanları için süre engelleme bağlantı havuzu kaldırıldı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ile başlayarak, bağlantı için bilinen bir Azure SQL veritabanları için açık olan istekleri (*. database.windows.net, *. database.chinacloudapi.cn, *. database.usgovcloudapi.net, *. database.cloudapi.de), bağlantı havuzu engelleme süresi kaldırılmış ve açık bağlantı hataları önbelleğe alınmaz. Bağlantı açık isteklerin yeniden deneme girişimleri hemen sonra geçici bağlantı hataları ortaya çıkar. Bu değişiklik, böylece bulut-etkin uygulama performansını iyileştirme, Azure SQL veritabanları için hemen yeniden denenmesi bağlantı açık denemesi sağlar. Diğer tüm bağlantı girişimleri için bağlantı havuzu engelleme süresi zorlanmaya devam eder.<p/>Uygulama, veritabanına bağlanırken geçici bağlantı hatası karşılaştığında bağlantı havuzu hata önbelleğe alır ve 1 5 saniye boyunca yeniden harekete olduğundan .NET Framework 4.6.1 ve önceki sürümlerle bağlantı denemesi hızlı bir şekilde yeniden denenemez dakika. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Bu sorunlu bağlantılar için genellikle gelen birkaç saniye içinde kurtarıldığı geçici hatalar çoğunlukla başarısız Azure SQL veritabanları, davranıştır. Bağlantı havuzu engelleme özelliği, uygulama veritabanı kapsamlı bir dönem için veritabanının kullanılabilir olduğundan ve uygulamayı birkaç saniye içinde işlemek gerekli olsa bile bağlanamadığını anlamına gelir.|
|Öneri|Bu davranış, istenmeyen ise, bağlantı havuzu engelleme süresi ayarlayarak yapılandırılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> özelliği .NET Framework 4.6.2 sunmuştur. Özelliğinin değeri bir üyesidir <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> numaralandırmadan üç değerden birini alabilir:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>Ayarlayarak önceki davranış geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> özelliğini <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

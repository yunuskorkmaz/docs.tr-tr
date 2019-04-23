---
ms.openlocfilehash: fcaee245e98dfe71beb4042a2664a14b64cf2398
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805286"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection artık SQL Server 1997'den veya VIA bağdaştırıcısı kullanarak veritabanlarına bağlanabilir

|   |   |
|---|---|
|Ayrıntılar|Kullanarak SQL Server veritabanlarına bağlantı [sanal arabirim bağdaştırıcısı (VIA) protokolünü](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229%28v=sql.105%29) artık desteklenmemektedir. Bir SQL Server veritabanına bağlanmak için kullanılan protokol, bağlantı dizesinde görülebilir. VIA bağlantı aracılığıyla içerecek:&lt;servername&gt;. VIA dışındaki bir protokolü aracılığıyla bu uygulamaya SQL'e bağlanma, (tcp: veya np: gibi), sonra hiçbir değişiklik karşılaşıldı. Ayrıca, SQL Server 7 (1997'den) bağlantı artık desteklenmemektedir.|
|Öneri|VIA Protokolü kullanım dışı olduğundan SQL veritabanlarına bağlanmak için alternatif bir protokolü kullanılmalıdır. En yaygın kullanılan protokol, TCP/IP'yi ' dir. TCP/IP bağlanma hakkında daha fazla bilgi için bkz. [veritabanı örneği için TCP/IP protokolünü etkinleştirin](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Veritabanı yalnızca gelen içinde intranet erişilirse, paylaşılan kanallar Protokolü'nü Ağ yavaşsa daha iyi performans sağlayabilir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

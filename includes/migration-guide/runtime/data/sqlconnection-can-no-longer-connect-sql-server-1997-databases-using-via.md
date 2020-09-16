---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606273"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection artık VıA bağdaştırıcısını kullanarak SQL Server 1997 veya veritabanlarına bağlanamaz

#### <a name="details"></a>Ayrıntılar

[Sanal arabirim bağdaştırıcısı (VIA) protokolünü](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) kullanarak SQL Server veritabanlarına bağlantı artık desteklenmemektedir. Bir SQL Server veritabanına bağlanmak için kullanılan protokol bağlantı dizesinde görünür. Bir Ile bağlantı, ile arasında şunu içerir: &lt; ServerName &gt; . Bu uygulama, SQL 'e aracılığıyla (TCP: veya NP: örneğin) dışında bir protokol aracılığıyla bağlanıyorsa, hiçbir bir değişikliğe karşı karşılaşacaktır. Ayrıca, SQL Server 7 (1997) bağlantıları artık desteklenmemektedir.

#### <a name="suggestion"></a>Öneri

VıA Protokolü kullanım dışıdır, bu nedenle SQL veritabanlarına bağlanmak için alternatif bir protokol kullanılmalıdır. Kullanılan en yaygın protokol TCP/IP 'dir. TCP/IP üzerinden bağlanma hakkında daha fazla bilgi için bkz. [bir veritabanı örneği IÇIN TCP/IP protokolünü etkinleştirme](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Veritabanına yalnızca bir intranet içinden erişilirse, ağ yavaşsa paylaşılan kanallar Protokolü daha iyi performans sağlayabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->

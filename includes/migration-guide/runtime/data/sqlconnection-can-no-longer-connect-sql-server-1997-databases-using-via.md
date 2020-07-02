---
ms.openlocfilehash: 241184d61d718fedfea396260e739d2dbc05c305
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620603"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection artık VıA bağdaştırıcısını kullanarak SQL Server 1997 veya veritabanlarına bağlanamaz

#### <a name="details"></a>Ayrıntılar

[Sanal arabirim bağdaştırıcısı (VIA) protokolünü](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) kullanarak SQL Server veritabanlarına bağlantı artık desteklenmemektedir. Bir SQL Server veritabanına bağlanmak için kullanılan protokol bağlantı dizesinde görünür. Bir Ile bağlantı, ile arasında şunu içerir: &lt; ServerName &gt; . Bu uygulama, SQL 'e aracılığıyla (TCP: veya NP: örneğin) dışında bir protokol aracılığıyla bağlanıyorsa, hiçbir bir değişikliğe karşı karşılaşacaktır. Ayrıca, SQL Server 7 (1997) bağlantıları artık desteklenmemektedir.

#### <a name="suggestion"></a>Öneri

VıA Protokolü kullanım dışıdır, bu nedenle SQL veritabanlarına bağlanmak için alternatif bir protokol kullanılmalıdır. Kullanılan en yaygın protokol TCP/IP 'dir. TCP/IP üzerinden bağlanma hakkında daha fazla bilgi için bkz. [bir veritabanı örneği IÇIN TCP/IP protokolünü etkinleştirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)). Veritabanına yalnızca bir intranet içinden erişilirse, ağ yavaşsa paylaşılan kanallar Protokolü daha iyi performans sağlayabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)></li></ul>|

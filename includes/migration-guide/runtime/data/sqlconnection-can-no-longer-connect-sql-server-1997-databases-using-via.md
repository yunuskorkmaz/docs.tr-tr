---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606273"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="e5981-101">SqlConnection artık VıA bağdaştırıcısını kullanarak SQL Server 1997 veya veritabanlarına bağlanamaz</span><span class="sxs-lookup"><span data-stu-id="e5981-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="e5981-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e5981-102">Details</span></span>

<span data-ttu-id="e5981-103">[Sanal arabirim bağdaştırıcısı (VIA) protokolünü](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) kullanarak SQL Server veritabanlarına bağlantı artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="e5981-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="e5981-104">Bir SQL Server veritabanına bağlanmak için kullanılan protokol bağlantı dizesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="e5981-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="e5981-105">Bir Ile bağlantı, ile arasında şunu içerir: &lt; ServerName &gt; .</span><span class="sxs-lookup"><span data-stu-id="e5981-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="e5981-106">Bu uygulama, SQL 'e aracılığıyla (TCP: veya NP: örneğin) dışında bir protokol aracılığıyla bağlanıyorsa, hiçbir bir değişikliğe karşı karşılaşacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5981-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="e5981-107">Ayrıca, SQL Server 7 (1997) bağlantıları artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="e5981-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e5981-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="e5981-108">Suggestion</span></span>

<span data-ttu-id="e5981-109">VıA Protokolü kullanım dışıdır, bu nedenle SQL veritabanlarına bağlanmak için alternatif bir protokol kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5981-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="e5981-110">Kullanılan en yaygın protokol TCP/IP 'dir.</span><span class="sxs-lookup"><span data-stu-id="e5981-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="e5981-111">TCP/IP üzerinden bağlanma hakkında daha fazla bilgi için bkz. [bir veritabanı örneği IÇIN TCP/IP protokolünü etkinleştirme](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e5981-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="e5981-112">Veritabanına yalnızca bir intranet içinden erişilirse, ağ yavaşsa paylaşılan kanallar Protokolü daha iyi performans sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e5981-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="e5981-113">Name</span><span class="sxs-lookup"><span data-stu-id="e5981-113">Name</span></span>    | <span data-ttu-id="e5981-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e5981-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e5981-115">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e5981-115">Scope</span></span>   |<span data-ttu-id="e5981-116">Edge</span><span class="sxs-lookup"><span data-stu-id="e5981-116">Edge</span></span>|
|<span data-ttu-id="e5981-117">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e5981-117">Version</span></span>|<span data-ttu-id="e5981-118">4,5</span><span class="sxs-lookup"><span data-stu-id="e5981-118">4.5</span></span>|
|<span data-ttu-id="e5981-119">Tür</span><span class="sxs-lookup"><span data-stu-id="e5981-119">Type</span></span>|<span data-ttu-id="e5981-120">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="e5981-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e5981-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e5981-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->

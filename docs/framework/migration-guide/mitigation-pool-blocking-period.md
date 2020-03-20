---
title: 'Azaltma: Havuz Engelleme Dönemi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457850"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="68a37-102">Azaltma: Havuz Engelleme Dönemi</span><span class="sxs-lookup"><span data-stu-id="68a37-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="68a37-103">Bağlantı havuzu engelleme süresi, Azure SQL veritabanlarına bağlantılar için kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="68a37-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="68a37-104">Ek açıklama</span><span class="sxs-lookup"><span data-stu-id="68a37-104">Additional description</span></span>  
 <span data-ttu-id="68a37-105">.NET Framework 4.6.1 ve önceki sürümlerinde, bir uygulama veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında, bağlantı havuzu hatayı önbelleğe aldığından ve 5 saniye ile 1 dakika arasında yeniden attığından, bağlantı denemesi hızlı bir şekilde yeniden denenemez. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md)adresine bakın.</span><span class="sxs-lookup"><span data-stu-id="68a37-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="68a37-106">Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantılar için sorunludur.</span><span class="sxs-lookup"><span data-stu-id="68a37-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="68a37-107">Bağlantı havuzu engelleme özelliği, veritabanı kullanılabilir olsa bile uygulamanın geniş bir süre veritabanına bağlanamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="68a37-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="68a37-108">Bu davranış, Azure SQL veritabanlarına bağlanan ve birkaç saniye içinde işlenmesi gereken web uygulamaları için özellikle sorunludur.</span><span class="sxs-lookup"><span data-stu-id="68a37-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="68a37-109">.NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına (\*.database.windows.net, \*.database.chinacloudapi.cn, .database.usgovcloudapi.net, \* \*.database.cloudapi.de) bağlantı açık istekleri için bağlantı açık hataları önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="68a37-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="68a37-110">Diğer tüm bağlantı denemeleri için bağlantı havuzu engelleme süresi zorlanmaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="68a37-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="68a37-111">Etki</span><span class="sxs-lookup"><span data-stu-id="68a37-111">Impact</span></span>  
 <span data-ttu-id="68a37-112">Bu değişiklik, bağlantı açık girişiminin Azure SQL veritabanları için hemen yeniden denenmesine ve böylece bulut özellikli uygulamaların performansını artırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68a37-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="68a37-113">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="68a37-113">Mitigation</span></span>  
 <span data-ttu-id="68a37-114">Bu değişiklikten olumsuz etkilenen uygulamalar için bağlantı havuzu engelleme süresi yeni <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> özellik ayarlayarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="68a37-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="68a37-115">Özelliğin değeri, üç değerden <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> birini alabilecek numaralandırmanın bir üyesidir:</span><span class="sxs-lookup"><span data-stu-id="68a37-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="68a37-116">Önceki davranış <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği ' ne <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>ayarlayarak geri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="68a37-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a37-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68a37-117">See also</span></span>

- [<span data-ttu-id="68a37-118">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="68a37-118">Application compatibility</span></span>](application-compatibility.md)

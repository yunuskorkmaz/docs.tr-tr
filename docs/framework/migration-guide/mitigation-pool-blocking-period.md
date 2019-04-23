---
title: 'Azaltma: Havuz engelleme süresi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97650099aed0be7e1983f759cd0f38fc568f857
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082769"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="b8b6f-102">Azaltma: Havuz engelleme süresi</span><span class="sxs-lookup"><span data-stu-id="b8b6f-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="b8b6f-103">Azure SQL veritabanlarına bağlantı için süre engelleme bağlantı havuzu kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="b8b6f-104">Ek açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b6f-104">Additional description</span></span>  
 <span data-ttu-id="b8b6f-105">İçinde [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümlerinde, bir uygulama, bir veritabanına bağlanırken geçici bağlantı hatası karşılaşırsa, çünkü bağlantı havuzu hata önbelleğe alır ve 1 dakika için 5 saniye boyunca yeniden harekete bağlantı denemesi hızlı bir şekilde yeniden denenemez. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="b8b6f-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="b8b6f-106">Bu sorunlu bağlantılar için genellikle gelen birkaç saniye içinde kurtarıldığı geçici hatalar çoğunlukla başarısız Azure SQL veritabanları, davranıştır.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="b8b6f-107">Bağlantı havuzu engelleme özelliği veritabanı kullanılabilir olsa bile, uygulama kapsamlı bir dönem için veritabanına bağlanamıyor anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="b8b6f-108">Bu, Azure SQL veritabanlarına bağlanmak ve birkaç saniye içinde işlemek gereken web apps için özellikle sorunlu, davranıştır.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="b8b6f-109">İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]bağlantıyı açmak için bilinen bir Azure SQL veritabanlarına istekleri (\*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Bağlantı açık hataları önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="b8b6f-110">Diğer tüm bağlantı girişimleri için bağlantı havuzu engelleme süresi zorlanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b8b6f-111">Etki</span><span class="sxs-lookup"><span data-stu-id="b8b6f-111">Impact</span></span>  
 <span data-ttu-id="b8b6f-112">Bu değişiklik, böylece bulut özellikli uygulamalar performansını iyileştirme, Azure SQL veritabanları için hemen yeniden denenmesi bağlantı açık denemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b8b6f-113">Azaltma</span><span class="sxs-lookup"><span data-stu-id="b8b6f-113">Mitigation</span></span>  
 <span data-ttu-id="b8b6f-114">Yeni ayarlayarak, olumsuz bu değişiklikten etkilenen uygulamaları için bağlantı havuzu engelleme süresi yapılandırılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="b8b6f-115">Özelliğinin değeri bir üyesidir <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırmadan üç değerden birini alabilir:</span><span class="sxs-lookup"><span data-stu-id="b8b6f-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="b8b6f-116">Ayarlayarak önceki davranış geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliğini <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b6f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b6f-117">See also</span></span>

- [<span data-ttu-id="b8b6f-118">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="b8b6f-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)

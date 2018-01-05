---
title: "Azaltma: Havuzu engelleme süresi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42eaddeb2714a8c294f45d24eb7e6d9cf216fecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="e6c38-102">Azaltma: Havuzu engelleme süresi</span><span class="sxs-lookup"><span data-stu-id="e6c38-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="e6c38-103">Dönem engelleme bağlantı havuzu bağlantılar Azure SQL veritabanları için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e6c38-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="e6c38-104">Ek açıklama</span><span class="sxs-lookup"><span data-stu-id="e6c38-104">Additional description</span></span>  
 <span data-ttu-id="e6c38-105">İçinde [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki sürümlerinde, bir uygulama, bir veritabanına bağlanırken bir geçici bağlantı hatası karşılaştığında, çünkü bağlantı havuzu hata önbelleğe alır ve bunu 1 dak 5 saniye için yeniden oluşturur, hızlı bir şekilde, bağlantı girişimi denenemiyor. Daha fazla bilgi için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="e6c38-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="e6c38-106">Bu bağlantılar genellikle genellikle gelen birkaç saniye içinde kurtarılan geçici hataları ile başarısız Azure SQL veritabanları için sorunlu davranıştır.</span><span class="sxs-lookup"><span data-stu-id="e6c38-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="e6c38-107">Veritabanı kullanılabilir olsa bile bağlantı havuzu engelleme özelliği, uygulama kapsamlı bir dönem için veritabanına bağlanılamıyor anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6c38-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="e6c38-108">Bu davranış, Azure SQL veritabanlarına bağlanmak ve, birkaç saniye içinde işlemek gereken web uygulamaları için özellikle sorunlu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6c38-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="e6c38-109">İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bağlantıyı açmak için bilinen Azure SQL veritabanları için istekleri (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Bağlantı açık hatalarını önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="e6c38-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="e6c38-110">Diğer tüm bağlantı girişimleri için bağlantı havuzunu engelleme süresi zorlanacak devam eder.</span><span class="sxs-lookup"><span data-stu-id="e6c38-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e6c38-111">Etki</span><span class="sxs-lookup"><span data-stu-id="e6c38-111">Impact</span></span>  
 <span data-ttu-id="e6c38-112">Bu değişiklik, böylece bulut özellikli uygulamalar performansını iyileştirme Azure SQL veritabanları için hemen denenmesi bağlantı açık denemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6c38-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e6c38-113">Azaltma</span><span class="sxs-lookup"><span data-stu-id="e6c38-113">Mitigation</span></span>  
 <span data-ttu-id="e6c38-114">Yeni ayarlayarak bağlantı havuzu engelleme süresi olumsuz bu değişiklikten etkilenen uygulamalar için yapılandırılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e6c38-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property.</span></span>  <span data-ttu-id="e6c38-115">Özelliğinin değeri bir üyesidir <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırması üç değerden birini alabilir:</span><span class="sxs-lookup"><span data-stu-id="e6c38-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 <span data-ttu-id="e6c38-116">Önceki davranış ayarlayarak geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliğine `PoolBlockingPeriod.AlwaysBlock`.</span><span class="sxs-lookup"><span data-stu-id="e6c38-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to `PoolBlockingPeriod.AlwaysBlock`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c38-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6c38-117">See Also</span></span>  
 [<span data-ttu-id="e6c38-118">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e6c38-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)

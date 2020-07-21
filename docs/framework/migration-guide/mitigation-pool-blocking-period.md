---
title: 'Risk azaltma: havuz engelleme süresi'
description: Azure SQL veritabanlarına bağlantılar için, bağlantı havuzu engelleme döneminin kaldırılmasının neden olduğu sorunları nasıl azaltacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: be60fe87952697d964571176743a4e6f839c4894
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475417"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="91b91-103">Risk azaltma: havuz engelleme süresi</span><span class="sxs-lookup"><span data-stu-id="91b91-103">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="91b91-104">Bağlantı havuzu engelleme süresi Azure SQL veritabanlarına bağlantılar için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="91b91-104">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="91b91-105">Ek açıklama</span><span class="sxs-lookup"><span data-stu-id="91b91-105">Additional description</span></span>  
 <span data-ttu-id="91b91-106">.NET Framework 4.6.1 ve önceki sürümlerde, bir uygulama bir veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında bağlantı girişimi hızlı bir şekilde yeniden denenemez, çünkü bağlantı havuzu hatayı önbelleğe alır ve 5 saniye ile 1 dak yeniden oluşturur. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="91b91-106">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="91b91-107">Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantı için sorunlu olur.</span><span class="sxs-lookup"><span data-stu-id="91b91-107">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="91b91-108">Bağlantı havuzu engelleme özelliği, uygulamanın veritabanı kullanılabilir olsa bile kapsamlı bir süre için veritabanına bağlanamamasıdır.</span><span class="sxs-lookup"><span data-stu-id="91b91-108">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="91b91-109">Bu davranış, Azure SQL veritabanlarına bağlanan ve birkaç saniye içinde işlenmesi gereken Web uygulamaları için özellikle sorunlu olur.</span><span class="sxs-lookup"><span data-stu-id="91b91-109">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="91b91-110">.NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına yönelik bağlantı açık istekleri (\*. database.windows.net, \* . Database.chinacloudapi.cn, \* . Database.usgovcloudapi.net, \* . Database.cloudapi.de) için bağlantı açma hataları önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="91b91-110">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="91b91-111">Diğer tüm bağlantı girişimleri için, bağlantı havuzu engelleme süresi zorlanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="91b91-111">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="91b91-112">Etki</span><span class="sxs-lookup"><span data-stu-id="91b91-112">Impact</span></span>  
 <span data-ttu-id="91b91-113">Bu değişiklik, bağlantı açma denemesinin Azure SQL veritabanları için hemen yeniden denenmeye olanak tanır ve böylece bulut özellikli uygulamaların performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="91b91-113">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="91b91-114">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="91b91-114">Mitigation</span></span>  
 <span data-ttu-id="91b91-115">Bu değişiklikten olumsuz etkilenen uygulamalar için, bağlantı havuzu engelleme süresi yeni özellik ayarlanarak yapılandırılabilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="91b91-115">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="91b91-116">Özelliğinin değeri, <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> üç değerden birini ele alan numaralandırmanın bir üyesidir:</span><span class="sxs-lookup"><span data-stu-id="91b91-116">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="91b91-117">Önceki davranış özelliği olarak ayarlanarak geri yüklenebilir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="91b91-117">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b91-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91b91-118">See also</span></span>

- [<span data-ttu-id="91b91-119">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="91b91-119">Application compatibility</span></span>](application-compatibility.md)

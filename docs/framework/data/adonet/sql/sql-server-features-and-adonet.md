---
title: SQL Server Özellikleri ve ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 2839529b-a79b-4450-be5d-07a98dbc7a0f
ms.openlocfilehash: 743e0eb9761cdc58018aab8aaed50a99b197116c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552628"
---
# <a name="sql-server-features-and-adonet"></a><span data-ttu-id="e6b53-102">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6b53-102">SQL Server Features and ADO.NET</span></span>
<span data-ttu-id="e6b53-103">Bu bölümdeki konularda, ADO.NET kullanarak veritabanı uygulamaları geliştirmeye hedeflenmiş SQL Server özellikler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6b53-103">The topics in this section discuss features in SQL Server that are targeted at developing database applications using ADO.NET.</span></span>  
  
 <span data-ttu-id="e6b53-104">Daha fazla bilgi için, aşağıdaki tabloda listelendiği gibi, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online 'a bakın.</span><span class="sxs-lookup"><span data-stu-id="e6b53-104">For more information, see SQL Server Books Online for the version of SQL Server you are using, as listed in the following table.</span></span>  
  
 <span data-ttu-id="e6b53-105">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="e6b53-105">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="e6b53-106">[Geliştirme (veritabanı altyapısı)](/previous-versions/sql/sql-server-2008/bb500155(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="e6b53-106">[Development (Database Engine)](/previous-versions/sql/sql-server-2008/bb500155(v=sql.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6b53-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e6b53-107">In This Section</span></span>  
 [<span data-ttu-id="e6b53-108">SQL Server (ADO.NET) Numaralandırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e6b53-108">Enumerating Instances of SQL Server (ADO.NET)</span></span>](enumerating-instances-of-sql-server.md)  
 <span data-ttu-id="e6b53-109">SQL Server etkin örneklerinin nasıl numaralandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-109">Describes how to enumerate active instances of SQL Server.</span></span>  
  
 [<span data-ttu-id="e6b53-110">SQL Server için Sağlayıcı İstatistikleri</span><span class="sxs-lookup"><span data-stu-id="e6b53-110">Provider Statistics for SQL Server</span></span>](provider-statistics-for-sql-server.md)  
 <span data-ttu-id="e6b53-111">SQL Server çalışma zamanı istatistiklerini alma desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-111">Describes support for obtaining SQL Server run-time statistics.</span></span>  
  
 [<span data-ttu-id="e6b53-112">SQL Server Express Kullanıcı Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e6b53-112">SQL Server Express User Instances</span></span>](sql-server-express-user-instances.md)  
 <span data-ttu-id="e6b53-113">SQL Server Express Kullanıcı örnekleri için desteği açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-113">Describes support for SQL Server Express user instances.</span></span>  
  
 [<span data-ttu-id="e6b53-114">SQL Server’da Veritabanı Yansıtması</span><span class="sxs-lookup"><span data-stu-id="e6b53-114">Database Mirroring in SQL Server</span></span>](database-mirroring-in-sql-server.md)  
 <span data-ttu-id="e6b53-115">Veritabanı yansıtma işlevini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-115">Describes database mirroring functionality.</span></span>  
  
 [<span data-ttu-id="e6b53-116">SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="e6b53-116">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)  
 <span data-ttu-id="e6b53-117">SQL Server, bir ortak dil çalışma zamanı (CLR) veritabanı nesnesi içinden, verilerin nasıl erişilebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-117">Describes how data can be accessed from within a common language runtime (CLR) database object in SQL Server.</span></span>  
  
 [<span data-ttu-id="e6b53-118">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="e6b53-118">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)  
 <span data-ttu-id="e6b53-119">.NET Framework uygulamaların veri değiştirildiğinde SQL Server nasıl bildirim isteyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-119">Describes how .NET Framework applications can request notification from SQL Server when data has changed.</span></span>  
  
 [<span data-ttu-id="e6b53-120">SQL Server'da Anlık Görüntü Yalıtımı</span><span class="sxs-lookup"><span data-stu-id="e6b53-120">Snapshot Isolation in SQL Server</span></span>](snapshot-isolation-in-sql-server.md)  
 <span data-ttu-id="e6b53-121">İşlemsel uygulamalarda engellemeyi azaltmak için tasarlanan bir satır sürümü oluşturma mekanizması olan anlık görüntü yalıtımı desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-121">Describes support for snapshot isolation, a row versioning mechanism designed to reduce blocking in transactional applications.</span></span>  
  
 [<span data-ttu-id="e6b53-122">Yüksek Kullanılabilirlik, Olağanüstü Durum Kurtarma için SqlClient Desteği</span><span class="sxs-lookup"><span data-stu-id="e6b53-122">SqlClient Support for High Availability, Disaster Recovery</span></span>](sqlclient-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="e6b53-123">Yüksek kullanılabilirlik, olağanüstü durum kurtarma (AlwaysOn) kullanılabilirlik grupları için SqlClient desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-123">Describes SqlClient support for high-availability, disaster recovery (AlwaysOn) availability groups.</span></span>  
  
 [<span data-ttu-id="e6b53-124">Yerel Veritabanı için SqlClient Desteği</span><span class="sxs-lookup"><span data-stu-id="e6b53-124">SqlClient Support for LocalDB</span></span>](sqlclient-support-for-localdb.md)  
 <span data-ttu-id="e6b53-125">LocalDB veritabanları için SqlClient desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6b53-125">Describes SqlClient support for LocalDB databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b53-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b53-126">See also</span></span>

- [<span data-ttu-id="e6b53-127">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="e6b53-127">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="e6b53-128">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e6b53-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="e6b53-129">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e6b53-129">LINQ to SQL</span></span>](./linq/index.md)
- [<span data-ttu-id="e6b53-130">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6b53-130">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="e6b53-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e6b53-131">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
title: SQL Server'da Sorgu Bildirimleri
description: SQL Server veritabanında veri değiştirildiğinde uygulamalara bildirim almak için sorgu bildirimlerini nasıl kullanacağınızı öğrenin, örneğin, uygulama ekranları yenilemek için.
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 43b496db74f7e6fc9bc9f17d946bf34398b32312
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543991"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="f8deb-103">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="f8deb-103">Query Notifications in SQL Server</span></span>
<span data-ttu-id="f8deb-104">Hizmet Aracısı altyapısına inşa edildiğinde sorgu bildirimleri, veriler değiştiğinde uygulamalara bildirim gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8deb-104">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="f8deb-105">Bu özellik özellikle bir Web uygulaması gibi bir veritabanından bilgi önbelleği sağlayan ve kaynak veriler değiştirildiğinde bildirilmesi gereken uygulamalar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8deb-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="f8deb-106">ADO.NET kullanarak sorgu bildirimleri uygulayabileceğiniz üç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="f8deb-106">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="f8deb-107">Düşük düzey uygulama, `SqlNotificationRequest` sunucu tarafı işlevselliğini kullanıma sunan sınıf tarafından sağlanır ve bir komut, bildirim isteğiyle birlikte yürütmelerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f8deb-107">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="f8deb-108">Üst düzey uygulama, `SqlDependency` kaynak uygulama ve SQL Server arasında yüksek düzeyde bir bildirim işlevselliği sağlayan sınıfı tarafından sağlanır ve bu, sunucudaki değişiklikleri algılamak için bir bağımlılık kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8deb-108">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="f8deb-109">Çoğu durumda bu, SQL Server için .NET Framework Veri Sağlayıcısı kullanarak yönetilen istemci uygulamaları tarafından SQL Server bildirim yeteneğinin faydalanacak en basit ve en etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="f8deb-109">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="f8deb-110">Ayrıca, ASP.NET 2,0 veya üzeri kullanılarak oluşturulan Web uygulamaları `SqlCacheDependency` yardımcı sınıfları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-110">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="f8deb-111">Sorgu bildirimleri, temel verilerdeki değişikliklere yanıt olarak, ekranları veya önbellekleri yenilemesi gereken uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8deb-111">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="f8deb-112">Microsoft SQL Server, .NET Framework uygulamaların SQL Server bir komut göndermesini ve aynı komutun yürütülmesi, başlangıçta alınanlardan farklı sonuç kümeleri üretmesi durumunda bildirim istemesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-112">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="f8deb-113">Sunucuda oluşturulan bildirimler daha sonra işlenmek üzere kuyruklarla gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-113">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="f8deb-114">SELECT ve EXECUTE deyimlerine yönelik bildirimler ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8deb-114">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="f8deb-115">EXECUTE ifadesini kullanırken, SQL Server EXECUTE ifadesinin kendisi yerine yürütülen komut için bir bildirim kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f8deb-115">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="f8deb-116">Komutun, SELECT ifadesiyle ilgili gereksinimleri ve sınırlamaları karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-116">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="f8deb-117">Bildirimi kaydeden bir komut birden fazla ifade içeriyorsa, veritabanı altyapısı toplu işteki her bir bildirim için bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8deb-117">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="f8deb-118">Veriler değiştiğinde güvenilir alt-ikinci bildirimlere ihtiyacınız olan bir uygulama geliştiriyorsanız, **etkili bir sorgu bildirimleri stratejisi planlama** ve [bildirim planlaması](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) makalesinde **sorgu bildirimlerinin alternatiflerini** planlama başlıklı bölümleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="f8deb-118">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) article.</span></span> <span data-ttu-id="f8deb-119">Sorgu bildirimleri ve SQL Server Hizmet Aracısı hakkında daha fazla bilgi için, SQL Server belgelerindeki makalelere yönelik aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="f8deb-119">For more information about Query Notifications and SQL Server Service Broker, see the following links to articles in the SQL Server documentation.</span></span>  
  
 <span data-ttu-id="f8deb-120">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="f8deb-120">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="f8deb-121">[Sorgu bildirimlerini kullanma](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="f8deb-121">[Using Query Notifications](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="f8deb-122">[Bildirim için sorgu oluşturma](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="f8deb-122">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="f8deb-123">[Geliştirme (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="f8deb-123">[Development (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="f8deb-124">[Hizmet Aracısı geliştirici bilgi merkezi](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="f8deb-124">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="f8deb-125">[Geliştirici Kılavuzu (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="f8deb-125">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8deb-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f8deb-126">In This Section</span></span>  
 [<span data-ttu-id="f8deb-127">Sorgu Bildirimlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f8deb-127">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="f8deb-128">' Nin etkinleştirilmesi ve kullanılması ile ilgili gereksinimler dahil olmak üzere sorgu bildirimlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8deb-128">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="f8deb-129">Bir ASP.NET Uygulamasında SqlDependency</span><span class="sxs-lookup"><span data-stu-id="f8deb-129">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="f8deb-130">ASP.NET uygulamasından sorgu bildirimlerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-130">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="f8deb-131">SqlDependency ile Değişiklikleri Algılama</span><span class="sxs-lookup"><span data-stu-id="f8deb-131">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="f8deb-132">Sorgu sonuçlarının başlangıçta alınanlardan farklı olacağını nasıl algılayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-132">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="f8deb-133">Bir SqlNotificationRequest ile SqlCommand Yürütme</span><span class="sxs-lookup"><span data-stu-id="f8deb-133">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="f8deb-134">Bir <xref:System.Data.SqlClient.SqlCommand> nesneyi sorgu bildirimiyle çalışacak şekilde yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8deb-134">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f8deb-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f8deb-135">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="f8deb-136"><xref:System.Data.Sql.SqlNotificationRequest>Sınıfını ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8deb-136">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="f8deb-137"><xref:System.Data.SqlClient.SqlDependency>Sınıfını ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8deb-137">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="f8deb-138"><xref:System.Web.Caching.SqlCacheDependency>Sınıfını ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8deb-138">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8deb-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8deb-139">See also</span></span>

- [<span data-ttu-id="f8deb-140">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8deb-140">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="f8deb-141">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8deb-141">ADO.NET Overview</span></span>](../ado-net-overview.md)

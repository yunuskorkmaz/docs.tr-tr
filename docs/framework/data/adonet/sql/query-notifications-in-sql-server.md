---
title: SQL Server'da sorgu bildirimleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 854407d2e6d1341d5917cc78664c1f653e55fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="014bd-102">SQL Server'da sorgu bildirimleri</span><span class="sxs-lookup"><span data-stu-id="014bd-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="014bd-103">Hizmet Aracısı altyapı inşa edilen sorgu bildirimleri veriler değiştiğinde bildirim almak uygulamaların olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="014bd-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="014bd-104">Bu özellik, bilgileri bir veritabanından, bir Web uygulaması gibi bir önbellekte sağlamak ve veri kaynağını değiştiğinde bildirim almak gereken uygulamalar için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="014bd-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="014bd-105">ADO.NET kullanarak sorgu bildirimleri uygulayabilirsiniz üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="014bd-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1.  <span data-ttu-id="014bd-106">Alt düzey uygulama tarafından sağlanan `SqlNotificationRequest` sunucu tarafı işlevselliği, size bir bildirim isteği ile komut yürütme etkinleştirme gösteren sınıf.</span><span class="sxs-lookup"><span data-stu-id="014bd-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2.  <span data-ttu-id="014bd-107">Üst düzey uygulama tarafından sağlanan `SqlDependency` kaynak uygulama ve SQL Server, bağımlılık değişiklikleri algılamak için kullanmak üzere etkinleştirme arasında bildirim işlevinin üst düzey bir Özet sağlar sınıftır sınıfı Sunucu.</span><span class="sxs-lookup"><span data-stu-id="014bd-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="014bd-108">Çoğu durumda, SQL Server için .NET Framework veri sağlayıcısı kullanarak yönetilen istemci uygulamalar tarafından SQL Server bildirimleri yeteneğinden yararlanabilir basit ve en etkili yolu budur.</span><span class="sxs-lookup"><span data-stu-id="014bd-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3.  <span data-ttu-id="014bd-109">Ayrıca, Web uygulamaları ASP.NET 2.0 kullanılarak oluşturulmuş ya da daha sonra kullanabileceğiniz `SqlCacheDependency` yardımcı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="014bd-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="014bd-110">Sorgu bildirimleri yenilemek için gereken uygulamalar için kullanılan görüntüler veya yanıt temel alınan verilerde yapılan değişiklikler olarak önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="014bd-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="014bd-111">Microsoft SQL Server, SQL Server ve aynı komutu çalıştırıldığında istek bildirim komutuna başlangıçta alınan olanlardan farklı sonuç kümesi oluşturur göndermek .NET Framework uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="014bd-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="014bd-112">Sunucuda oluşturulan bildirimleri daha sonra işlenmek üzere kuyruklar üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="014bd-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="014bd-113">Seçim için bildirimleri ve ÇALIŞTIRMA deyimleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="014bd-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="014bd-114">Bir EXECUTE deyimi kullanılırken, SQL Server EXECUTE deyimi kendisi yerine yürütülen komut bir bildirime kaydolur.</span><span class="sxs-lookup"><span data-stu-id="014bd-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="014bd-115">Komut bir SELECT deyimi için kısıtlamaları ve gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="014bd-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="014bd-116">Birden fazla deyim bir bildirim kaydeden bir komut içerir, veritabanı altyapısı her deyim için bir bildirim toplu işlemde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="014bd-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="014bd-117">Veriler değiştiğinde güvenilir saniyeden bildirimleri ihtiyaç duyacağınız bir uygulama geliştiriyorsanız, bölümleri gözden **verimli bir sorgu bildirimleri stratejisi planlama** ve **sorgu alternatifleri Bildirimleri** içinde [bildirimleri için planlama](http://go.microsoft.com/fwlink/?LinkId=211984) SQL Server Books Online konusu.</span><span class="sxs-lookup"><span data-stu-id="014bd-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](http://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="014bd-118">Sorgu bildirimleri ve SQL Server hizmet Aracısı hakkında daha fazla bilgi için SQL Server Books Online'da konular için aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="014bd-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="014bd-119">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="014bd-119">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="014bd-120">Sorgu bildirimleri kullanma</span><span class="sxs-lookup"><span data-stu-id="014bd-120">Using Query Notifications</span></span>](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [<span data-ttu-id="014bd-121">Bildirim için sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="014bd-121">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="014bd-122">Hizmet Aracısı</span><span class="sxs-lookup"><span data-stu-id="014bd-122">Service Broker</span></span>](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [<span data-ttu-id="014bd-123">Hizmet aracısı geliştirici Bilgi Merkezi</span><span class="sxs-lookup"><span data-stu-id="014bd-123">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="014bd-124">Geliştirme (hizmet Aracısı)</span><span class="sxs-lookup"><span data-stu-id="014bd-124">Development (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a><span data-ttu-id="014bd-125">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="014bd-125">In This Section</span></span>  
 [<span data-ttu-id="014bd-126">Sorgu bildirimleri etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="014bd-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="014bd-127">Etkinleştirme ve bunları kullanarak gereksinimlerini de dahil olmak üzere sorgu bildirimlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="014bd-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="014bd-128">Bir ASP.NET uygulamasında SqlDependency</span><span class="sxs-lookup"><span data-stu-id="014bd-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="014bd-129">Bir ASP.NET uygulamasında sorgu bildirimlerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="014bd-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="014bd-130">SqlDependency ile değişiklikleri algılama</span><span class="sxs-lookup"><span data-stu-id="014bd-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="014bd-131">Sorgu sonuçları başlangıçta alınan olanlardan farklı algılayabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="014bd-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="014bd-132">Bir SqlNotificationRequest ile SqlCommand yürütme</span><span class="sxs-lookup"><span data-stu-id="014bd-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="014bd-133">Yapılandırma gösteren bir <xref:System.Data.SqlClient.SqlCommand> sorgu bildirimi ile çalışmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="014bd-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="014bd-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="014bd-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="014bd-135">Açıklar <xref:System.Data.Sql.SqlNotificationRequest> sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="014bd-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="014bd-136">Açıklar <xref:System.Data.SqlClient.SqlDependency> sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="014bd-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="014bd-137">Açıklar <xref:System.Web.Caching.SqlCacheDependency> sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="014bd-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014bd-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="014bd-138">See Also</span></span>  
 [<span data-ttu-id="014bd-139">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="014bd-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="014bd-140">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="014bd-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

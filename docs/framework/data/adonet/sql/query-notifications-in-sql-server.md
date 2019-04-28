---
title: SQL Server'da Sorgu Bildirimleri
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: e31a733635cf56a9c5e539dfb1d71d7d7037175a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645987"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="0ff5e-102">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="0ff5e-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="0ff5e-103">Hizmet Aracısı altyapı inşa edilen uygulamalar, veriler değiştiğinde bildirim almak sorgu bildirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="0ff5e-104">Bu özellik, bilgileri bir veritabanından, bir Web uygulaması gibi bir önbellek sağlamanız ve kaynak veriler değiştiğinde bildirim almak gereken uygulamalar için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="0ff5e-105">ADO.NET kullanarak sorgu bildirimleri uygulamak üç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="0ff5e-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="0ff5e-106">Alt düzey uygulama tarafından sağlanan `SqlNotificationRequest` komut bir bildirim isteği ile yürütme olanak sağlayan, sunucu tarafı işlevler gösteren sınıf.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="0ff5e-107">Üst düzey uygulama tarafından sağlanan `SqlDependency` üst düzey bir soyutlama bildirim işlevselliği arasında kaynak uygulaması ve SQL Server, değişiklikleri algılamak için bir bağımlılık kullanmanıza olanak sağlayan bir sınıf olan sınıf Sunucu.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="0ff5e-108">Çoğu durumda, bu SQL Server için .NET Framework veri sağlayıcısı kullanarak yönetilen istemci uygulamalar tarafından SQL Server bildirim özelliği yararlanmak için basit ve en etkili yoludur.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="0ff5e-109">Ayrıca, Web uygulamaları ASP.NET 2.0 kullanılarak oluşturulan veya daha sonra kullanabileceğiniz `SqlCacheDependency` yardımcı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="0ff5e-110">Sorgu bildirimleri yenilemek için gerek duyan uygulamalar için kullanılan görüntüler veya yanıt temel alınan verilerde yapılan değişiklikler olarak önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="0ff5e-111">Microsoft SQL Server, SQL Server ve aynı komutu çalıştırıldığında istek bildirimi komut başlangıçta alınan olanlardan farklı sonuç kümesi oluşturur göndermek .NET Framework uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="0ff5e-112">Sunucuda oluşturulan tüm bildirimleri, daha sonra işlenmek üzere kuyruklar üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="0ff5e-113">Bildirimler için seçin ve ÇALIŞTIRMA deyimleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="0ff5e-114">EXECUTE deyimi kullanılırken, SQL Server EXECUTE deyimi kendisi yerine yürütülen komut bir bildirime kaydolur.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="0ff5e-115">Komutu, bir SELECT deyimi sınırlamaları ve gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="0ff5e-116">Bir bildirim kaydeden bir komutu birden fazla deyim içeren veritabanı altyapısı toplu işlemde her deyim için bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="0ff5e-117">Veriler değiştiğinde, güvenilir saniyenin bildirimleri gereken bir uygulama geliştiriyorsanız, bölümleri gözden geçirin. **verimli bir sorgu bildirimleri stratejisi planlama** ve **sorgu alternatifleri Bildirimleri** içinde [bildirimleri için planlama](https://go.microsoft.com/fwlink/?LinkId=211984) konu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](https://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="0ff5e-118">Sorgu bildirimleri ve SQL Server hizmet Aracısı hakkında daha fazla bilgi için aşağıdaki konulara bağlantılar da SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="0ff5e-119">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="0ff5e-119">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="0ff5e-120">[Sorgu bildirimleri kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="0ff5e-120">[Using Query Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="0ff5e-121">[Bildirim için sorgu oluşturma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="0ff5e-121">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="0ff5e-122">[Geliştirme (hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="0ff5e-122">[Development (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="0ff5e-123">[Service Broker Geliştirici Bilgi Merkezi](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="0ff5e-123">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="0ff5e-124">[Geliştirici Kılavuzu (hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="0ff5e-124">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ff5e-125">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0ff5e-125">In This Section</span></span>  
 [<span data-ttu-id="0ff5e-126">Sorgu Bildirimlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0ff5e-126">Enabling Query Notifications</span></span>](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 <span data-ttu-id="0ff5e-127">Sorgu bildirimleri, etkinleştirmek ve bunları kullanmak için gereksinimleri dahil olmak üzere kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="0ff5e-128">Bir ASP.NET Uygulamasında SqlDependency</span><span class="sxs-lookup"><span data-stu-id="0ff5e-128">SqlDependency in an ASP.NET Application</span></span>](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="0ff5e-129">Sorgu bildirimleri bir ASP.NET uygulamasından nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="0ff5e-130">SqlDependency ile Değişiklikleri Algılama</span><span class="sxs-lookup"><span data-stu-id="0ff5e-130">Detecting Changes with SqlDependency</span></span>](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="0ff5e-131">Sorgu sonuçları başlangıçta alınan olanlardan farklı Algıla gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="0ff5e-132">Bir SqlNotificationRequest ile SqlCommand Yürütme</span><span class="sxs-lookup"><span data-stu-id="0ff5e-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="0ff5e-133">Yapılandırma gösteren bir <xref:System.Data.SqlClient.SqlCommand> bir sorgu bildirimi ile çalışmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0ff5e-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0ff5e-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="0ff5e-135">Açıklar <xref:System.Data.Sql.SqlNotificationRequest> sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="0ff5e-136">Açıklar <xref:System.Data.SqlClient.SqlDependency> sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="0ff5e-137">Açıklar <xref:System.Web.Caching.SqlCacheDependency> sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff5e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff5e-138">See also</span></span>

- [<span data-ttu-id="0ff5e-139">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0ff5e-139">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="0ff5e-140">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0ff5e-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

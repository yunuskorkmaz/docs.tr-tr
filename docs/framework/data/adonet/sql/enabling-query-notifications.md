---
title: Sorgu Bildirimlerini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 693e67b4d369eb69b8e0a9dded6decb2d3928459
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554885"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="a2da5-102">Sorgu Bildirimlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a2da5-102">Enabling Query Notifications</span></span>
<span data-ttu-id="a2da5-103">Sorgu bildirimlerini kullanan uygulamaların ortak bir gereksinim kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="a2da5-104">Veri kaynağınız SQL sorgu bildirimlerini destekleyecek şekilde doğru yapılandırılmış olmalıdır ve Kullanıcı doğru istemci tarafı ve sunucu tarafı izinlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="a2da5-105">Sorgu bildirimlerini kullanmak için şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a2da5-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="a2da5-106">Veritabanınız için sorgu bildirimlerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a2da5-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="a2da5-107">Veritabanına bağlanmak için kullanılan Kullanıcı KIMLIĞININ gerekli izinlere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a2da5-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="a2da5-108">İlişkili bir <xref:System.Data.SqlClient.SqlCommand> bildirim nesnesiyle (ya da) geçerli BIR SELECT ifadesini yürütmek için bir nesnesi <xref:System.Data.SqlClient.SqlDependency> kullanın <xref:System.Data.Sql.SqlNotificationRequest> .</span><span class="sxs-lookup"><span data-stu-id="a2da5-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="a2da5-109">İzlenen veriler değişirse bildirimi işlemek için kod sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a2da5-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="a2da5-110">Sorgu bildirimleri gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="a2da5-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="a2da5-111">Sorgu bildirimleri yalnızca belirli bir gereksinimler listesini karşılayan SELECT deyimleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="a2da5-112">Aşağıdaki tablo, SQL Server Çevrimiçi Kitaplar'da Service Broker ve Sorgu Bildirimleri belgelerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2da5-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a2da5-113">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="a2da5-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="a2da5-114">[Bildirim için sorgu oluşturma](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a2da5-114">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="a2da5-115">[Hizmet Aracısı için güvenlik konuları](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="a2da5-115">[Security Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="a2da5-116">[Güvenlik ve koruma (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a2da5-116">[Security and Protection (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="a2da5-117">[Bildirim Hizmetleri için güvenlik konuları](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="a2da5-117">[Security Considerations for Notifications Services](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="a2da5-118">[Sorgu bildirim Izinleri](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a2da5-118">[Query Notification Permissions](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="a2da5-119">[Hizmet Aracısı için uluslararası konular](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="a2da5-119">[International Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="a2da5-120">[Çözüm tasarımı konuları (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a2da5-120">[Solution Design Considerations (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="a2da5-121">[Hizmet Aracısı geliştirici bilgi merkezi](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a2da5-121">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="a2da5-122">[Geliştirici Kılavuzu (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="a2da5-122">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="a2da5-123">Örnek kod çalıştırmak için sorgu bildirimlerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a2da5-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="a2da5-124">SQL Server Management Studio kullanarak **AdventureWorks** veritabanında hizmet Aracısı etkinleştirmek Için aşağıdaki Transact-SQL ifadesini yürütün:</span><span class="sxs-lookup"><span data-stu-id="a2da5-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="a2da5-125">Sorgu bildirimi örneklerinin doğru çalışması için, veritabanı sunucusunda aşağıdaki Transact-SQL deyimlerinin yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="a2da5-126">Sorgu bildirimleri Izinleri</span><span class="sxs-lookup"><span data-stu-id="a2da5-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="a2da5-127">Bildirim isteyen komutları çalıştıran kullanıcıların, sunucuda abone sorgu BILDIRIMLERI veritabanı iznine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="a2da5-128">Kısmi güven durumunda çalışan istemci tarafı kodu için gerekir <xref:System.Data.SqlClient.SqlClientPermission> .</span><span class="sxs-lookup"><span data-stu-id="a2da5-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="a2da5-129">Aşağıdaki kod, <xref:System.Data.SqlClient.SqlClientPermission> öğesini olarak ayarlayarak bir nesnesi oluşturur <xref:System.Security.Permissions.PermissionState> <xref:System.Security.Permissions.PermissionState.Unrestricted> .</span><span class="sxs-lookup"><span data-stu-id="a2da5-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="a2da5-130"><xref:System.Security.CodeAccessPermission.Demand%2A> <xref:System.Security.SecurityException> Çağrı yığınında daha yüksek olan arayanlara izin verilmemişse, çalışma zamanında bir çalışma süresi zorlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="a2da5-131">Bildirim nesnesi seçme</span><span class="sxs-lookup"><span data-stu-id="a2da5-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="a2da5-132">Sorgu bildirimleri API 'SI, bildirimleri işlemek için iki nesne sağlar: <xref:System.Data.SqlClient.SqlDependency> ve <xref:System.Data.Sql.SqlNotificationRequest> .</span><span class="sxs-lookup"><span data-stu-id="a2da5-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="a2da5-133">Genel olarak, çoğu non-ASP.NET uygulaması <xref:System.Data.SqlClient.SqlDependency> nesnesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="a2da5-134">ASP.NET uygulamaları, <xref:System.Web.Caching.SqlCacheDependency> <xref:System.Data.SqlClient.SqlDependency> bildirim ve önbellek nesnelerini yönetmek için bir çerçeve sağlayan ve sağlayan daha yüksek düzeyi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="a2da5-135">SqlDependency kullanma</span><span class="sxs-lookup"><span data-stu-id="a2da5-135">Using SqlDependency</span></span>  
 <span data-ttu-id="a2da5-136">Kullanmak için <xref:System.Data.SqlClient.SqlDependency> , kullanılan SQL Server veritabanı için hizmet Aracısı etkinleştirilmelidir ve kullanıcıların bildirimleri almak için izinleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="a2da5-137">Bildirim kuyruğu gibi Hizmet Aracısı nesneleri önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="a2da5-138">Ayrıca, <xref:System.Data.SqlClient.SqlDependency> bildirimleri kuyruğa nakledildiği sırada işlemek için otomatik olarak bir çalışan iş parçacığı başlatır; Ayrıca, bilgileri olay bağımsız değişken verileri olarak ortaya çıkaran hizmet Aracısı iletisini de ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="a2da5-139"><xref:System.Data.SqlClient.SqlDependency>`Start`veritabanına bir bağımlılık oluşturmak için metodu çağırarak başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="a2da5-140">Bu, gereken her veritabanı bağlantısı için uygulama başlatma sırasında yalnızca bir kez çağrılması gereken statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="a2da5-141">`Stop`Yöntemi, yapılan her bağımlılık bağlantısı için uygulama sonlandırmada çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="a2da5-142">SqlNotificationRequest kullanma</span><span class="sxs-lookup"><span data-stu-id="a2da5-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="a2da5-143">Buna karşılık, <xref:System.Data.Sql.SqlNotificationRequest> Tüm dinleme altyapısını kendiniz uygulamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="a2da5-144">Ayrıca, sıra tarafından desteklenen sıra, hizmet ve ileti türleri gibi tüm destekleyici Hizmet Aracısı nesnelerinin tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2da5-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="a2da5-145">Bu el ile yaklaşım, uygulamanız özel bildirim iletileri veya bildirim davranışları gerektiriyorsa ya da uygulamanız daha büyük bir Hizmet Aracısı uygulamasının parçasıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2da5-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2da5-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2da5-146">See also</span></span>

- [<span data-ttu-id="a2da5-147">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="a2da5-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="a2da5-148">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a2da5-148">ADO.NET Overview</span></span>](../ado-net-overview.md)

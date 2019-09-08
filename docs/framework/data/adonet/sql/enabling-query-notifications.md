---
title: Sorgu Bildirimlerini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 9919bad113eb11a38ce137a2cbbf6c67bd5b21ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794078"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="94f7c-102">Sorgu Bildirimlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="94f7c-102">Enabling Query Notifications</span></span>
<span data-ttu-id="94f7c-103">Sorgu bildirimlerini kullanan uygulamaların ortak bir gereksinim kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="94f7c-104">Veri kaynağınız SQL sorgu bildirimlerini destekleyecek şekilde doğru yapılandırılmış olmalıdır ve Kullanıcı doğru istemci tarafı ve sunucu tarafı izinlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="94f7c-105">Sorgu bildirimlerini kullanmak için şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="94f7c-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="94f7c-106">Veritabanınız için sorgu bildirimlerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="94f7c-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="94f7c-107">Veritabanına bağlanmak için kullanılan Kullanıcı KIMLIĞININ gerekli izinlere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="94f7c-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="94f7c-108">İlişkili bir <xref:System.Data.SqlClient.SqlCommand> bildirim nesnesiyle (ya <xref:System.Data.Sql.SqlNotificationRequest>da <xref:System.Data.SqlClient.SqlDependency> ) geçerli bir SELECT ifadesini yürütmek için bir nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="94f7c-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="94f7c-109">İzlenen veriler değişirse bildirimi işlemek için kod sağlayın.</span><span class="sxs-lookup"><span data-stu-id="94f7c-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="94f7c-110">Sorgu bildirimleri gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="94f7c-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="94f7c-111">Sorgu bildirimleri yalnızca belirli bir gereksinimler listesini karşılayan SELECT deyimleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="94f7c-112">Aşağıdaki tablo, SQL Server Çevrimiçi Kitaplar'da Service Broker ve Sorgu Bildirimleri belgelerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="94f7c-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="94f7c-113">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="94f7c-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="94f7c-114">[Bildirim için sorgu oluşturma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="94f7c-114">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="94f7c-115">[Hizmet Aracısı için güvenlik konuları](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="94f7c-115">[Security Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="94f7c-116">[Güvenlik ve koruma (Hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="94f7c-116">[Security and Protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="94f7c-117">[Bildirim Hizmetleri için güvenlik konuları](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="94f7c-117">[Security Considerations for Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="94f7c-118">[Sorgu bildirim Izinleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="94f7c-118">[Query Notification Permissions](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="94f7c-119">[Hizmet Aracısı için uluslararası konular](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="94f7c-119">[International Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="94f7c-120">[Çözüm tasarımı konuları (Hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="94f7c-120">[Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="94f7c-121">[Hizmet Aracısı geliştirici bilgi merkezi](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="94f7c-121">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="94f7c-122">[Geliştirici Kılavuzu (Hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="94f7c-122">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="94f7c-123">Örnek kod çalıştırmak için sorgu bildirimlerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="94f7c-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="94f7c-124">SQL Server Management Studio kullanarak **AdventureWorks** veritabanında hizmet Aracısı etkinleştirmek Için aşağıdaki Transact-SQL ifadesini yürütün:</span><span class="sxs-lookup"><span data-stu-id="94f7c-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="94f7c-125">Sorgu bildirimi örneklerinin doğru çalışması için, veritabanı sunucusunda aşağıdaki Transact-SQL deyimlerinin yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="94f7c-126">Sorgu bildirimleri Izinleri</span><span class="sxs-lookup"><span data-stu-id="94f7c-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="94f7c-127">Bildirim isteyen komutları çalıştıran kullanıcıların, sunucuda abone sorgu BILDIRIMLERI veritabanı iznine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="94f7c-128">Kısmi güven durumunda çalışan istemci tarafı kodu için <xref:System.Data.SqlClient.SqlClientPermission>gerekir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="94f7c-129">Aşağıdaki kod, öğesini <xref:System.Data.SqlClient.SqlClientPermission> <xref:System.Security.Permissions.PermissionState> olarak <xref:System.Security.Permissions.PermissionState.Unrestricted>ayarlayarak bir nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94f7c-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="94f7c-130">Çağrı <xref:System.Security.CodeAccessPermission.Demand%2A> yığınında daha yüksek <xref:System.Security.SecurityException> olan arayanlara izin verilmemişse, çalışma zamanında bir çalışma süresi zorlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="94f7c-131">Bildirim nesnesi seçme</span><span class="sxs-lookup"><span data-stu-id="94f7c-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="94f7c-132">Sorgu bildirimleri API 'si, bildirimleri işlemek için iki nesne sağlar <xref:System.Data.SqlClient.SqlDependency> : <xref:System.Data.Sql.SqlNotificationRequest>ve.</span><span class="sxs-lookup"><span data-stu-id="94f7c-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="94f7c-133">Genel olarak, çoğu non-ASP.NET uygulaması <xref:System.Data.SqlClient.SqlDependency> nesnesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="94f7c-134">ASP.NET uygulamaları, bildirim ve önbellek nesnelerini yönetmek <xref:System.Web.Caching.SqlCacheDependency>için bir çerçeve <xref:System.Data.SqlClient.SqlDependency> sağlayan ve sağlayan daha yüksek düzeyi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="94f7c-135">SqlDependency kullanma</span><span class="sxs-lookup"><span data-stu-id="94f7c-135">Using SqlDependency</span></span>  
 <span data-ttu-id="94f7c-136">Kullanmak <xref:System.Data.SqlClient.SqlDependency>için, kullanılan SQL Server veritabanı için hizmet Aracısı etkinleştirilmelidir ve kullanıcıların bildirimleri almak için izinleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="94f7c-137">Bildirim kuyruğu gibi Hizmet Aracısı nesneleri önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="94f7c-138">Ayrıca, <xref:System.Data.SqlClient.SqlDependency> bildirimleri kuyruğa nakledildiği sırada işlemek için otomatik olarak bir çalışan iş parçacığı başlatır; Ayrıca, bilgileri olay bağımsız değişken verileri olarak ortaya çıkaran hizmet Aracısı iletisini de ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="94f7c-139"><xref:System.Data.SqlClient.SqlDependency>veritabanına bir bağımlılık oluşturmak için `Start` metodu çağırarak başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="94f7c-140">Bu, gereken her veritabanı bağlantısı için uygulama başlatma sırasında yalnızca bir kez çağrılması gereken statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="94f7c-141">Yöntemi `Stop` , yapılan her bağımlılık bağlantısı için uygulama sonlandırmada çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="94f7c-142">SqlNotificationRequest kullanma</span><span class="sxs-lookup"><span data-stu-id="94f7c-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="94f7c-143">Buna karşılık, <xref:System.Data.Sql.SqlNotificationRequest> tüm dinleme altyapısını kendiniz uygulamanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="94f7c-144">Ayrıca, sıra tarafından desteklenen sıra, hizmet ve ileti türleri gibi tüm destekleyici Hizmet Aracısı nesnelerinin tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="94f7c-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="94f7c-145">Bu el ile yaklaşım, uygulamanız özel bildirim iletileri veya bildirim davranışları gerektiriyorsa ya da uygulamanız daha büyük bir Hizmet Aracısı uygulamasının parçasıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="94f7c-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f7c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94f7c-146">See also</span></span>

- [<span data-ttu-id="94f7c-147">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="94f7c-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="94f7c-148">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="94f7c-148">ADO.NET Overview</span></span>](../ado-net-overview.md)

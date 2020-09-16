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
# <a name="enabling-query-notifications"></a>Sorgu Bildirimlerini Etkinleştirme
Sorgu bildirimlerini kullanan uygulamaların ortak bir gereksinim kümesi vardır. Veri kaynağınız SQL sorgu bildirimlerini destekleyecek şekilde doğru yapılandırılmış olmalıdır ve Kullanıcı doğru istemci tarafı ve sunucu tarafı izinlerine sahip olmalıdır.  
  
 Sorgu bildirimlerini kullanmak için şunları yapmanız gerekir:  
  
- Veritabanınız için sorgu bildirimlerini etkinleştirin.  
  
- Veritabanına bağlanmak için kullanılan Kullanıcı KIMLIĞININ gerekli izinlere sahip olduğundan emin olun.  
  
- İlişkili bir <xref:System.Data.SqlClient.SqlCommand> bildirim nesnesiyle (ya da) geçerli BIR SELECT ifadesini yürütmek için bir nesnesi <xref:System.Data.SqlClient.SqlDependency> kullanın <xref:System.Data.Sql.SqlNotificationRequest> .  
  
- İzlenen veriler değişirse bildirimi işlemek için kod sağlayın.  
  
## <a name="query-notifications-requirements"></a>Sorgu bildirimleri gereksinimleri  
 Sorgu bildirimleri yalnızca belirli bir gereksinimler listesini karşılayan SELECT deyimleri için desteklenir. Aşağıdaki tablo, SQL Server Çevrimiçi Kitaplar'da Service Broker ve Sorgu Bildirimleri belgelerine bağlantılar sağlar.  
  
 **SQL Server belgeleri**  
  
- [Bildirim için sorgu oluşturma](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Hizmet Aracısı için güvenlik konuları](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Güvenlik ve koruma (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Bildirim Hizmetleri için güvenlik konuları](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Sorgu bildirim Izinleri](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Hizmet Aracısı için uluslararası konular](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Çözüm tasarımı konuları (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Hizmet Aracısı geliştirici bilgi merkezi](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Geliştirici Kılavuzu (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Örnek kod çalıştırmak için sorgu bildirimlerini etkinleştirme  
 SQL Server Management Studio kullanarak **AdventureWorks** veritabanında hizmet Aracısı etkinleştirmek Için aşağıdaki Transact-SQL ifadesini yürütün:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Sorgu bildirimi örneklerinin doğru çalışması için, veritabanı sunucusunda aşağıdaki Transact-SQL deyimlerinin yürütülmesi gerekir.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Sorgu bildirimleri Izinleri  
 Bildirim isteyen komutları çalıştıran kullanıcıların, sunucuda abone sorgu BILDIRIMLERI veritabanı iznine sahip olması gerekir.  
  
 Kısmi güven durumunda çalışan istemci tarafı kodu için gerekir <xref:System.Data.SqlClient.SqlClientPermission> .  
  
 Aşağıdaki kod, <xref:System.Data.SqlClient.SqlClientPermission> öğesini olarak ayarlayarak bir nesnesi oluşturur <xref:System.Security.Permissions.PermissionState> <xref:System.Security.Permissions.PermissionState.Unrestricted> . <xref:System.Security.CodeAccessPermission.Demand%2A> <xref:System.Security.SecurityException> Çağrı yığınında daha yüksek olan arayanlara izin verilmemişse, çalışma zamanında bir çalışma süresi zorlayacaktır.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Bildirim nesnesi seçme  
 Sorgu bildirimleri API 'SI, bildirimleri işlemek için iki nesne sağlar: <xref:System.Data.SqlClient.SqlDependency> ve <xref:System.Data.Sql.SqlNotificationRequest> . Genel olarak, çoğu non-ASP.NET uygulaması <xref:System.Data.SqlClient.SqlDependency> nesnesini kullanmalıdır. ASP.NET uygulamaları, <xref:System.Web.Caching.SqlCacheDependency> <xref:System.Data.SqlClient.SqlDependency> bildirim ve önbellek nesnelerini yönetmek için bir çerçeve sağlayan ve sağlayan daha yüksek düzeyi kullanmalıdır.  
  
### <a name="using-sqldependency"></a>SqlDependency kullanma  
 Kullanmak için <xref:System.Data.SqlClient.SqlDependency> , kullanılan SQL Server veritabanı için hizmet Aracısı etkinleştirilmelidir ve kullanıcıların bildirimleri almak için izinleri olması gerekir. Bildirim kuyruğu gibi Hizmet Aracısı nesneleri önceden tanımlanmıştır.  
  
 Ayrıca, <xref:System.Data.SqlClient.SqlDependency> bildirimleri kuyruğa nakledildiği sırada işlemek için otomatik olarak bir çalışan iş parçacığı başlatır; Ayrıca, bilgileri olay bağımsız değişken verileri olarak ortaya çıkaran hizmet Aracısı iletisini de ayrıştırır. <xref:System.Data.SqlClient.SqlDependency>`Start`veritabanına bir bağımlılık oluşturmak için metodu çağırarak başlatılmalıdır. Bu, gereken her veritabanı bağlantısı için uygulama başlatma sırasında yalnızca bir kez çağrılması gereken statik bir yöntemdir. `Stop`Yöntemi, yapılan her bağımlılık bağlantısı için uygulama sonlandırmada çağrılmalıdır.  
  
### <a name="using-sqlnotificationrequest"></a>SqlNotificationRequest kullanma  
 Buna karşılık, <xref:System.Data.Sql.SqlNotificationRequest> Tüm dinleme altyapısını kendiniz uygulamanızı gerektirir. Ayrıca, sıra tarafından desteklenen sıra, hizmet ve ileti türleri gibi tüm destekleyici Hizmet Aracısı nesnelerinin tanımlanması gerekir. Bu el ile yaklaşım, uygulamanız özel bildirim iletileri veya bildirim davranışları gerektiriyorsa ya da uygulamanız daha büyük bir Hizmet Aracısı uygulamasının parçasıysa yararlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](query-notifications-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

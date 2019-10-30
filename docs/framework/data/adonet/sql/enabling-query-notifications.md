---
title: Sorgu Bildirimlerini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 84048a3fba2b32b1ae745160e2b405c04b738c65
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040236"
---
# <a name="enabling-query-notifications"></a>Sorgu Bildirimlerini Etkinleştirme
Sorgu bildirimlerini kullanan uygulamaların ortak bir gereksinim kümesi vardır. Veri kaynağınız SQL sorgu bildirimlerini destekleyecek şekilde doğru yapılandırılmış olmalıdır ve Kullanıcı doğru istemci tarafı ve sunucu tarafı izinlerine sahip olmalıdır.  
  
 Sorgu bildirimlerini kullanmak için şunları yapmanız gerekir:  
  
- Veritabanınız için sorgu bildirimlerini etkinleştirin.  
  
- Veritabanına bağlanmak için kullanılan Kullanıcı KIMLIĞININ gerekli izinlere sahip olduğundan emin olun.  
  
- İlişkili bir bildirim nesnesiyle (<xref:System.Data.SqlClient.SqlDependency> ya da <xref:System.Data.Sql.SqlNotificationRequest>) geçerli bir SELECT ifadesini yürütmek için <xref:System.Data.SqlClient.SqlCommand> nesnesini kullanın.  
  
- İzlenen veriler değişirse bildirimi işlemek için kod sağlayın.  
  
## <a name="query-notifications-requirements"></a>Sorgu bildirimleri gereksinimleri  
 Sorgu bildirimleri yalnızca belirli bir gereksinimler listesini karşılayan SELECT deyimleri için desteklenir. Aşağıdaki tablo, SQL Server Çevrimiçi Kitaplar'da Service Broker ve Sorgu Bildirimleri belgelerine bağlantılar sağlar.  
  
 **SQL Server belgeleri**  
  
- [Bildirim için sorgu oluşturma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Hizmet Aracısı için güvenlik konuları](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Güvenlik ve koruma (Hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Bildirim Hizmetleri için güvenlik konuları](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Sorgu bildirim Izinleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Hizmet Aracısı için uluslararası konular](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Çözüm tasarımı konuları (Hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Hizmet Aracısı geliştirici bilgi merkezi](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Geliştirici Kılavuzu (Hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
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
  
 Kısmi güven durumunda çalışan istemci tarafı kodu, <xref:System.Data.SqlClient.SqlClientPermission>gerektirir.  
  
 Aşağıdaki kod, <xref:System.Security.Permissions.PermissionState> <xref:System.Security.Permissions.PermissionState.Unrestricted>olarak ayarlayarak bir <xref:System.Data.SqlClient.SqlClientPermission> nesnesi oluşturur. Çağrı yığınındaki tüm arayanlara izin verilmemişse, <xref:System.Security.CodeAccessPermission.Demand%2A> çalışma zamanında bir <xref:System.Security.SecurityException> zorlayacaktır.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Bildirim nesnesi seçme  
 Sorgu bildirimleri API 'SI, bildirimleri işlemek için iki nesne sağlar: <xref:System.Data.SqlClient.SqlDependency> ve <xref:System.Data.Sql.SqlNotificationRequest>. Genel olarak, çoğu non-ASP.NET uygulaması <xref:System.Data.SqlClient.SqlDependency> nesnesini kullanmalıdır. ASP.NET uygulamaları, <xref:System.Data.SqlClient.SqlDependency> sarmalayan ve bildirim ve önbellek nesnelerini yönetmek için bir çerçeve sağlayan daha yüksek düzey <xref:System.Web.Caching.SqlCacheDependency>kullanmalıdır.  
  
### <a name="using-sqldependency"></a>SqlDependency kullanma  
 <xref:System.Data.SqlClient.SqlDependency>kullanmak için, kullanılan SQL Server veritabanı için Hizmet Aracısı etkinleştirilmeli ve kullanıcıların bildirimleri almak için izinleri olması gerekir. Bildirim kuyruğu gibi Hizmet Aracısı nesneleri önceden tanımlanmıştır.  
  
 Ayrıca, <xref:System.Data.SqlClient.SqlDependency> kuyruğa nakledildiği sırada bildirimleri işlemek için otomatik olarak bir çalışan iş parçacığı başlatır; Ayrıca, bilgileri olay bağımsız değişken verileri olarak ortaya çıkaran Hizmet Aracısı iletisini ayrıştırır. veritabanına bir bağımlılık oluşturmak için `Start` yöntemi çağırarak <xref:System.Data.SqlClient.SqlDependency> başlatılmalıdır. Bu, gereken her veritabanı bağlantısı için uygulama başlatma sırasında yalnızca bir kez çağrılması gereken statik bir yöntemdir. `Stop` yöntemi, yapılan her bağımlılık bağlantısı için uygulama sonlandırmada çağrılmalıdır.  
  
### <a name="using-sqlnotificationrequest"></a>SqlNotificationRequest kullanma  
 Buna karşılık <xref:System.Data.Sql.SqlNotificationRequest>, tüm dinleme altyapısını kendiniz uygulamanızı gerektirir. Ayrıca, sıra tarafından desteklenen sıra, hizmet ve ileti türleri gibi tüm destekleyici Hizmet Aracısı nesnelerinin tanımlanması gerekir. Bu el ile yaklaşım, uygulamanız özel bildirim iletileri veya bildirim davranışları gerektiriyorsa ya da uygulamanız daha büyük bir Hizmet Aracısı uygulamasının parçasıysa yararlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](query-notifications-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

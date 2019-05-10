---
title: Sorgu Bildirimlerini Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 0c377e02d5be7cb4de41d62b1e3734f790115086
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651225"
---
# <a name="enabling-query-notifications"></a>Sorgu Bildirimlerini Etkinleştirme
Sorgu bildirimleri kullanan uygulamaları bir ortak gereksinimleri vardır. Veri kaynağı doğru SQL sorgu bildirimleri destekleyecek şekilde yapılandırılmalıdır ve kullanıcı doğru istemci ve sunucu tarafı izinlere sahip olmalıdır.  
  
 Sorgu bildirimleri gerekir kullanmak için:  
  
- Veritabanınız için sorgu bildirimleri etkinleştirin.  
  
- Veritabanına bağlanmak için kullanılan kullanıcı kimliği gerekli izinlere sahip olduğundan emin olun.  
  
- Kullanım bir <xref:System.Data.SqlClient.SqlCommand> ilişkili bildirim nesnesi ile geçerli bir SELECT deyimi yürütmek için nesne — ya da <xref:System.Data.SqlClient.SqlDependency> veya <xref:System.Data.Sql.SqlNotificationRequest>.  
  
- Veri izlenmekte olan bildirim işlemi verirsiniz değişiklikler.  
  
## <a name="query-notifications-requirements"></a>Sorgu bildirimleri gereksinimleri  
 Sorgu bildirimleri yalnızca belirli bir gereksinimler listesini karşılayan SELECT deyimleri için desteklenir. Aşağıdaki tablo, SQL Server Çevrimiçi Kitaplar'da Service Broker ve Sorgu Bildirimleri belgelerine bağlantılar sağlar.  
  
 **SQL Server belgeleri**  
  
- [Bildirim için sorgu oluşturma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Hizmet aracısı için güvenlik konuları](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Güvenlik ve koruma (hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Bildirim Hizmetleri için güvenlik konuları](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Sorgu bildirim izinleri](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Service Broker için Uluslararası konular](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Çözüm tasarımı konuları (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Service Broker Geliştirici Bilgi Merkezi](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Geliştirici Kılavuzu (hizmet Aracısı)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Örnek kodu çalıştırma etkinleştirme sorgu bildirimleri  
 Hizmet Aracısı etkinleştirmek için **AdventureWorks** veritabanı SQL Server Management Studio kullanarak, aşağıdaki Transact-SQL deyimi çalıştırın:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Sorgu bildirim örnekleri düzgün çalışması aşağıdaki Transact-SQL deyimlerini veritabanı sunucusunda yürütülmelidir.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Sorgu bildirimleri izinleri  
 Bildirim sorgu bildirimleri abone olmalıdır isteyen komutları yürütmek kullanıcılar izin sunucuda veritabanı.  
  
 Kısmi güven durumda çalışan istemci tarafı kod gerektiren <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Aşağıdaki kod oluşturur bir <xref:System.Data.SqlClient.SqlClientPermission> ayar nesnesi <xref:System.Security.Permissions.PermissionState> için <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> Zorlar bir <xref:System.Security.SecurityException> çağrı yığınında daha yüksek tüm çağıranların izni verilmemiş, çalışma zamanında.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Bir bildirim nesne seçme  
 Sorgu bildirimleri API'si bildirimleri işlemek için iki nesne sağlar: <xref:System.Data.SqlClient.SqlDependency> ve <xref:System.Data.Sql.SqlNotificationRequest>. Genel olarak, çoğu ASP.NET olmayan uygulamaları kullanması gereken <xref:System.Data.SqlClient.SqlDependency> nesne. ASP.NET uygulamaları üst düzey kullanın <xref:System.Web.Caching.SqlCacheDependency>, sarmalayan <xref:System.Data.SqlClient.SqlDependency> ve bildirim ve önbellek nesneleri yönetmek için bir çerçeve sunar.  
  
### <a name="using-sqldependency"></a>SqlDependency kullanma  
 Kullanılacak <xref:System.Data.SqlClient.SqlDependency>hizmet aracısı için kullanılan SQL Server veritabanı etkin olması ve kullanıcıların bildirimleri almak için izinlere sahip olması gerekir. Bildirim sırası gibi hizmet Aracısı nesneleri önceden tanımlanmıştır.  
  
 Ayrıca, <xref:System.Data.SqlClient.SqlDependency> otomatik olarak başlatılan bir çalışan iş parçacığı kuyruğa gönderilen bildirimleri işlemek için; ayrıca olay bağımsız değişkeni veri bilgileri gösterme hizmet Aracısı iletiyi ayrıştırır. <xref:System.Data.SqlClient.SqlDependency> çağırarak başlatılmalıdır `Start` veritabanına bir bağımlılık oluşturmak için yöntemi. Gereken her bir veritabanı bağlantısı için uygulama başlatma sırasında yalnızca bir kez çağrılması gereken bir statik yöntem budur. `Stop` Yöntemi sırasında yapılan her bir bağımlılık bağlantısı için uygulama sonlandırma çağrılabilir.  
  
### <a name="using-sqlnotificationrequest"></a>SqlNotificationRequest kullanma  
 Buna karşılık, <xref:System.Data.Sql.SqlNotificationRequest> tüm dinleme altyapısını kendi başınıza uygulamak gerektirir. Ayrıca, kuyruğu, hizmet ve ileti kuyruğu tarafından desteklenen türleri gibi tüm destekleyici hizmet Aracısı nesnelerini tanımlanmalıdır. El ile bu yaklaşım, uygulamanız özel bildirim iletileri ya da bildirim davranışları gerektiriyorsa veya uygulamanız daha büyük bir hizmet Aracısı uygulamanın parçası ise yararlı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

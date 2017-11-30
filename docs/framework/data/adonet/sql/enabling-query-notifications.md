---
title: "Sorgu bildirimleri etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fbdec484af39eb4d98418ad72ed66ef7913f2d56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-query-notifications"></a>Sorgu bildirimleri etkinleştirme
Sorgu bildirimleri kullanmasına uygulamalarının ortak bir dizi gereksinim vardır. Veri kaynağınızı SQL sorgu bildirimleri desteklemek için doğru şekilde yapılandırılmalıdır ve kullanıcı doğru istemci ve sunucu tarafı izinlerine sahip olmalıdır.  
  
 Sorgu bildirimleri gerekir kullanmak için:  
  
-   Veritabanınız için sorgu bildirimleri etkinleştirin.  
  
-   Veritabanına bağlanmak için kullanılan kullanıcı kimliği gerekli izinlere sahip olduğundan emin olun.  
  
-   Kullanım bir <xref:System.Data.SqlClient.SqlCommand> bir ilişkili bildirim nesne geçerli bir SELECT deyimi yürütmek için nesne — ya da <xref:System.Data.SqlClient.SqlDependency> veya <xref:System.Data.Sql.SqlNotificationRequest>.  
  
-   Bildirim verileri izlenmekte olan varsa işlemek için kod değişiklikleri.  
  
## <a name="query-notifications-requirements"></a>Sorgu bildirimleri gereksinimleri  
 Sorgu bildirimleri yalnızca belirli bir gereksinimler listesini karşılayan SELECT deyimleri için desteklenir. Aşağıdaki tablo, SQL Server Çevrimiçi Kitaplar'da Service Broker ve Sorgu Bildirimleri belgelerine bağlantılar sağlar.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
-   [Bildirim için sorgu oluşturma](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Hizmet aracısı için güvenlik konuları](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [Güvenlik ve koruma (hizmet Aracısı)](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [Bildirim Hizmetleri için güvenlik konuları](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [Sorgu bildirim izinleri](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [Hizmet aracısı için Uluslararası ilgili önemli noktalar](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [Çözüm tasarım konuları (hizmet Aracısı)](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [Hizmet aracısı geliştirici Bilgi Merkezi](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Geliştirici Kılavuzu (hizmet Aracısı)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Örnek kodu çalıştırmak için etkinleştirme sorgu bildirimleri  
 Hizmet Aracısı etkinleştirmek için **AdventureWorks** veritabanı SQL Server Management Studio kullanarak, aşağıdaki Transact-SQL deyimini yürütün:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Sorgu bildirim örnekleri düzgün çalışması veritabanı sunucusunda aşağıdaki Transact-SQL deyimi yürütülmelidir.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Sorgu bildirimleri izinleri  
 Bildirim sorgu bildirimleri abone olmalıdır isteyen komutları yürütün kullanıcılar izni sunucuda veritabanı.  
  
 Kısmi güven durumda çalışan bir istemci-tarafı kod gerektirir <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Aşağıdaki kod oluşturur bir <xref:System.Data.SqlClient.SqlClientPermission> ayarı nesne <xref:System.Security.Permissions.PermissionState> için <xref:System.Security.Permissions.PermissionState.Unrestricted>. <xref:System.Security.CodeAccessPermission.Demand%2A> Zorlayacağı bir <xref:System.Security.SecurityException> tüm arayanlar çağrı yığınında yüksek izni verilmemiş, çalışma zamanında.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Bir bildirim nesnesi seçme  
 Sorgu bildirimleri API'sı bildirimleri işlemek için iki nesne sağlar: <xref:System.Data.SqlClient.SqlDependency> ve <xref:System.Data.Sql.SqlNotificationRequest>. Genel olarak, çoğu ASP.NET olmayan uygulamaları kullanması gereken <xref:System.Data.SqlClient.SqlDependency> nesnesi. ASP.NET uygulamaları kullanması gereken üst düzey <xref:System.Web.Caching.SqlCacheDependency>, hangi sarmalayan <xref:System.Data.SqlClient.SqlDependency> ve bildirim ve önbellek nesneleri yönetmek için bir çerçeve sağlar.  
  
### <a name="using-sqldependency"></a>SqlDependency kullanma  
 Kullanılacak <xref:System.Data.SqlClient.SqlDependency>, hizmet Aracısı kullanılan SQL Server veritabanı için etkin olması ve kullanıcıların bildirimleri almak için izinlere sahip olması gerekir. Bildirim sırası gibi hizmet Aracısı nesnelerini önceden tanımlanmıştır.  
  
 Ayrıca, <xref:System.Data.SqlClient.SqlDependency> otomatik olarak başlatır bir çalışan iş parçacığı kuyruğa gönderilen bildirimleri işleme için; ayrıca bilgileri olay bağımsız değişken veri olarak gösterme hizmet Aracısı ileti ayrıştırır. <xref:System.Data.SqlClient.SqlDependency>çağırarak başlatılmalıdır `Start` veritabanı için bir bağımlılık oluşturmak için yöntem. Bu yalnızca bir kez gerekli her veritabanı bağlantısı için uygulama başlatma sırasında çağrılması gereken statik bir yöntemdir. `Stop` Yöntemi uygulama sonlandırma yapılan her bağımlılık bağlantı sırasında çağrılabilir.  
  
### <a name="using-sqlnotificationrequest"></a>SqlNotificationRequest kullanma  
 Buna karşılık, <xref:System.Data.Sql.SqlNotificationRequest> tüm dinleme altyapısında kendiniz uygulamak gerektirir. Ayrıca, sıra, hizmet ve ileti sıra tarafından desteklenen türleri gibi tüm destekleyici hizmet Aracısı nesneleri tanımlanmalıdır. El ile bu yaklaşım uygulamanız özel bildirim iletilerini veya bildirim davranışları gerektiriyorsa veya uygulamanızın daha büyük bir hizmet Aracısı uygulamanın parçası ise yararlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server'da sorgu bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

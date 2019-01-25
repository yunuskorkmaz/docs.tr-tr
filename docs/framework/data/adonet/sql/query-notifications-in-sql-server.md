---
title: SQL Server'da sorgu bildirimleri
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 87335b5c9ad626e998fdb7bf0e71cae2542386f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636696"
---
# <a name="query-notifications-in-sql-server"></a>SQL Server'da sorgu bildirimleri
Hizmet Aracısı altyapı inşa edilen uygulamalar, veriler değiştiğinde bildirim almak sorgu bildirimleri sağlar. Bu özellik, bilgileri bir veritabanından, bir Web uygulaması gibi bir önbellek sağlamanız ve kaynak veriler değiştiğinde bildirim almak gereken uygulamalar için özellikle yararlıdır.  
  
 ADO.NET kullanarak sorgu bildirimleri uygulamak üç yol vardır:  
  
1.  Alt düzey uygulama tarafından sağlanan `SqlNotificationRequest` komut bir bildirim isteği ile yürütme olanak sağlayan, sunucu tarafı işlevler gösteren sınıf.  
  
2.  Üst düzey uygulama tarafından sağlanan `SqlDependency` üst düzey bir soyutlama bildirim işlevselliği arasında kaynak uygulaması ve SQL Server, değişiklikleri algılamak için bir bağımlılık kullanmanıza olanak sağlayan bir sınıf olan sınıf Sunucu. Çoğu durumda, bu SQL Server için .NET Framework veri sağlayıcısı kullanarak yönetilen istemci uygulamalar tarafından SQL Server bildirim özelliği yararlanmak için basit ve en etkili yoludur.  
  
3.  Ayrıca, Web uygulamaları ASP.NET 2.0 kullanılarak oluşturulan veya daha sonra kullanabileceğiniz `SqlCacheDependency` yardımcı sınıfları.  
  
 Sorgu bildirimleri yenilemek için gerek duyan uygulamalar için kullanılan görüntüler veya yanıt temel alınan verilerde yapılan değişiklikler olarak önbelleğe alır. Microsoft SQL Server, SQL Server ve aynı komutu çalıştırıldığında istek bildirimi komut başlangıçta alınan olanlardan farklı sonuç kümesi oluşturur göndermek .NET Framework uygulamaları sağlar. Sunucuda oluşturulan tüm bildirimleri, daha sonra işlenmek üzere kuyruklar üzerinden gönderilir.  
  
 Bildirimler için seçin ve ÇALIŞTIRMA deyimleri ayarlayabilirsiniz. EXECUTE deyimi kullanılırken, SQL Server EXECUTE deyimi kendisi yerine yürütülen komut bir bildirime kaydolur. Komutu, bir SELECT deyimi sınırlamaları ve gereksinimleri karşılaması gerekir. Bir bildirim kaydeden bir komutu birden fazla deyim içeren veritabanı altyapısı toplu işlemde her deyim için bir bildirim oluşturur.  
  
 Veriler değiştiğinde, güvenilir saniyenin bildirimleri gereken bir uygulama geliştiriyorsanız, bölümleri gözden geçirin. **verimli bir sorgu bildirimleri stratejisi planlama** ve **sorgu alternatifleri Bildirimleri** içinde [bildirimleri için planlama](https://go.microsoft.com/fwlink/?LinkId=211984) konu SQL Server Books Online. Sorgu bildirimleri ve SQL Server hizmet Aracısı hakkında daha fazla bilgi için aşağıdaki konulara bağlantılar da SQL Server Books Online'a bakın.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
-   [Sorgu bildirimleri kullanma](https://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Bildirim için sorgu oluşturma](https://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Hizmet Aracısı](https://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Service Broker Geliştirici Bilgi Merkezi](https://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Geliştirme (hizmet Aracısı)](https://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sorgu Bildirimlerini Etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 Sorgu bildirimleri, etkinleştirmek ve bunları kullanmak için gereksinimleri dahil olmak üzere kullanmayı açıklar.  
  
 [Bir ASP.NET Uygulamasında SqlDependency](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Sorgu bildirimleri bir ASP.NET uygulamasından nasıl yapılacağı açıklanır.  
  
 [SqlDependency ile Değişiklikleri Algılama](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Sorgu sonuçları başlangıçta alınan olanlardan farklı Algıla gösterilmektedir.  
  
 [Bir SqlNotificationRequest ile SqlCommand Yürütme](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Yapılandırma gösteren bir <xref:System.Data.SqlClient.SqlCommand> bir sorgu bildirimi ile çalışmak için nesne.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Açıklar <xref:System.Data.Sql.SqlNotificationRequest> sınıfı ve tüm üyeleri.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Açıklar <xref:System.Data.SqlClient.SqlDependency> sınıfı ve tüm üyeleri.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Açıklar <xref:System.Web.Caching.SqlCacheDependency> sınıfı ve tüm üyeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

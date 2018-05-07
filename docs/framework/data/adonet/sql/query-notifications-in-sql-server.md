---
title: SQL Server'da sorgu bildirimleri
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 60ab686437f764a006fca5a2043d02288ea46d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="query-notifications-in-sql-server"></a>SQL Server'da sorgu bildirimleri
Hizmet Aracısı altyapı inşa edilen sorgu bildirimleri veriler değiştiğinde bildirim almak uygulamaların olanak tanır. Bu özellik, bilgileri bir veritabanından, bir Web uygulaması gibi bir önbellekte sağlamak ve veri kaynağını değiştiğinde bildirim almak gereken uygulamalar için özellikle yararlıdır.  
  
 ADO.NET kullanarak sorgu bildirimleri uygulayabilirsiniz üç yolu vardır:  
  
1.  Alt düzey uygulama tarafından sağlanan `SqlNotificationRequest` sunucu tarafı işlevselliği, size bir bildirim isteği ile komut yürütme etkinleştirme gösteren sınıf.  
  
2.  Üst düzey uygulama tarafından sağlanan `SqlDependency` kaynak uygulama ve SQL Server, bağımlılık değişiklikleri algılamak için kullanmak üzere etkinleştirme arasında bildirim işlevinin üst düzey bir Özet sağlar sınıftır sınıfı Sunucu. Çoğu durumda, SQL Server için .NET Framework veri sağlayıcısı kullanarak yönetilen istemci uygulamalar tarafından SQL Server bildirimleri yeteneğinden yararlanabilir basit ve en etkili yolu budur.  
  
3.  Ayrıca, Web uygulamaları ASP.NET 2.0 kullanılarak oluşturulmuş ya da daha sonra kullanabileceğiniz `SqlCacheDependency` yardımcı sınıfları.  
  
 Sorgu bildirimleri yenilemek için gereken uygulamalar için kullanılan görüntüler veya yanıt temel alınan verilerde yapılan değişiklikler olarak önbelleğe alır. Microsoft SQL Server, SQL Server ve aynı komutu çalıştırıldığında istek bildirim komutuna başlangıçta alınan olanlardan farklı sonuç kümesi oluşturur göndermek .NET Framework uygulamaları sağlar. Sunucuda oluşturulan bildirimleri daha sonra işlenmek üzere kuyruklar üzerinden gönderilir.  
  
 Seçim için bildirimleri ve ÇALIŞTIRMA deyimleri ayarlayabilirsiniz. Bir EXECUTE deyimi kullanılırken, SQL Server EXECUTE deyimi kendisi yerine yürütülen komut bir bildirime kaydolur. Komut bir SELECT deyimi için kısıtlamaları ve gereksinimleri karşılaması gerekir. Birden fazla deyim bir bildirim kaydeden bir komut içerir, veritabanı altyapısı her deyim için bir bildirim toplu işlemde oluşturur.  
  
 Veriler değiştiğinde güvenilir saniyeden bildirimleri ihtiyaç duyacağınız bir uygulama geliştiriyorsanız, bölümleri gözden **verimli bir sorgu bildirimleri stratejisi planlama** ve **sorgu alternatifleri Bildirimleri** içinde [bildirimleri için planlama](http://go.microsoft.com/fwlink/?LinkId=211984) SQL Server Books Online konusu. Sorgu bildirimleri ve SQL Server hizmet Aracısı hakkında daha fazla bilgi için SQL Server Books Online'da konular için aşağıdaki bağlantılara bakın.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
-   [Sorgu bildirimleri kullanma](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Bildirim için sorgu oluşturma](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Hizmet Aracısı](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Hizmet aracısı geliştirici Bilgi Merkezi](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Geliştirme (hizmet Aracısı)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sorgu Bildirimlerini Etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 Etkinleştirme ve bunları kullanarak gereksinimlerini de dahil olmak üzere sorgu bildirimlerinin nasıl kullanılacağını açıklar.  
  
 [Bir ASP.NET Uygulamasında SqlDependency](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Bir ASP.NET uygulamasında sorgu bildirimlerinin nasıl kullanılacağını gösterir.  
  
 [SqlDependency ile Değişiklikleri Algılama](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Sorgu sonuçları başlangıçta alınan olanlardan farklı algılayabilir gösterir.  
  
 [Bir SqlNotificationRequest ile SqlCommand Yürütme](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Yapılandırma gösteren bir <xref:System.Data.SqlClient.SqlCommand> sorgu bildirimi ile çalışmak için nesne.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Açıklar <xref:System.Data.Sql.SqlNotificationRequest> sınıfı ve tüm üyeleri.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Açıklar <xref:System.Data.SqlClient.SqlDependency> sınıfı ve tüm üyeleri.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Açıklar <xref:System.Web.Caching.SqlCacheDependency> sınıfı ve tüm üyeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

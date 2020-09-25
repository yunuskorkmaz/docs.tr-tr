---
title: SQL Server'da Sorgu Bildirimleri
description: SQL Server veritabanında veri değiştirildiğinde uygulamalara bildirim almak için sorgu bildirimlerini nasıl kullanacağınızı öğrenin, örneğin, uygulama ekranları yenilemek için.
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 8001f75d7e278a965b6e8e00e4b9af7b770a8bb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183097"
---
# <a name="query-notifications-in-sql-server"></a>SQL Server'da Sorgu Bildirimleri

Hizmet Aracısı altyapısına inşa edildiğinde sorgu bildirimleri, veriler değiştiğinde uygulamalara bildirim gönderilmesini sağlar. Bu özellik özellikle bir Web uygulaması gibi bir veritabanından bilgi önbelleği sağlayan ve kaynak veriler değiştirildiğinde bildirilmesi gereken uygulamalar için yararlıdır.  
  
 ADO.NET kullanarak sorgu bildirimleri uygulayabileceğiniz üç yol vardır:  
  
1. Düşük düzey uygulama, `SqlNotificationRequest` sunucu tarafı işlevselliğini kullanıma sunan sınıf tarafından sağlanır ve bir komut, bildirim isteğiyle birlikte yürütmelerine olanak tanır.  
  
2. Üst düzey uygulama, `SqlDependency` kaynak uygulama ve SQL Server arasında yüksek düzeyde bir bildirim işlevselliği sağlayan sınıfı tarafından sağlanır ve bu, sunucudaki değişiklikleri algılamak için bir bağımlılık kullanmanıza olanak sağlar. Çoğu durumda bu, SQL Server için .NET Framework Veri Sağlayıcısı kullanarak yönetilen istemci uygulamaları tarafından SQL Server bildirim yeteneğinin faydalanacak en basit ve en etkili yoldur.  
  
3. Ayrıca, ASP.NET 2,0 veya üzeri kullanılarak oluşturulan Web uygulamaları `SqlCacheDependency` yardımcı sınıfları kullanabilir.  
  
 Sorgu bildirimleri, temel verilerdeki değişikliklere yanıt olarak, ekranları veya önbellekleri yenilemesi gereken uygulamalar için kullanılır. Microsoft SQL Server, .NET Framework uygulamaların SQL Server bir komut göndermesini ve aynı komutun yürütülmesi, başlangıçta alınanlardan farklı sonuç kümeleri üretmesi durumunda bildirim istemesi için izin verir. Sunucuda oluşturulan bildirimler daha sonra işlenmek üzere kuyruklarla gönderilir.  
  
 SELECT ve EXECUTE deyimlerine yönelik bildirimler ayarlayabilirsiniz. EXECUTE ifadesini kullanırken, SQL Server EXECUTE ifadesinin kendisi yerine yürütülen komut için bir bildirim kaydeder. Komutun, SELECT ifadesiyle ilgili gereksinimleri ve sınırlamaları karşılaması gerekir. Bildirimi kaydeden bir komut birden fazla ifade içeriyorsa, veritabanı altyapısı toplu işteki her bir bildirim için bir bildirim oluşturur.  
  
 Veriler değiştiğinde güvenilir alt-ikinci bildirimlere ihtiyacınız olan bir uygulama geliştiriyorsanız, **etkili bir sorgu bildirimleri stratejisi planlama** ve [bildirim planlaması](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) makalesinde **sorgu bildirimlerinin alternatiflerini** planlama başlıklı bölümleri gözden geçirin. Sorgu bildirimleri ve SQL Server Hizmet Aracısı hakkında daha fazla bilgi için, SQL Server belgelerindeki makalelere yönelik aşağıdaki bağlantılara bakın.  
  
 **SQL Server belgeleri**  
  
- [Sorgu bildirimlerini kullanma](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Bildirim için sorgu oluşturma](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Geliştirme (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Hizmet Aracısı geliştirici bilgi merkezi](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Geliştirici Kılavuzu (Hizmet Aracısı)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Sorgu Bildirimlerini Etkinleştirme](enabling-query-notifications.md)  
 ' Nin etkinleştirilmesi ve kullanılması ile ilgili gereksinimler dahil olmak üzere sorgu bildirimlerinin nasıl kullanılacağını açıklar.  
  
 [Bir ASP.NET Uygulamasında SqlDependency](sqldependency-in-an-aspnet-app.md)  
 ASP.NET uygulamasından sorgu bildirimlerinin nasıl kullanılacağını gösterir.  
  
 [SqlDependency ile Değişiklikleri Algılama](detecting-changes-with-sqldependency.md)  
 Sorgu sonuçlarının başlangıçta alınanlardan farklı olacağını nasıl algılayabileceğinizi gösterir.  
  
 [Bir SqlNotificationRequest ile SqlCommand Yürütme](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Bir <xref:System.Data.SqlClient.SqlCommand> nesneyi sorgu bildirimiyle çalışacak şekilde yapılandırmayı gösterir.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.Data.Sql.SqlNotificationRequest>  
 <xref:System.Data.Sql.SqlNotificationRequest>Sınıfını ve tüm üyelerini açıklar.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <xref:System.Data.SqlClient.SqlDependency>Sınıfını ve tüm üyelerini açıklar.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <xref:System.Web.Caching.SqlCacheDependency>Sınıfını ve tüm üyelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

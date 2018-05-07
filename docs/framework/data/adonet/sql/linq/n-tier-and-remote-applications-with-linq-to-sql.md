---
title: N katmanlı ve uzak uygulamalarla LINQ-SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 6fd31fd565d09b53cba74cd307f211d5bc0d68b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N katmanlı ve uzak uygulamalarla LINQ-SQL
Kullanan n katmanlı veya çok katmanlı uygulamalar oluşturabileceğiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Genellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlamı, sınıflar ve sorgu oluşturma mantığı bulunur Orta katmanda (DAL) veri erişim katmanı. İş mantığı ve kalıcı olmayan veriler tamamen kısmi sınıflar ve yöntemler varlıkları ve veri bağlamı içinde uygulanabilir veya ayrı sınıflarda uygulanabilir.  
  
 İstemci veya sunu katmanı orta katman uzak arabirimde yöntemleri çağırır ve bu katmanda DAL sorgular veya eşlendiği saklı yordamlar yürütecek <xref:System.Data.Linq.DataContext> yöntemleri. Orta katman veri istemcilere genellikle varlıklar veya proxy nesneleri XML gösterimlerini döndürür.  
  
 Orta katmanda varlıklar durumlarına izler ve ertelenmiş yüklenmesini ve değişiklikleri teslimini veritabanına yöneten veri bağlamı tarafından oluşturulur. Bu varlıklar "bağlı" `DataContext`. Varlıkları seri hale getirme yoluyla başka bir katmana gönderildikten sonra ancak başka bir deyişle, ayrılmış, olduklarında `DataContext` durumlarına artık izlemektir. İstemci güncelleştirmelerini geri gönderir varlıkları yeniden, önce veri bağlamı için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklikler veritabanına gönderebilirsiniz. İstemci özgün değerler sağlamaktan sorumludur ve/veya bu iyimser eşzamanlılık denetimleri için gerekli olduğunda zaman damgaları orta katman yedekleyin.  
  
 ASP.NET uygulamalarında <xref:System.Web.UI.WebControls.LinqDataSource> çoğu bu karmaşıklık yönetir. Daha fazla bilgi için bkz: [NIB: LinqDataSource Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="additional-resources"></a>Ek Kaynaklar  
 Kullanan n katmanlı uygulamalar uygulama hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aşağıdaki konulara bakın:  
  
-   [ASP.NET ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [Web Hizmetleri ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [Sıkıca Bağlı İstemci-Sunucu Uygulamaları ile LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [N Katmanı İş Mantığını Uygulama](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 ADO.NET veri kümelerini kullanan n katmanlı uygulamalar hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

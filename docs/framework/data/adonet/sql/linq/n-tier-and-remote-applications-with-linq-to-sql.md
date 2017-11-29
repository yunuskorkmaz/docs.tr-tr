---
title: "N katmanlı ve uzak uygulamalarla LINQ-SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f44b6da8ecc8d036a9550856f71b2981770e9478
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>N katmanlı ve uzak uygulamalarla LINQ-SQL
Kullanan n katmanlı veya çok katmanlı uygulamalar oluşturabileceğiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Genellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlamı, sınıflar ve sorgu oluşturma mantığı bulunur Orta katmanda (DAL) veri erişim katmanı. İş mantığı ve kalıcı olmayan veriler tamamen kısmi sınıflar ve yöntemler varlıkları ve veri bağlamı içinde uygulanabilir veya ayrı sınıflarda uygulanabilir.  
  
 İstemci veya sunu katmanı orta katman uzak arabirimde yöntemleri çağırır ve bu katmanda DAL sorgular veya eşlendiği saklı yordamlar yürütecek <xref:System.Data.Linq.DataContext> yöntemleri. Orta katman veri istemcilere genellikle varlıklar veya proxy nesneleri XML gösterimlerini döndürür.  
  
 Orta katmanda varlıklar durumlarına izler ve ertelenmiş yüklenmesini ve değişiklikleri teslimini veritabanına yöneten veri bağlamı tarafından oluşturulur. Bu varlıklar "bağlı" `DataContext`. Varlıkları seri hale getirme yoluyla başka bir katmana gönderildikten sonra ancak başka bir deyişle, ayrılmış, olduklarında `DataContext` durumlarına artık izlemektir. İstemci güncelleştirmelerini geri gönderir varlıkları yeniden, önce veri bağlamı için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklikler veritabanına gönderebilirsiniz. İstemci özgün değerler sağlamaktan sorumludur ve/veya bu iyimser eşzamanlılık denetimleri için gerekli olduğunda zaman damgaları orta katman yedekleyin.  
  
 ASP.NET uygulamalarında <xref:System.Web.UI.WebControls.LinqDataSource> çoğu bu karmaşıklık yönetir. Daha fazla bilgi için bkz: [NIB: LinqDataSource Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="additional-resources"></a>Ek Kaynaklar  
 Kullanan n katmanlı uygulamalar uygulama hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aşağıdaki konulara bakın:  
  
-   [LINQ-SQL N katmanlı ASP.NET ile](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [LINQ-SQL N katmanlı Web Hizmetleri](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [LINQ-SQL ile sıkı şekilde bağlı istemci-sunucu uygulamaları](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [N katmanlı iş mantığı uygulama](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [Veri alma ve CUD işlemleri N katmanlı uygulamalarda (LINQ-SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 ADO.NET veri kümelerini kullanan n katmanlı uygulamalar hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka plan bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

---
title: LINQ to SQL ile N Katmanı ve Uzak Uygulamalar
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 31f06fd5e840c51c0133d22078d79cd4f945c369
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660912"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>LINQ to SQL ile N Katmanı ve Uzak Uygulamalar
Kullanan n katmanlı veya çok katmanlı uygulamaları oluşturabileceğiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Genellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlamı, varlık sınıfları ve sorgu oluşturma mantığı bulunur Orta katmanda veri erişim katmanı (DAL). İş mantığı ve kalıcı olmayan herhangi bir veri tamamen kısmi sınıflar ve yöntemler varlıkları ve veri bağlamı uygulanabilir veya ayrı sınıflarda uygulanabilir.

 İstemci ya da sunum katmanı Orta katmanın uzak arabirimdeki yöntemleri çağırır ve bu katmanda DAL sorguları veya için eşlenmiş saklı yordamlar çalıştırır <xref:System.Data.Linq.DataContext> yöntemleri. Orta katman veri istemcilere genellikle XML temsillerini varlıklar veya proxy nesneleri döndürür.

 Orta katmanda varlıkları kendi durumunu izler ve ertelenmiş yüklenmesini ve veritabanına değişiklikleri gönderme yöneten veri bağlamı tarafından oluşturulur. Bu varlıkların "eklenir" `DataContext`. Varlıkları serileştirme aracılığıyla başka bir katmana gönderildikten sonra Bununla birlikte, yani ayrılmış, haline gelmeden `DataContext` durumlarına artık izlemektir. İstemci güncelleştirmeleri geri gönderir varlıkları eklenemeyeceği, önce veri bağlamı için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanına değişiklikleri gönderebilirsiniz. İstemci, özgün değerlerine sağlamaktan sorumludur ve/veya olanlar için iyimser eşzamanlılık denetimlerinin gerekli olduğunda zaman damgaları için orta katman yedekleyin.

 ASP.NET uygulamalarında <xref:System.Web.UI.WebControls.LinqDataSource> Bu karmaşıklığı çoğunu yönetir. Daha fazla bilgi için [LinqDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Ek Kaynaklar
 Kullanan n katmanlı uygulamaları ekleme hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aşağıdaki konulara bakın:

- [ASP.NET ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)

- [Web Hizmetleri ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md) 

- [N Katmanı İş Mantığını Uygulama](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)

- [N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)

 ADO.NET veri kümeleri kullanan n katmanlı uygulamalar hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

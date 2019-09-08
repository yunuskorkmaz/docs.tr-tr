---
title: LINQ to SQL ile N Katmanı ve Uzak Uygulamalar
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 94ca057da10c3570e85e17b5caec2d86154d8a3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781409"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>LINQ to SQL ile N Katmanı ve Uzak Uygulamalar
Tarafından kullanılan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]n katmanlı veya çok katmanlı uygulamalar oluşturabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Genellikle veri bağlamı, varlık sınıfları ve sorgu oluşturma mantığı, veri erişim katmanı (dal) olarak Orta katmanda bulunur. İş mantığı ve kalıcı olmayan tüm veriler tamamen kısmi sınıflarda ve varlık yöntemlerine ve veri bağlamına uygulanabilir veya ayrı sınıflarda uygulanabilir.

 İstemci veya sunu katmanı, ortadaki katmanın uzak arabirimindeki yöntemleri çağırır ve bu katmandaki dal, <xref:System.Data.Linq.DataContext> yöntemlerle eşlenen sorguları veya saklı yordamları yürütür. Orta katman, verileri genellikle varlıkların veya proxy nesnelerinin XML gösterimleri olarak istemcilere döndürür.

 Orta katmanda varlıklar, veri bağlamı tarafından oluşturulur. Bu, durumlarını izler ve değişiklikleri veritabanına ertelenmesini ve verilerin veritabanına gönderilmesini yönetir. Bu varlıklar ' e `DataContext`"eklenir. Ancak, varlıklar, serileştirme aracılığıyla başka bir katmana gönderildikten sonra ayrılmaları, yani artık durumlarını izlememe anlamına `DataContext` gelir. İstemci güncelleştirmeler için geri gönderdiği varlıkların, değişiklikleri veritabanına gönderebilmeleri için önce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlamına yeniden eklenmesi gerekir. İstemci, iyimser eşzamanlılık denetimleri için gerekliyse orijinal değerleri ve/veya zaman damgasını Orta katmana geri sağlamaktan sorumludur.

 ASP.NET uygulamalarında, <xref:System.Web.UI.WebControls.LinqDataSource> bu karmaşıklığın çoğunu yönetir. Daha fazla bilgi için bkz. [LinqDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Ek Kaynaklar
 Kullanan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]n katmanlı uygulamaların nasıl uygulanacağı hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [ASP.NET ile LINQ to SQL N Katmanı](linq-to-sql-n-tier-with-aspnet.md)

- [Web Hizmetleri ile LINQ to SQL N Katmanı](linq-to-sql-n-tier-with-web-services.md) 

- [N Katmanı İş Mantığını Uygulama](implementing-business-logic-linq-to-sql.md)

- [N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 ADO.NET veri kümeleri kullanan n katmanlı uygulamalar hakkında daha fazla bilgi için, bkz. [n katmanlı uygulamalarda veri kümeleriyle çalışma](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)

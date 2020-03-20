---
title: LINQ to SQL ile N Katmanı ve Uzak Uygulamalar
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 6758ae23c25d8e7a4255d0a784cccd1eb404bfe7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174309"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>LINQ to SQL ile N Katmanı ve Uzak Uygulamalar
N katmanlı veya çok katmanlı uygulamalar oluşturabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Genellikle, veri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağlamı, varlık sınıfları ve sorgu yapısı mantığı, veri erişim katmanı (DAL) olarak orta katmanda yer alır. İş mantığı ve kalıcı olmayan veriler, varlıkların kısmi sınıflarında ve yöntemlerinde ve veri bağlamında tamamen uygulanabilir veya ayrı sınıflarda uygulanabilir.

 İstemci veya sunu katmanı orta katmanın uzak arabiriminde yöntemleri çağırır ve bu katmandaki DAL, <xref:System.Data.Linq.DataContext> yöntemlerle eşlenen sorguları veya depolanmış yordamları yürütecek. Orta katman, verileri genellikle varlıkların veya proxy nesnelerin XML gösterimleri olarak istemcilere döndürür.

 Orta katmanda, varlıklar durumlarını izleyen veri bağlamı tarafından oluşturulur ve veritabanındaki değişikliklerin ertelenmiş yüklemeve gönderilmesini yönetir. Bu varlıklar " bağlı" olan. `DataContext` Ancak, varlıklar serileştirme yoluyla başka bir katmana gönderildikten sonra, `DataContext` ayrılırlar, bu da durumlarının artık izlenmediği anlamına gelir. Değişikliklerin veritabanına gönderilemeden önce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] istemcinin güncelleştirmeler için geri gönderdiği varlıkların veri bağlamına yeniden eklenmesi gerekir. Müşteri, iyimser eşzamanlılık denetimleri için gerekliyse, orijinal değerleri ve/veya zaman damgalarını orta katmana geri sağlamakla yükümlüdür.

 ASP.NET uygulamalarda, <xref:System.Web.UI.WebControls.LinqDataSource> bu karmaşıklığın çoğunu yönetir. Daha fazla bilgi için [Bkz. LinqDataSource Web Sunucusu Denetimine Genel Bakış.](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))

## <a name="additional-resources"></a>Ek Kaynaklar
 N katmanı uygulamalarının nasıl uygulanacağı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [ASP.NET ile LINQ to SQL N Katmanı](linq-to-sql-n-tier-with-aspnet.md)

- [Web Hizmetleri ile LINQ to SQL N Katmanı](linq-to-sql-n-tier-with-web-services.md)

- [N Katmanı İş Mantığını Uygulama](implementing-business-logic-linq-to-sql.md)

- [N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Veri Kümeleri ADO.NET kullanan n katmanlı uygulamalar hakkında daha fazla bilgi için n [katmanlı uygulamalardaki veri kümeleriyle çalışma'ya](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)

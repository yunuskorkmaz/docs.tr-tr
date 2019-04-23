---
title: Web Hizmetleri ile LINQ to SQL N Katmanı
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: 7b13a0cd77925423a12c093b1b5ac9b63ad7e019
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107412"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>Web Hizmetleri ile LINQ to SQL N Katmanı
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle orta katman Web hizmeti gibi bir zamanı gevşek bağlanmış veri erişim katmanı (DAL) olarak kullanılmak üzere tasarlanmıştır. Sunu katmanına bir ASP.NET Web sayfası olduğu sonra kullandığınız <xref:System.Web.UI.WebControls.LinqDataSource> Web sunucu denetimi, kullanıcı arabirimi arasında veri aktarımını yönetme ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] orta katman. Sunu katmanına bir ASP.NET sayfasına değil, serileştirme ve seri durumundan çıkarma veri yönetmek için bazı ek işleri hem Orta katmanda hem de sunu katmanı yapmalısınız.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>LINQ to SQL orta katman ayarlama  
 Bir Web hizmeti veya n-katmanlı uygulamaya orta katman veri bağlamı ve varlık sınıfları içerir. El ile veya her iki SQLMetal.exe kullanarak bu sınıflar oluşturabilir veya [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] belgelerinde açıklanan başka bir yerde. Tasarım zamanında, varlık sınıfları seri hale getirilebilir yapma seçeneğiniz vardır. Daha fazla bilgi için [nasıl yapılır: Varlıkları serileştirilebilir yapmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md). Verileri iade ettiğinizde bu seri hale getirilebilir bir tür olarak ayrı bir dizi verileri seri hale kapsayan sınıflar ve proje oluşturmak için başka bir seçenektir, [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular.  
  
 Ardından almak, eklemek ve verileri güncelleştirmek için istemcilere çağıran yöntemleri ile arabirimini tanımlar. Arabirim yöntemleri kaydırma, [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular. Uzak yöntem çağrıları ve veri seri hale getirme işlemek için serileştirme mekanizması herhangi bir türden kullanabilirsiniz. Döngüsel veya çift yönlü ilişkiler gibi müşteriler ve siparişler standart Northwind nesne modelinde arasında nesne modeliniz varsa ardından onu destekleyen bir seri hale getirici kullanmalısınız olduğunu tek gereksinim olmasıdır. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> yönlü ilişkiler destekler ancak WCF Web Hizmetleri ile kullanılan XmlSerializer desteklemez. Ardından XmlSerializer kullanmayı seçerseniz, nesne modeliniz hiçbir döngüsel bir ilişki olduğundan emin olmalısınız.  
  
 Windows Communication Foundation hakkında daha fazla bilgi için bkz: [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Kısmi sınıflar ve yöntemler kullanarak, iş kuralları veya başka bir etki alanına özgü mantığı uygulamak <xref:System.Data.Linq.DataContext> ve içine yeteneklerinizi varlık sınıfları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı olayları. Daha fazla bilgi için [N katmanlı iş mantığı uygulama](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Seri hale getirilebilir türler tanımlama  
 İstemci ya da sunum katmanı, Orta katmanı alacak sınıflar için tür tanımları olması gerekir. Bu türler, varlık sınıfları kendilerini ya da yalnızca belirli alanları uzaktan iletişim için varlık sınıfları sarmalamak özel sınıflar olabilir. Her iki durumda da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nasıl bu tür tanımlarını sunu katmanı edinme hakkında tamamen unconcerned olduğu. Örneğin, sunu katmanı WCF türlerini otomatik olarak oluşturmak için kullanabilir veya bir kopyasını türlerine tanımlandığı bir DLL olabilir veya yalnızca kendi tür sürümleri tanımlayabilirsiniz.  
  
## <a name="retrieving-and-inserting-data"></a>Alma ve veri ekleme  
 Orta katman sunu katmanı verileri nasıl eriştiğini belirten bir arabirim tanımlar. Örneğin `GetProductByID(int productID)`, veya `GetCustomers()`. Orta katmanda, yöntem gövdesini yeni bir örneğini oluşturur <xref:System.Data.Linq.DataContext>, bir veya daha fazla alt tablo yönelik bir sorgu yürütür. Orta katman sonra sonuç olarak döndüren bir <xref:System.Collections.Generic.IEnumerable%601>burada `T` varlık sınıfı ya da seri hale getirme için kullanılan başka bir tür. Hiçbir zaman sunu katmanı tarafından gönderilen veya alınan sorgu değişkenleri doğrudan ya da orta katman. İki katmanda değerleri, nesneleri ve koleksiyonları somut veri değişimi. Bir koleksiyon aldıktan sonra sunu katmanı kullanabilirsiniz [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] gerekirse sorgulamak için nesneleri.  
  
 Verileri eklerken, sunu katmanı yeni bir nesne oluşturmak ve orta katmanla iletebilirsiniz ya da orta katman sağladığı değerlerine göre bir nesne oluşturmak olabilir. Genel olarak, almaya ve n katmanlı uygulamalarda veri ekleme çok 2 katmanlı uygulamalarda işleminden farklı değildir. Daha fazla bilgi için [veritabanını sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md) ve [yapma ve gönderme veri değişikliklerini](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Güncelleştirme ve silme için değişiklikleri izleme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] İyimser eşzamanlılık (RowVersions olarak da adlandırılır) zaman damgaları ve özgün değerlerine dayalı destekler. Ardından veritabanı tablolarını zaman damgaları varsa, güncelleştirme ve silme işlemleri küçük ek iş üzerinde orta katman ya da sunu katmanı gerektirir. Orijinal değerleri için iyimser eşzamanlılık denetimlerinin kullanmanız gerekirse, ancak ardından sunu katmanı bu değerleri izleme ve geri güncelleştirmeleri gerçekleştirdiğinde göndererek sorumludur. Sunu katmanı varlıklarda yapılan değişiklikler, Orta katmanda izlenmez olmasıdır. Aslında, varlık ve üzerinde yapılan son güncelleştirme özgün alınmasını genellikle gerçekleştirilir iki tamamen ayrı örnekleri tarafından <xref:System.Data.Linq.DataContext>.  
  
 Sayısı arttıkça sunu katmanı sağlar, değişiklikleri daha karmaşık bu değişiklikleri ve bunları Orta katmanla yeniden paket izlemek için olur. İletişim kuran değişiklikler için bir mekanizma tamamen kadar uygulama uygulamasıdır. Tek gereksinim olmasıdır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık denetimlerinin için gerekli olan orijinal değerleri verilmelidir.  
  
 Daha fazla bilgi için [veri alma ve CUD işlemleri (LINQ to SQL) N katmanlı uygulamalarda](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Pokud Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))

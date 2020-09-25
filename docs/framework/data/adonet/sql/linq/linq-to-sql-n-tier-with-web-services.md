---
title: Web Hizmetleri ile LINQ to SQL N Katmanı
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: dd1f756fae99fbae591b27aaefc7cc4ad7501bd6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175297"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>Web Hizmetleri ile LINQ to SQL N Katmanı

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , özellikle de Web hizmeti gibi gevşek bağlanmış bir veri erişim katmanında (DAL) Orta katmanda kullanılmak üzere tasarlanmıştır. Sunu katmanı bir ASP.NET Web sayfasındaysa, <xref:System.Web.UI.WebControls.LinqDataSource> Kullanıcı arabirimi ve orta katman arasında veri aktarımını yönetmek için Web sunucusu denetimini kullanabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Sunu katmanı bir ASP.NET sayfası değilse, hem orta katman hem de sunum katmanının, verilerin serileştirilmesi ve serisini kaldırma işini yönetmesi için bazı ek işler yapması gerekir.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Orta katmanda LINQ to SQL ayarlama  

 Bir Web hizmeti veya n katmanlı uygulamada, orta katman veri bağlamını ve varlık sınıflarını içerir. Bu sınıfları el ile veya SQLMetal.exe ya da Nesne İlişkisel Tasarımcısı kullanarak belgelerde başka bir yerde açıklandığı şekilde oluşturabilirsiniz. Tasarım zamanında, varlık sınıflarını seri hale getirilebilir hale getirme seçeneğiniz vardır. Daha fazla bilgi için bkz. [nasıl yapılır: varlıkları seri hale getirme](how-to-make-entities-serializable.md). Başka bir seçenek de, seri hale getirilecek verileri kapsülleyen ayrı bir sınıf kümesi oluşturmak ve ardından LINQ sorgularınızda veri döndürdüğünüzde bu serileştirilebilir türler için proje oluşturmaktır.  
  
 Daha sonra arabirimi, istemcilerin verileri almak, eklemek ve güncelleştirmek için çağıracağının yöntemleriyle tanımlarsınız. Arabirim yöntemleri LINQ sorgularınızı sarlar. Uzak yöntem çağrılarını ve verilerin serileştirmesini işlemek için herhangi bir tür serileştirme mekanizması kullanabilirsiniz. Tek gereksinim, nesne modelinizde standart Northwind nesne modelindeki müşteriler ve siparişler arasındaki döngüsel veya çift yönlü ilişklarınız varsa, bunu destekleyen bir serileştirici kullanmanız gerekir. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> çift yönlü ilişkileri destekler, ancak WCF olmayan Web hizmetleriyle kullanılan XmlSerializer değildir. XmlSerializer 'ı kullanmayı seçerseniz, nesne modelinizin döngüsel ilişki olmadığından emin olmanız gerekir.  
  
 Windows Communication Foundation hakkında daha fazla bilgi için bkz. [Visual Studio 'da Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 <xref:System.Data.Linq.DataContext>Çalışma zamanı olaylarına bağlamak için ve varlık sınıflarında yer alan kısmi sınıfları ve yöntemleri kullanarak iş kurallarınızı veya diğer etki alanına özgü mantığınızı uygulayın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Daha fazla bilgi için, bkz. [N katmanlı Iş mantığını uygulama](implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Serileştirilebilir türleri tanımlama  

 İstemci veya sunu katmanının, orta katmandan alacak sınıflar için tür tanımlarına sahip olması gerekir. Bu türler, varlık sınıflarının kendileri veya yalnızca belirli alanları, uzaktan iletişim için varlık sınıflarından sarmaya yönelik özel sınıflar olabilir. Herhangi bir durumda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sunum katmanının bu tür tanımlarını nasıl edindiğini tamamen ortadan kaldırmamışlar. Örneğin, sunu katmanı, türleri otomatik olarak oluşturmak için WCF kullanabilir veya bu türlerin tanımlandığı DLL 'nin bir kopyası olabilir ya da yalnızca kendi türlerin kendi sürümlerini tanımlayabilir.  
  
## <a name="retrieving-and-inserting-data"></a>Verileri alma ve ekleme  

 Orta katman, sunum katmanının verilere nasıl eriştiğini belirten bir arabirim tanımlar. Örneğin `GetProductByID(int productID)` , veya `GetCustomers()` . Orta katmanda, Yöntem gövdesi genellikle yeni bir örneğini oluşturur <xref:System.Data.Linq.DataContext> , bir veya daha fazla tablosunda bir sorgu yürütür. Daha sonra orta katman sonucu <xref:System.Collections.Generic.IEnumerable%601> , bir `T` varlık sınıfı ya da serileştirme için kullanılan başka bir tür olan olarak döndürür. Sunu katmanı hiçbir şekilde doğrudan orta katmana sorgu değişkenleri göndermez veya almaz. İki katmanda değer, nesne ve somut veri koleksiyonları değiş tokuş. Bir koleksiyon aldıktan sonra, sunum katmanı gerekirse sorgulamak için LINQ to Objects kullanabilir.  
  
 Veri eklenirken sunum katmanı yeni bir nesne oluşturabilir ve bunu Orta katmana gönderebilir ya da orta katman, sağladığı değerlere göre nesneyi oluşturabilir. Genel olarak, n katmanlı uygulamalarda veri alma ve ekleme işlemi, 2 katmanlı uygulamalardaki işlemden çok farklı değildir. Daha fazla bilgi için bkz. [Veritabanını sorgulama](querying-the-database.md) ve [veri değişikliklerini oluşturma ve gönderme](making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Güncelleştirmeler ve silmeler için değişiklikleri izleme  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , zaman damgalarına (RowVersions olarak da adlandırılır) ve özgün değerlere göre iyimser eşzamanlılık destekler. Veritabanı tablolarında zaman damgaları varsa, güncelleştirmeler ve silmeler, orta katman veya sunu katmanında çok fazla iş gerektirir. Ancak, iyimser eşzamanlılık denetimleri için özgün değerleri kullanmanız gerekiyorsa, sunu katmanı bu değerleri izlemekten ve güncelleştirme yaptığında geri göndermekten sorumludur. Bunun nedeni, sunum katmanındaki varlıklarda yapılan değişikliklerin Orta katmanda izlenmemesi nedeniyle oluşur. Aslında, bir varlığın özgün alımı ve kendisine yapılan son güncelleştirme genellikle iki ayrı farklı örnek tarafından gerçekleştirilir <xref:System.Data.Linq.DataContext> .  
  
 Sunu katmanının yaptığı değişikliklerin sayısı arttıkça, bu değişiklikleri izlemek ve ortadaki katmana geri paketlemek için de daha karmaşık hale gelir. Değişiklikleri iletişim için bir mekanizmanın uygulanması, uygulamaya tamamen yöneliktir. Tek gereksinim, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık denetimleri için gerekli olan özgün değerler verilmelidir.  
  
 Daha fazla bilgi için, bkz. [N katmanlı uygulamalarda veri alma ve CUD işlemleri (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)
- [LinqDataSource Web sunucusu denetimine genel bakış](/previous-versions/aspnet/bb547113(v=vs.100))

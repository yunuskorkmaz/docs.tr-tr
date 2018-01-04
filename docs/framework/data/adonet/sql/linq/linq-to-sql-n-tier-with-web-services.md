---
title: "LINQ-SQL N katmanlı Web Hizmetleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 37dfeec82339ed4381d158b1bd5ac442223bfe50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>LINQ-SQL N katmanlı Web Hizmetleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]özellikle orta katman bir Web hizmeti gibi birbirine sıkı şekilde bağlı veri erişim katmanı (DAL) olarak kullanılmak üzere tasarlanmıştır. Sunu katmanı bir ASP.NET Web sayfasıdır sonra kullandığınız <xref:System.Web.UI.WebControls.LinqDataSource> Web kullanıcı arabirimi arasında veri aktarımını yönetmek için sunucu denetimi ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta katmanda. Sunu katmanı ASP.NET sayfası değilse, seri hale getirme ve seri durumundan çıkarılması veri yönetmek için bazı ek iş Orta katmanda ve sunu katmanı yapmalısınız.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>LINQ-SQL orta katman ayarlama  
 Web hizmeti veya n katmanlı uygulama, orta katman veri bağlamı ve sınıflar içerir. El ile veya her iki SQLMetal.exe kullanarak bu sınıfları oluşturabilirsiniz veya [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] başka bir yerde belgelerinde açıklandığı gibi. Tasarım zamanında varlık sınıflarının seri hale getirilebilir seçeneğiniz vardır. Daha fazla bilgi için bkz: [nasıl yapılır: varlıklar serileştirilebilir olun](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md). Verileri geri döndüğünüzde verilerin serileştirilmesi için kapsülleyen sınıfları ve proje ayrı bir dizi bu seri hale getirilebilir türler oluşturmak için başka bir seçenektir, [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular.  
  
 Ardından istemcilerin almak, eklemek ve verileri güncelleştirmek için arayacağı yöntemleriyle arabirimi tanımlayın. Arabirim yöntemleri sarmalama, [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgular. Uzak yöntem çağrılarını ve veri serileştirmek işlemek için seri hale getirme mekanizmasını herhangi bir tür kullanın. Tek gereksinim, müşteriler ve standart Northwind nesne modelindeki Siparişler arasında gibi nesne modelinde döngüsel ya da çift yönlü ilişkiler varsa, daha sonra onu destekleyen bir seri hale getirici kullanmasıdır. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> destekleyen iki yönlü ilişkileri ancak WCF Web Hizmetleri ile kullanılan XmlSerializer desteklemez. Ardından XmlSerializer kullanmayı seçerseniz, nesne modeli hiçbir döngüsel ilişki sahip olduğundan emin olmalısınız.  
  
 Windows Communication Foundation hakkında daha fazla bilgi için bkz: [Windows Communication Foundation Hizmetleri ve Visual Studio'da WCF Veri Hizmetleri](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Kısmi sınıflar ve yöntemler kullanarak, iş kurallarını veya diğer etki alanına özgü mantığı uygulamak <xref:System.Data.Linq.DataContext> ve uygulamasına olanak sınıflar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı olayları. Daha fazla bilgi için bkz: [N katmanlı iş mantığı uygulama](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Seri hale getirilebilir türleri tanımlama  
 İstemci veya sunu katmanı orta katmandan alabilmesi sınıfları için tür tanımları olması gerekir. Bu türlerde varlık sınıfları kendilerini ya da yalnızca belirli alanlar uzaktan iletişim için varlık sınıflardan sarmalamak özel sınıfları olabilir. Her iki durumda da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sunu katmanı bu tür tanımları nasıl edinme hakkında tamamen unconcerned değil. Örneğin, sunu katmanı türleri otomatik olarak oluşturmak için WCF kullanabilir veya bu türlerinin tanımlı olduğu DLL bir kopyasına sahip veya yalnızca kendi türlerinin sürümlerini tanımlayabilirsiniz.  
  
## <a name="retrieving-and-inserting-data"></a>Alma ve veri ekleme  
 Orta katman nasıl sunu katmanı verilere erişen belirten bir arabirim tanımlar. Örneğin `GetProductByID(int productID)`, veya `GetCustomers()`. Orta katmanda yöntem gövdesi yeni bir örneğini oluşturur <xref:System.Data.Linq.DataContext>, bir veya daha fazla, tablodaki bir sorgu yürütür. Orta katman sonra sonuç olarak döndüren bir <xref:System.Collections.Generic.IEnumerable%601>, burada `T` bir varlık sınıfı ya da serileştirme için kullanılan başka bir tür. Sunu katmanı hiçbir zaman gönderir veya sorgu değişkenleri doğrudan veya orta katman alır. İki katmanı değerleri, nesneleri ve koleksiyonları somut veri değişimi. Bir koleksiyon aldıktan sonra sunu katmanı kullanabilirsiniz [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] gerekirse sorgu nesnelere.  
  
 Veri eklerken, sunu katmanı yeni bir nesne oluşturmak ve orta katman iletebilirsiniz veya sağladığı değerlerine göre bir nesne oluşturmak orta katman sağlayabilirsiniz. Genel olarak, alma ve n katmanlı uygulamalarda veri ekleme çok 2 katmanlı uygulamalarda işleminden farklı. Daha fazla bilgi için bkz: [veritabanını sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md) ve [alma ve gönderme veri değişikliklerini](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Güncelleştirmeleri ve silme için değişiklikleri izleme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zaman damgaları (RowVersions olarak da adlandırılır) ve özgün değerlerine dayalı iyimser eşzamanlılık destekler. Ardından veritabanı tablolarını zaman damgaları varsa, güncelleştirmeleri ve silme işlemleri orta katman veya sunu katmanı üzerinde çok az ek iş gerektirir. İyimser eşzamanlılık denetimleri için özgün değerleri kullanmanız gerekiyorsa, ancak ardından sunu katmanı bu değerleri izleme ve geri güncelleştirmeleri yaptığında göndererek sorumludur. Sunu katmanı üzerinde varlıklar için yapılan değişiklikler Orta katmanda izlenmez olmasıdır. Aslında, bir varlık ve üzerinde yapılan son güncelleştirme özgün alınmasını genellikle gerçekleştirilir iki tamamen ayrı ayrı örnekleri tarafından <xref:System.Data.Linq.DataContext>.  
  
 Sayısı arttıkça sunu katmanı yaptığı değişiklikler bu değişiklikler ve orta katman geri paket izlemek için hale karmaşık. İletişim kuran değişiklikleri için bir mekanizma tamamen kadar uygulama uygulamasıdır. Tek gereksinim olan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık denetimleri için gerekli olan özgün değerlere verilmelidir.  
  
 Daha fazla bilgi için bkz: [veri alımı ve N katmanlı uygulamalar (LINQ-SQL) CUD işlemlerinde](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [NIB: LinqDataSource Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)

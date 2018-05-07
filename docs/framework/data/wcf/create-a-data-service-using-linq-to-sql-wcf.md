---
title: 'Nasıl yapılır: bir LINQ SQL veri kaynağı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 5769ff5296d096df41b59104ad0581f0e816c648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Nasıl yapılır: bir LINQ SQL veri kaynağı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] varlık verilerini veri hizmet olarak sunar. Üye sunan herhangi bir sınıf üzerinde dayalı bir veri modeli tanımlamak için bu iade yansıma sağlayıcı sağlar bir <xref:System.Linq.IQueryable%601> uygulaması. Veri kaynağındaki güncelleştirmeler yapmak için bu sınıfları ayrıca uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi. Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Bu konu LINQ Northwind örnek veritabanı yansıtma sağlayıcı kullanarak erişim SQL sınıfları için oluşturma yanı sıra, bu veri sınıflara göre veri hizmetin nasıl oluşturulacağını gösterir.  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a>LINQ SQL sınıfları bir proje eklemek için  
  
1.  Gelen bir Visual Basic veya C# uygulamadaki üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.  
  
2.  Tıklatın **LINQ'ten SQL'e sınıflarını** şablonu.  
  
3.  Adına değiştirme **Northwind.dbml**.  
  
4.  **Ekle**'yi tıklatın.  
  
     Northwind.dbml dosyası projeye eklenir ve Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) açar.  
  
5.  İçinde **Server**/**Database Explorer**, Northwind altında genişletin **tabloları** ve sürükleyin `Customers` Nesne İlişkisel Tasarımcısı (O/R üzerine tablo Tasarımcı).  
  
     A `Customer` varlık sınıfı oluşturulur ve tasarım yüzeyine görünür.  
  
6.  Yineleme adım 6 için `Orders`, `Order_Details`, ve `Products` tabloları.  
  
7.  LINQ SQL sınıfları ve seçeneğini temsil eden yeni .dbml dosyasını sağ tıklatın **görünümü kodu**.  
  
     Bu devraldığı sınıfı için bir parçalı sınıf tanımını içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur <xref:System.Data.Linq.DataContext> bu durumda sınıfı `NorthwindDataContext`.  
  
8.  Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod genişleterek yansıma sağlayıcı uygulayan <xref:System.Data.Linq.DataContext> ve LINQ-SQL tarafından oluşturulan veri sınıfları:  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>SQL tabanlı veri modeli için bir LINQ kullanarak bir veri hizmeti oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ASP.NET proje adına sağ tıklayın ve ardından **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.  
  
3.  Hizmet için bir ad sağlayın ve ardından **Tamam**.  
  
     Visual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur. Varsayılan olarak Kod Düzenleyicisi penceresini açar.  
  
4.  Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` , varlık kapsayıcısının veri modelinin türü olan veri hizmeti tanımlayan sınıf tanımında bu durumda olduğu `NorthwindDataContext`.  
  
5.  Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     Bu, üç belirtilen varlık kümeleri için kaynaklara erişmek yetkili istemcilerin sağlar.  
  
6.  Northwind.svc veri hizmeti bir Web tarayıcısı kullanarak test etmek için konudaki yönergeleri [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

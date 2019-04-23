---
title: 'Nasıl yapılır: LINQ to SQL veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: b33eb8f470fc8ce3851c7843de992b39e86ce018
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59518226"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Nasıl yapılır: LINQ to SQL veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma

WCF Veri Hizmetleri, varlık verilerini bir veri hizmeti kullanıma sunar. Yansıma sağlayıcısı döndüren üyeleri ortaya koyar herhangi bir sınıfın alan bir veri modeli tanımlamanızı sağlayan bir <xref:System.Linq.IQueryable%601> uygulaması. Veri kaynağındaki güncelleştirmeler yapmak için bu sınıflar da uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi. Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Bu konu LINQ to SQL sınıfları, yansıma sağlayıcısını kullanarak Northwind örnek veritabanına erişim oluşturma yanı sıra, bu veri sınıflara göre veri hizmeti oluşturulacağını gösterir.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>LINQ to SQL sınıfları bir projeye eklemek için

1. Gelen bir Visual Basic veya C# uygulamasından üzerinde **proje** menüsünde tıklatın **Ekle** > **yeni öğe**.

2. Tıklayın **LINQ to SQL sınıfları** şablonu.

3. Adla değiştirin **Northwind.dbml**.

4. **Ekle**'yi tıklatın.

     Northwind.dbml dosyası projenize eklenir ve Object Relational Designer (O/R Tasarımcısı) açar.

5. İçinde **sunucu**/**veritabanı Gezgini**, Northwind altında genişletin **tabloları** sürükleyin `Customers` Object Relational Designer (O/R üzerine tablo Tasarımcı).

     A `Customer` varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür.

6. Yineleme adım 6 için `Orders`, `Order_Details`, ve `Products` tablolar.

7. LINQ SQL sınıfları ve seçeneğini temsil eden yeni bir .dbml dosyası sağ **kodu görüntüle**.

     Bu devralınan sınıf için bir parçalı sınıf tanımını içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur <xref:System.Data.Linq.DataContext> bu durumda olan sınıf `NorthwindDataContext`.

8. Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod genişleterek yansıma sağlayıcısı uygulayan <xref:System.Data.Linq.DataContext> ve LINQ to SQL tarafından oluşturulan veri sınıfları:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Bir LINQ to SQL tabanlı veri modelini kullanarak bir veri hizmeti oluşturmak için

1. İçinde **Çözüm Gezgini**ASP.NET projenizin adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti** şablondan **Web** kategorisi.

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.

3. Hizmet için bir ad sağlayın ve ardından **Tamam**.

     Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur. Varsayılan olarak, kod düzenleyicisi penceresi açılır.

4. Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` veri modelinin varlık kapsayıcı türü olan veri hizmeti tanımlayan sınıf tanımında, bu durumda olduğu `NorthwindDataContext`.

5. Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     Bu üç belirtilen varlık kümesi için kaynaklara erişmeye yetkili istemcilere sağlar.

6. Bir Web tarayıcısı kullanarak Northwind.svc veri hizmeti test etmek için konusundaki yönergeleri izleyin. [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir ADO.NET varlık çerçevesi veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
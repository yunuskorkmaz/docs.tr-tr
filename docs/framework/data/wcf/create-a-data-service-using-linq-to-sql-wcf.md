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
ms.openlocfilehash: e65d9dc48f128d7808f0731057ec0a5e52e65444
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798485"
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

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]

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

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]

     Bu üç belirtilen varlık kümesi için kaynaklara erişmeye yetkili istemcilere sağlar.

6. Bir Web tarayıcısı kullanarak Northwind.svc veri hizmeti test etmek için konusundaki yönergeleri izleyin. [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
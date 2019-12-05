---
title: 'Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: cde5b9903a1fd164ce106a6a408ac4bb79976642
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802287"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, veri hizmeti olarak varlık verilerini gösterir. Yansıma sağlayıcısı, bir <xref:System.Linq.IQueryable%601> uygulamasını döndüren üyeleri kullanıma sunan herhangi bir sınıfa dayalı bir veri modeli tanımlamanızı sağlar. Veri kaynağındaki verilerde güncelleştirme yapabilmek için, bu sınıfların de <xref:System.Data.Services.IUpdatable> arabirimini uygulaması gerekir. Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md). Bu konu başlığı altında, yansıma sağlayıcısını kullanarak Northwind örnek veritabanına erişen LINQ to SQL sınıfları oluşturma ve bu veri sınıflarını temel alan veri hizmetini oluşturma işlemi gösterilmektedir.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Bir projeye LINQ to SQL sınıfları eklemek için

1. Visual Basic C# veya uygulamanın Içinden, **proje** menüsünde Yeni > **öğe** **Ekle** ' ye tıklayın.

2. **LINQ to SQL sınıfları** şablonuna tıklayın.

3. Adı **Northwind. dbml**olarak değiştirin.

4. **Ekle**'yi tıklatın.

     Northwind. dbml dosyası projeye eklenir ve Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.

5. **Sunucu**/**veritabanı Gezgini**, Northwind altında **tablolar** ' ı genişletin ve `Customers` tablosunu nesne ilişkisel Tasarımcısı (O/R Designer) üzerine sürükleyin.

     `Customer` bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görüntülenir.

6. `Orders`, `Order_Details`ve `Products` tabloları için 6. adımı yineleyin.

7. LINQ to SQL sınıfları temsil eden New. dbml dosyasına sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

     Bu, <xref:System.Data.Linq.DataContext> sınıfından devralan sınıf için kısmi bir sınıf tanımı içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur ve bu durumda `NorthwindDataContext`.

8. Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod, LINQ to SQL tarafından oluşturulan <xref:System.Data.Linq.DataContext> ve veri sınıflarını genişleterek yansıma sağlayıcısını uygular:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>LINQ to SQL tabanlı bir veri modeli kullanarak veri hizmeti oluşturmak için

1. **Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' ye tıklayın.

2. **Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisinden **WCF veri hizmeti** şablonunu seçin.

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.

3. Hizmet için bir ad sağlayın ve ardından **Tamam**' a tıklayın.

     Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur. Varsayılan olarak, kod Düzenleyicisi penceresi açılır.

4. Veri Hizmeti kodunda, veri hizmetinin varlık kapsayıcısı olan tür ile veri hizmetini tanımlayan sınıfın tanımındaki açıklama `/* TODO: put your data source class name here */` değiştirin. Bu durumda, `NorthwindDataContext`.

5. Veri Hizmeti kodunda, `InitializeService` işlevindeki yer tutucu kodunu aşağıdaki gibi değiştirin:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     Bu, yetkili istemcilerin belirtilen üç varlık kümesi için kaynaklara erişmesini sağlar.

6. Northwind. svc veri hizmetini bir Web tarayıcısı kullanarak test etmek için [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)konusundaki yönergeleri izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-rp-wcf-data-services.md)
- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)

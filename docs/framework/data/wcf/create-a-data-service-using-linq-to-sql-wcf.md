---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 18c59cc8a067372f2a5c5b4b25d9aec77515ad98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766250"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri, veri hizmeti olarak varlık verilerini gösterir. Yansıma sağlayıcısı, bir uygulamayı döndüren üyeleri sunan herhangi bir sınıfa dayalı bir veri modeli tanımlamanızı sağlar <xref:System.Linq.IQueryable%601> . Veri kaynağındaki verilerde güncelleştirme yapabilmek için, bu sınıfların de arabirimini uygulaması gerekir <xref:System.Data.Services.IUpdatable> . Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md). Bu konu başlığı altında, yansıma sağlayıcısını kullanarak Northwind örnek veritabanına erişen LINQ to SQL sınıfları oluşturma ve bu veri sınıflarını temel alan veri hizmetini oluşturma işlemi gösterilmektedir.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Bir projeye LINQ to SQL sınıfları eklemek için

1. Visual Basic veya C# uygulamasının içinden, **Proje** menüsünde   >  **Yeni öğe** Ekle ' ye tıklayın.

2. **LINQ to SQL sınıfları** şablonuna tıklayın.

3. Adı **Northwind. dbml** olarak değiştirin.

4. **Ekle**'ye tıklayın.

     Northwind. dbml dosyası projeye eklenir ve Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.

5. **Sunucu** / **veritabanı Gezgini**' de, Northwind altında **Tablolar** ' ı genişletin ve `Customers` tabloyu nesne ilişkisel Tasarımcısı (O/R Designer) üzerine sürükleyin.

     Bir `Customer` varlık sınıfı oluşturulur ve tasarım yüzeyinde görüntülenir.

6. `Orders`, `Order_Details` Ve tabloları için 6. adımı yineleyin `Products` .

7. LINQ to SQL sınıfları temsil eden New. dbml dosyasına sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

     Bu, <xref:System.Data.Linq.DataContext> Bu örnekte olduğu sınıfından devralan sınıf için kısmi bir sınıf tanımı içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur `NorthwindDataContext` .

8. Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod, <xref:System.Data.Linq.DataContext> LINQ to SQL tarafından oluşturulan ve veri sınıflarını genişleterek yansıma sağlayıcısını uygular:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>LINQ to SQL tabanlı bir veri modeli kullanarak veri hizmeti oluşturmak için

1. **Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' ye tıklayın.

2. **Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisinden **WCF veri hizmeti** şablonunu seçin.

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.

3. Hizmet için bir ad sağlayın ve ardından **Tamam**' a tıklayın.

     Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur. Varsayılan olarak, kod Düzenleyicisi penceresi açılır.

4. Veri Hizmeti kodunda, veri `/* TODO: put your data source class name here */` hizmetini tanımlayan sınıfın tanımındaki, bu örnekte olduğu gibi veri modelinin varlık kapsayıcısı olan türde olan açıklamayı değiştirin `NorthwindDataContext` .

5. Veri Hizmeti kodunda, işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin `InitializeService` :

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     Bu, yetkili istemcilerin belirtilen üç varlık kümesi için kaynaklara erişmesini sağlar.

6. Northwind. svc veri hizmetini bir Web tarayıcısı kullanarak test etmek için [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)konusundaki yönergeleri izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-rp-wcf-data-services.md)
- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)

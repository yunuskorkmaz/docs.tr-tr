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
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="d66ed-102">Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="d66ed-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="d66ed-103">WCF Veri Hizmetleri, veri hizmeti olarak varlık verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d66ed-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="d66ed-104">Yansıma sağlayıcısı, bir <xref:System.Linq.IQueryable%601> uygulamasını döndüren üyeleri kullanıma sunan herhangi bir sınıfa dayalı bir veri modeli tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d66ed-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="d66ed-105">Veri kaynağındaki verilerde güncelleştirme yapabilmek için, bu sınıfların de <xref:System.Data.Services.IUpdatable> arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d66ed-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="d66ed-106">Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d66ed-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="d66ed-107">Bu konu başlığı altında, yansıma sağlayıcısını kullanarak Northwind örnek veritabanına erişen LINQ to SQL sınıfları oluşturma ve bu veri sınıflarını temel alan veri hizmetini oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d66ed-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="d66ed-108">Bir projeye LINQ to SQL sınıfları eklemek için</span><span class="sxs-lookup"><span data-stu-id="d66ed-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="d66ed-109">Visual Basic C# veya uygulamanın Içinden, **proje** menüsünde Yeni > **öğe** **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d66ed-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d66ed-110">**LINQ to SQL sınıfları** şablonuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d66ed-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="d66ed-111">Adı **Northwind. dbml**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d66ed-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="d66ed-112">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d66ed-112">Click **Add**.</span></span>

     <span data-ttu-id="d66ed-113">Northwind. dbml dosyası projeye eklenir ve Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.</span><span class="sxs-lookup"><span data-stu-id="d66ed-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="d66ed-114">**Sunucu**/**veritabanı Gezgini**, Northwind altında **tablolar** ' ı genişletin ve `Customers` tablosunu nesne ilişkisel Tasarımcısı (O/R Designer) üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="d66ed-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="d66ed-115">`Customer` bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d66ed-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="d66ed-116">`Orders`, `Order_Details`ve `Products` tabloları için 6. adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="d66ed-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="d66ed-117">LINQ to SQL sınıfları temsil eden New. dbml dosyasına sağ tıklayın ve **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d66ed-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="d66ed-118">Bu, <xref:System.Data.Linq.DataContext> sınıfından devralan sınıf için kısmi bir sınıf tanımı içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur ve bu durumda `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d66ed-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="d66ed-119">Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d66ed-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="d66ed-120">Bu kod, LINQ to SQL tarafından oluşturulan <xref:System.Data.Linq.DataContext> ve veri sınıflarını genişleterek yansıma sağlayıcısını uygular:</span><span class="sxs-lookup"><span data-stu-id="d66ed-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="d66ed-121">LINQ to SQL tabanlı bir veri modeli kullanarak veri hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d66ed-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="d66ed-122">**Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d66ed-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d66ed-123">**Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisinden **WCF veri hizmeti** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d66ed-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="d66ed-125">**WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d66ed-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="d66ed-126">Hizmet için bir ad sağlayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d66ed-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="d66ed-127">Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d66ed-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="d66ed-128">Varsayılan olarak, kod Düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="d66ed-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="d66ed-129">Veri Hizmeti kodunda, veri hizmetinin varlık kapsayıcısı olan tür ile veri hizmetini tanımlayan sınıfın tanımındaki açıklama `/* TODO: put your data source class name here */` değiştirin. Bu durumda, `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d66ed-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="d66ed-130">Veri Hizmeti kodunda, `InitializeService` işlevindeki yer tutucu kodunu aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d66ed-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="d66ed-131">Bu, yetkili istemcilerin belirtilen üç varlık kümesi için kaynaklara erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d66ed-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="d66ed-132">Northwind. svc veri hizmetini bir Web tarayıcısı kullanarak test etmek için [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d66ed-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d66ed-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d66ed-133">See also</span></span>

- [<span data-ttu-id="d66ed-134">Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d66ed-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="d66ed-135">Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d66ed-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="d66ed-136">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="d66ed-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

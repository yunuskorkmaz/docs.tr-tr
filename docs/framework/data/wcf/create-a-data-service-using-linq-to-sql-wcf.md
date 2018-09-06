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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866838"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="a5599-102">Nasıl yapılır: LINQ to SQL veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5599-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="a5599-103">WCF Veri Hizmetleri, varlık verilerini bir veri hizmeti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a5599-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="a5599-104">Yansıma sağlayıcısı döndüren üyeleri ortaya koyar herhangi bir sınıfın alan bir veri modeli tanımlamanızı sağlayan bir <xref:System.Linq.IQueryable%601> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a5599-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="a5599-105">Veri kaynağındaki güncelleştirmeler yapmak için bu sınıflar da uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a5599-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="a5599-106">Daha fazla bilgi için [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5599-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="a5599-107">Bu konu LINQ to SQL sınıfları, yansıma sağlayıcısını kullanarak Northwind örnek veritabanına erişim oluşturma yanı sıra, bu veri sınıflara göre veri hizmeti oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5599-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="a5599-108">LINQ to SQL sınıfları bir projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="a5599-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="a5599-109">Gelen bir Visual Basic veya C# uygulamasından üzerinde **proje** menüsünde tıklatın **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="a5599-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="a5599-110">Tıklayın **LINQ to SQL sınıfları** şablonu.</span><span class="sxs-lookup"><span data-stu-id="a5599-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="a5599-111">Adla değiştirin **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="a5599-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="a5599-112">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a5599-112">Click **Add**.</span></span>

     <span data-ttu-id="a5599-113">Northwind.dbml dosyası projenize eklenir ve Object Relational Designer (O/R Tasarımcısı) açar.</span><span class="sxs-lookup"><span data-stu-id="a5599-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="a5599-114">İçinde **sunucu**/**veritabanı Gezgini**, Northwind altında genişletin **tabloları** sürükleyin `Customers` Object Relational Designer (O/R üzerine tablo Tasarımcı).</span><span class="sxs-lookup"><span data-stu-id="a5599-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="a5599-115">A `Customer` varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür.</span><span class="sxs-lookup"><span data-stu-id="a5599-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="a5599-116">Yineleme adım 6 için `Orders`, `Order_Details`, ve `Products` tablolar.</span><span class="sxs-lookup"><span data-stu-id="a5599-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="a5599-117">LINQ SQL sınıfları ve seçeneğini temsil eden yeni bir .dbml dosyası sağ **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="a5599-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="a5599-118">Bu devralınan sınıf için bir parçalı sınıf tanımını içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur <xref:System.Data.Linq.DataContext> bu durumda olan sınıf `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="a5599-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="a5599-119">Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a5599-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="a5599-120">Bu kod genişleterek yansıma sağlayıcısı uygulayan <xref:System.Data.Linq.DataContext> ve LINQ to SQL tarafından oluşturulan veri sınıfları:</span><span class="sxs-lookup"><span data-stu-id="a5599-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="a5599-121">Bir LINQ to SQL tabanlı veri modelini kullanarak bir veri hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a5599-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="a5599-122">İçinde **Çözüm Gezgini**ASP.NET projenizin adına sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="a5599-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="a5599-123">İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti** şablondan **Web** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="a5599-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="a5599-125">**WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.</span><span class="sxs-lookup"><span data-stu-id="a5599-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="a5599-126">Hizmet için bir ad sağlayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a5599-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="a5599-127">Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5599-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="a5599-128">Varsayılan olarak, kod düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="a5599-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="a5599-129">Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` veri modelinin varlık kapsayıcı türü olan veri hizmeti tanımlayan sınıf tanımında, bu durumda olduğu `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="a5599-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="a5599-130">Veri Hizmeti için kodda yer tutucusunu değiştirin `InitializeService` işlevi aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="a5599-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="a5599-131">Bu üç belirtilen varlık kümesi için kaynaklara erişmeye yetkili istemcilere sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5599-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="a5599-132">Bir Web tarayıcısı kullanarak Northwind.svc veri hizmeti test etmek için konusundaki yönergeleri izleyin. [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="a5599-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5599-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5599-133">See Also</span></span>

- [<span data-ttu-id="a5599-134">Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5599-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="a5599-135">Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5599-135">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="a5599-136">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a5599-136">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
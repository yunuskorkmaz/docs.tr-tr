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
ms.locfileid: "33362253"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="01a7b-102">Nasıl yapılır: bir LINQ SQL veri kaynağı (WCF Veri Hizmetleri) kullanarak bir veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a7b-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="01a7b-103"> varlık verilerini veri hizmet olarak sunar.</span><span class="sxs-lookup"><span data-stu-id="01a7b-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="01a7b-104">Üye sunan herhangi bir sınıf üzerinde dayalı bir veri modeli tanımlamak için bu iade yansıma sağlayıcı sağlar bir <xref:System.Linq.IQueryable%601> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="01a7b-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="01a7b-105">Veri kaynağındaki güncelleştirmeler yapmak için bu sınıfları ayrıca uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="01a7b-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="01a7b-106">Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="01a7b-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="01a7b-107">Bu konu LINQ Northwind örnek veritabanı yansıtma sağlayıcı kullanarak erişim SQL sınıfları için oluşturma yanı sıra, bu veri sınıflara göre veri hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="01a7b-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="01a7b-108">LINQ SQL sınıfları bir proje eklemek için</span><span class="sxs-lookup"><span data-stu-id="01a7b-108">To add LINQ to SQL classes to a project</span></span>  
  
1.  <span data-ttu-id="01a7b-109">Gelen bir Visual Basic veya C# uygulamadaki üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="01a7b-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="01a7b-110">Tıklatın **LINQ'ten SQL'e sınıflarını** şablonu.</span><span class="sxs-lookup"><span data-stu-id="01a7b-110">Click the **LINQ to SQL Classes** template.</span></span>  
  
3.  <span data-ttu-id="01a7b-111">Adına değiştirme **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="01a7b-111">Change the name to **Northwind.dbml**.</span></span>  
  
4.  <span data-ttu-id="01a7b-112">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="01a7b-112">Click **Add**.</span></span>  
  
     <span data-ttu-id="01a7b-113">Northwind.dbml dosyası projeye eklenir ve Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) açar.</span><span class="sxs-lookup"><span data-stu-id="01a7b-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>  
  
5.  <span data-ttu-id="01a7b-114">İçinde **Server**/**Database Explorer**, Northwind altında genişletin **tabloları** ve sürükleyin `Customers` Nesne İlişkisel Tasarımcısı (O/R üzerine tablo Tasarımcı).</span><span class="sxs-lookup"><span data-stu-id="01a7b-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>  
  
     <span data-ttu-id="01a7b-115">A `Customer` varlık sınıfı oluşturulur ve tasarım yüzeyine görünür.</span><span class="sxs-lookup"><span data-stu-id="01a7b-115">A `Customer` entity class is created and appears on the design surface.</span></span>  
  
6.  <span data-ttu-id="01a7b-116">Yineleme adım 6 için `Orders`, `Order_Details`, ve `Products` tabloları.</span><span class="sxs-lookup"><span data-stu-id="01a7b-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>  
  
7.  <span data-ttu-id="01a7b-117">LINQ SQL sınıfları ve seçeneğini temsil eden yeni .dbml dosyasını sağ tıklatın **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="01a7b-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>  
  
     <span data-ttu-id="01a7b-118">Bu devraldığı sınıfı için bir parçalı sınıf tanımını içeren Northwind.cs adlı yeni bir arka plan kod sayfası oluşturur <xref:System.Data.Linq.DataContext> bu durumda sınıfı `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="01a7b-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>  
  
8.  <span data-ttu-id="01a7b-119">Northwind.cs kod dosyasının içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="01a7b-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="01a7b-120">Bu kod genişleterek yansıma sağlayıcı uygulayan <xref:System.Data.Linq.DataContext> ve LINQ-SQL tarafından oluşturulan veri sınıfları:</span><span class="sxs-lookup"><span data-stu-id="01a7b-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="01a7b-121">SQL tabanlı veri modeli için bir LINQ kullanarak bir veri hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="01a7b-121">To create a data service by using a LINQ to SQL-based data model</span></span>  
  
1.  <span data-ttu-id="01a7b-122">İçinde **Çözüm Gezgini**, ASP.NET proje adına sağ tıklayın ve ardından **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="01a7b-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="01a7b-123">İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="01a7b-123">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="01a7b-124">Hizmet için bir ad sağlayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="01a7b-124">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="01a7b-125">Visual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01a7b-125">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="01a7b-126">Varsayılan olarak Kod Düzenleyicisi penceresini açar.</span><span class="sxs-lookup"><span data-stu-id="01a7b-126">By default, the code-editor window opens.</span></span>  
  
4.  <span data-ttu-id="01a7b-127">Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` , varlık kapsayıcısının veri modelinin türü olan veri hizmeti tanımlayan sınıf tanımında bu durumda olduğu `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="01a7b-127">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>  
  
5.  <span data-ttu-id="01a7b-128">Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:</span><span class="sxs-lookup"><span data-stu-id="01a7b-128">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     <span data-ttu-id="01a7b-129">Bu, üç belirtilen varlık kümeleri için kaynaklara erişmek yetkili istemcilerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a7b-129">This enables authorized clients to access resources for the three specified entity sets.</span></span>  
  
6.  <span data-ttu-id="01a7b-130">Northwind.svc veri hizmeti bir Web tarayıcısı kullanarak test etmek için konudaki yönergeleri [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="01a7b-130">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a7b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01a7b-131">See Also</span></span>  
 [<span data-ttu-id="01a7b-132">Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a7b-132">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [<span data-ttu-id="01a7b-133">Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a7b-133">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="01a7b-134">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="01a7b-134">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

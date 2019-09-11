---
title: 'Nasıl yapılır: Bir ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 1d3c3628a32439d4847505e234b12b084b47ba3d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854128"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="7dd57-102">Nasıl yapılır: Bir ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="7dd57-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="7dd57-103">WCF Veri Hizmetleri, veri hizmeti olarak varlık verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7dd57-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="7dd57-104">Veri kaynağı ilişkisel bir veritabanı olduğunda, bu varlık verileri ADO. NETEntity Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7dd57-104">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="7dd57-105">Bu konu başlığı altında, var olan bir veritabanını temel alan Visual Studio Web uygulamasında Entity Framework tabanlı bir veri modeli oluşturma ve bu veri modelini kullanarak yeni bir veri hizmeti oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7dd57-105">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="7dd57-106">Entity Framework Ayrıca, Visual Studio projesi dışında bir Entity Framework modeli oluşturabilen bir komut satırı aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dd57-106">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="7dd57-107">Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)oluşturmak Için EdmGen. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="7dd57-108">Var olan bir veritabanını varolan bir Web uygulamasına dayalı bir Entity Framework modeli eklemek için</span><span class="sxs-lookup"><span data-stu-id="7dd57-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="7dd57-109">**Proje** menüsünde**Yeni öğe** **Ekle** > ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7dd57-110">**Şablonlar** bölmesinde, **veri** kategorisine ve sonra **ADO.net varlık veri modeli**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="7dd57-111">Model adını girip **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="7dd57-112">Varlık Veri Modeli sihirbazının ilk sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7dd57-112">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="7dd57-113">**Model Içeriğini seçin** iletişim kutusunda, **veritabanından oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="7dd57-114">Sonra **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-114">Then click **Next**.</span></span>

5. <span data-ttu-id="7dd57-115">**Yeni bağlantı** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="7dd57-116">**Bağlantı özellikleri** iletişim kutusunda sunucu adınızı yazın, kimlik doğrulama yöntemini seçin, veritabanı adını yazın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="7dd57-117">**Veri bağlantınızı seçin** iletişim kutusu, veritabanı bağlantı ayarlarınızla güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7dd57-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="7dd57-118">**App. config dosyasındaki varlık bağlantısı ayarlarını kaydet:** onay kutusunun işaretli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7dd57-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="7dd57-119">Sonra **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-119">Then click **Next**.</span></span>

8. <span data-ttu-id="7dd57-120">**Veritabanı nesnelerinizi seçin** iletişim kutusunda, veri hizmetinde kullanıma sunmayı planladığınız tüm veritabanı nesnelerini seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7dd57-121">Veri modeline eklenen nesneler veri hizmeti tarafından otomatik olarak gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="7dd57-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="7dd57-122">Bunlar, hizmetin kendisi tarafından açıkça gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7dd57-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="7dd57-123">Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7dd57-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="7dd57-124">Sihirbazı tamamladığınızda **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="7dd57-125">Bu, belirli bir veritabanını temel alan varsayılan bir veri modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7dd57-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="7dd57-126">Entity Framework veri modelini özelleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dd57-126">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="7dd57-127">Daha fazla bilgi için bkz. [varlık veri modeli araçları görevleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7dd57-127">For more information, see [Entity Data Model Tools Tasks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="7dd57-128">Yeni veri modelini kullanarak veri hizmetini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7dd57-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="7dd57-129">Visual Studio 'da, veri modelini temsil eden. edmx dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="7dd57-130">**Model tarayıcısında**modele sağ tıklayın, **Özellikler**' e tıklayın ve ardından varlık kapsayıcısının adını aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="7dd57-131">**Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="7dd57-132">**Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisindeki **WCF veri hizmeti** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="7dd57-134">**WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7dd57-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="7dd57-135">Hizmet için bir ad sağlayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd57-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="7dd57-136">Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7dd57-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7dd57-137">Varsayılan olarak, kod Düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="7dd57-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="7dd57-138">Veri Hizmeti kodunda, veri hizmetinin `/* TODO: put your data source class name here */` <xref:System.Data.Objects.ObjectContext> sınıfından devralan ve veri modelinin varlık kapsayıcısı olan ve adım 2 ' de belirtilen tür ile veri hizmetini tanımlayan sınıfın tanımındaki açıklamasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="7dd57-139">Veri Hizmeti kodunda, yetkili istemcilerin veri hizmetinin sunduğu varlık kümelerine erişmesine izin vermek için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="7dd57-140">Daha fazla bilgi için bkz. [veri hizmeti oluşturma](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="7dd57-140">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="7dd57-141">Northwind. svc veri hizmetini bir Web tarayıcısı kullanarak test etmek için [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7dd57-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd57-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd57-142">See also</span></span>

- [<span data-ttu-id="7dd57-143">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7dd57-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="7dd57-144">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="7dd57-144">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="7dd57-145">Nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="7dd57-145">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="7dd57-146">Nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="7dd57-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)

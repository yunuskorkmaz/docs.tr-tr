---
title: 'Nasıl yapılır: ADO.NET varlık çerçevesi veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 72439596ec6dc6c42024ed38116ba0026922154c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137362"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="1b7b1-102">Nasıl yapılır: ADO.NET varlık çerçevesi veri kaynağı (WCF Veri Hizmetleri) kullanarak veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b7b1-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="1b7b1-103">WCF Veri Hizmetleri, varlık verilerini bir veri hizmeti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="1b7b1-104">Bu varlık verilerini tarafından sağlanan [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] veri kaynağı, ilişkisel bir veritabanı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="1b7b1-105">Bu konu nasıl oluşturulacağını gösterir bir [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-tabanlı veri modeli varolan bir veritabanını temel alan ve yeni bir veri hizmeti oluşturmak için bu veri modeli kullanan bir Visual Studio Web uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="1b7b1-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Oluşturabilen bir komut satırı aracı da sağlar bir [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Visual Studio Proje dışındaki model.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a Visual Studio project.</span></span> <span data-ttu-id="1b7b1-107">Daha fazla bilgi için [nasıl yapılır: kullanımı Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="1b7b1-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="1b7b1-108">Mevcut bir Web uygulaması için varolan bir veritabanını temel alan bir Entity Framework modelini eklemek için</span><span class="sxs-lookup"><span data-stu-id="1b7b1-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="1b7b1-109">Üzerinde **proje** menüsünü tıklatın **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="1b7b1-110">İçinde **şablonları** bölmesinde tıklayın **veri** kategori tıklayın ve ardından **ADO.NET varlık veri modeli**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="1b7b1-111">Model adını girin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="1b7b1-112">' Nın ilk sayfasında [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Sihirbazı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>

4. <span data-ttu-id="1b7b1-113">İçinde **Choose Model Contents** iletişim kutusunda **veritabanından Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="1b7b1-114">Sonra **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-114">Then click **Next**.</span></span>

5. <span data-ttu-id="1b7b1-115">Tıklayın **yeni bağlantı** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="1b7b1-116">İçinde **bağlantı özellikleri** iletişim kutusu, sunucunuzun adını yazın, kimlik doğrulama yöntemini seçin, veritabanı adını yazın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="1b7b1-117">**Veri bağlantınızı seçin**s iletişim kutusunda, veritabanı bağlantı ayarlarınızı ile güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="1b7b1-118">Emin **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet:** onay kutusu işaretli.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="1b7b1-119">Sonra **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-119">Then click **Next**.</span></span>

8. <span data-ttu-id="1b7b1-120">İçinde **veritabanı nesnelerinizi seçin** veritabanının Tümünü Seç iletişim kutusunda, nesneler veri hizmeti kullanıma sunmak planlama.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1b7b1-121">Veri modelinde bulunan nesneleri, veri hizmeti tarafından otomatik olarak sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="1b7b1-122">Hizmet tarafından açıkça sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="1b7b1-123">Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1b7b1-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="1b7b1-124">Tıklayın **son** Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="1b7b1-125">Bu, belirli bir veritabanını temel alan varsayılan bir veri modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="1b7b1-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Veri modelini özelleştirmek için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="1b7b1-127">Daha fazla bilgi için [görevleri](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span><span class="sxs-lookup"><span data-stu-id="1b7b1-127">For more information, see [Tasks](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="1b7b1-128">Yeni veri modelini kullanarak veri hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b7b1-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="1b7b1-129">Visual Studio'da veri modelini temsil eden .edmx dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="1b7b1-130">İçinde **Model tarayıcı**, modelin sağ tıklayın, **özellikleri**ve sonra varlık kapsayıcısının adı not edin.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="1b7b1-131">İçinde **Çözüm Gezgini**, adına sağ tıklayın, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="1b7b1-132">İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti** şablonunda **Web** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Visual Studio 2015'te WCF veri hizmeti öğe şablonu](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="1b7b1-134">**WCF veri hizmeti** şablonu kullanılabilir Visual Studio 2015, ancak Visual Studio 2017 içinde değil.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="1b7b1-135">Hizmet için bir ad sağlayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="1b7b1-136">Visual Studio, yeni hizmet için XML işaretleme ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="1b7b1-137">Varsayılan olarak, kod düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="1b7b1-138">Veri Hizmeti için kod içinde açıklamayı değiştirin `/* TODO: put your data source class name here */` devralınan türüyle veri hizmeti tanımlayan sınıf tanımında <xref:System.Data.Objects.ObjectContext> sınıfı ve bu, 2. adımda belirtilen veri modelinin varlık kapsayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="1b7b1-139">Veri Hizmeti için kodda verileri kullanıma sunan hizmet varlık kümeleri erişmek yetkili istemcilere etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="1b7b1-140">Daha fazla bilgi için [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="1b7b1-140">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

8. <span data-ttu-id="1b7b1-141">Bir Web tarayıcısı kullanarak Northwind.svc veri hizmeti test etmek için konusundaki yönergeleri izleyin. [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="1b7b1-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b7b1-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b7b1-142">See Also</span></span>

- [<span data-ttu-id="1b7b1-143">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1b7b1-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="1b7b1-144">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="1b7b1-144">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="1b7b1-145">Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b7b1-145">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="1b7b1-146">Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b7b1-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
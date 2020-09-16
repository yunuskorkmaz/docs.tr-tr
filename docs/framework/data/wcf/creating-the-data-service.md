---
title: Visual Studio 'da WCF veri hizmeti oluşturma
description: Örnek bir veritabanını temel alan OData akışını kullanıma sunmak için WCF Veri Hizmetleri kullanan bir örnek veri hizmeti oluşturmayı öğrenin.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: f6e95ce58e055f0c745b781c664309e4ef91ffc6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554019"
---
# <a name="create-the-data-service"></a><span data-ttu-id="62a1e-103">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="62a1e-103">Create the data service</span></span>

<span data-ttu-id="62a1e-104">Bu konu başlığında, Northwind örnek veritabanına dayalı açık veri Protokolü (OData) akışını kullanıma sunmak için WCF Veri Hizmetleri kullanan bir örnek veri hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62a1e-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="62a1e-105">Görev aşağıdaki temel adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="62a1e-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="62a1e-106">Bir ASP.NET Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62a1e-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="62a1e-107">Varlık Veri Modeli araçlarını kullanarak veri modelini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="62a1e-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="62a1e-108">Veri hizmetini Web uygulamasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="62a1e-109">Veri hizmetine erişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="62a1e-110">ASP.NET Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="62a1e-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="62a1e-111">Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="62a1e-112">**Yeni proje** iletişim kutusunda, Visual Basic veya Visual C# altında **Web** kategorisini seçin ve ardından **ASP.NET Web uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="62a1e-113">`NorthwindService`Projenin adı olarak girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="62a1e-114">**Yeni ASP.NET Web uygulaması** Iletişim kutusunda **boş** ' ı seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="62a1e-115">Seçim Web uygulamanız için belirli bir bağlantı noktası numarası belirtin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="62a1e-116">Note: bağlantı noktası numarası, `12345` Bu hızlı başlangıç konuları serisinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62a1e-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="62a1e-117">**Çözüm Gezgini**, az önce oluşturduğunuz ASP.NET projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="62a1e-118">**Web** sekmesini seçin ve **belirli bir bağlantı noktası** metin kutusunun değerini olarak ayarlayın `12345` .</span><span class="sxs-lookup"><span data-stu-id="62a1e-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="62a1e-119">Veri modelini tanımlama</span><span class="sxs-lookup"><span data-stu-id="62a1e-119">Define the data model</span></span>

1. <span data-ttu-id="62a1e-120">**Çözüm Gezgini**, ASP.net projesinin adına sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="62a1e-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="62a1e-121">**Yeni öğe Ekle** Iletişim kutusunda **veri** kategorisini seçin ve ardından **ADO.net varlık veri modeli**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="62a1e-122">Veri modeli adı için girin `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="62a1e-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="62a1e-123">**Varlık veri modeli sihirbazında**, **veritabanından EF Designer**' ı seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="62a1e-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="62a1e-124">Aşağıdaki adımlardan birini gerçekleştirerek veri modelini veritabanına bağlayın ve ardından **İleri**' ye tıklayın:</span><span class="sxs-lookup"><span data-stu-id="62a1e-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="62a1e-125">Zaten yapılandırılmış bir veritabanı bağlantınız yoksa **Yeni bağlantı** ' ya tıklayın ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62a1e-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="62a1e-126">Daha fazla bilgi için bkz. [nasıl yapılır: SQL Server veritabanlarına bağlantı oluşturma](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="62a1e-126">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="62a1e-127">Bu SQL Server örneğine Northwind örnek veritabanının eklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62a1e-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="62a1e-128">\- veya</span><span class="sxs-lookup"><span data-stu-id="62a1e-128">\- or -</span></span>

    - <span data-ttu-id="62a1e-129">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bağlantı listesinden bu bağlantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="62a1e-130">Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümler ve saklı yordamlar onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="62a1e-131">Sihirbazı kapatmak için **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="62a1e-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="62a1e-132">WCF veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="62a1e-132">Create the WCF data service</span></span>

1. <span data-ttu-id="62a1e-133">**Çözüm Gezgini**, ASP.NET projesine sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="62a1e-134">**Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisinden **WCF veri hizmeti** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="62a1e-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="62a1e-136">**WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62a1e-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="62a1e-137">Hizmetin adı için, yazın `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="62a1e-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="62a1e-138">Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62a1e-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="62a1e-139">Varsayılan olarak, kod Düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="62a1e-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="62a1e-140">**Çözüm Gezgini**, hizmet Northwind adına *. svc.cs* veya *. svc. vb*uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="62a1e-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="62a1e-141">Veri Hizmeti kodunda, veri `/* TODO: put your data source class name here */` hizmetini tanımlayan sınıfın tanımındaki, bu örnekte olduğu gibi veri modelinin varlık kapsayıcısı olan türde olan açıklamayı değiştirin `NorthwindEntities` .</span><span class="sxs-lookup"><span data-stu-id="62a1e-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="62a1e-142">Sınıf tanımı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="62a1e-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="62a1e-143">Veri hizmeti kaynaklarına erişimi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="62a1e-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="62a1e-144">Veri Hizmeti kodunda, işlevdeki yer tutucu kodunu aşağıdaki gibi değiştirin `InitializeService` :</span><span class="sxs-lookup"><span data-stu-id="62a1e-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="62a1e-145">Bu, yetkili istemcilerin belirtilen varlık kümelerine yönelik kaynaklara okuma ve yazma erişimi olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="62a1e-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="62a1e-146">ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="62a1e-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="62a1e-147">Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisi de güvence altına alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62a1e-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="62a1e-148">Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="62a1e-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="62a1e-149">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="62a1e-149">Next steps</span></span>

<span data-ttu-id="62a1e-150">Northwind örnek veritabanına dayalı bir OData akışını kullanıma sunan yeni bir veri hizmetini başarıyla oluşturdunuz ve ASP.NET Web uygulamasında izinleri olan istemciler için akışa erişimi etkinleştirdiniz.</span><span class="sxs-lookup"><span data-stu-id="62a1e-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="62a1e-151">Ardından, Visual Studio 'dan veri hizmetini başlatacak ve bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek OData akışına erişebileceksiniz:</span><span class="sxs-lookup"><span data-stu-id="62a1e-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="62a1e-152">Hizmete bir Web tarayıcısından erişin</span><span class="sxs-lookup"><span data-stu-id="62a1e-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="62a1e-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62a1e-153">See also</span></span>

- <span data-ttu-id="62a1e-154">[ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62a1e-154">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

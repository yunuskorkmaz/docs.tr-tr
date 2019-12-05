---
title: Visual Studio 'da WCF veri hizmeti oluşturma
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 72e3b35465968674a20aa48262d3425a2190ff74
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802272"
---
# <a name="create-the-data-service"></a><span data-ttu-id="7fd6f-102">Veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="7fd6f-102">Create the data service</span></span>

<span data-ttu-id="7fd6f-103">Bu konu başlığında, Northwind örnek veritabanına dayalı açık veri Protokolü (OData) akışını kullanıma sunmak için WCF Veri Hizmetleri kullanan bir örnek veri hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-103">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="7fd6f-104">Görev aşağıdaki temel adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="7fd6f-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="7fd6f-105">Bir ASP.NET Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="7fd6f-106">Varlık Veri Modeli araçlarını kullanarak veri modelini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="7fd6f-107">Veri hizmetini Web uygulamasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="7fd6f-108">Veri hizmetine erişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="7fd6f-109">ASP.NET Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7fd6f-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="7fd6f-110">Visual Studio 'da, **Dosya** menüsünde **Yeni** > **projesi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="7fd6f-111">**Yeni proje** iletişim kutusunda, Visual Basic veya görsel C# altında **web** kategorisini seçin ve ardından **ASP.NET Web uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="7fd6f-112">Projenin adı olarak `NorthwindService` girin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="7fd6f-113">**Yeni ASP.NET Web uygulaması** Iletişim kutusunda **boş** ' ı seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="7fd6f-114">Seçim Web uygulamanız için belirli bir bağlantı noktası numarası belirtin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="7fd6f-115">Note: bağlantı noktası numarası `12345` bu hızlı başlangıç konularında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="7fd6f-116">**Çözüm Gezgini**, az önce oluşturduğunuz ASP.NET projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="7fd6f-117">**Web** sekmesini seçin ve **belirli bir bağlantı noktası** metin kutusunun değerini `12345`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="7fd6f-118">Veri modelini tanımlama</span><span class="sxs-lookup"><span data-stu-id="7fd6f-118">Define the data model</span></span>

1. <span data-ttu-id="7fd6f-119">**Çözüm Gezgini**, ASP.net projesinin adına sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7fd6f-120">**Yeni öğe Ekle** Iletişim kutusunda **veri** kategorisini seçin ve ardından **ADO.net varlık veri modeli**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="7fd6f-121">Veri modeli adı için `Northwind.edmx`girin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="7fd6f-122">**Varlık veri modeli sihirbazında**, **veritabanından EF Designer**' ı seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="7fd6f-123">Aşağıdaki adımlardan birini gerçekleştirerek veri modelini veritabanına bağlayın ve ardından **İleri**' ye tıklayın:</span><span class="sxs-lookup"><span data-stu-id="7fd6f-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="7fd6f-124">Zaten yapılandırılmış bir veritabanı bağlantınız yoksa **Yeni bağlantı** ' ya tıklayın ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="7fd6f-125">Daha fazla bilgi için bkz. [nasıl yapılır: SQL Server veritabanlarına bağlantı oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7fd6f-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="7fd6f-126">Bu SQL Server örneğine Northwind örnek veritabanının eklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="7fd6f-127">\- veya -</span><span class="sxs-lookup"><span data-stu-id="7fd6f-127">\- or -</span></span>

    - <span data-ttu-id="7fd6f-128">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantınız varsa, bağlantı listesinden bu bağlantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="7fd6f-129">Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümler ve saklı yordamlar onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="7fd6f-130">Sihirbazı kapatmak için **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="7fd6f-131">WCF veri hizmetini oluşturma</span><span class="sxs-lookup"><span data-stu-id="7fd6f-131">Create the WCF data service</span></span>

1. <span data-ttu-id="7fd6f-132">**Çözüm Gezgini**, ASP.NET projesine sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7fd6f-133">**Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisinden **WCF veri hizmeti** öğe şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="7fd6f-135">**WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="7fd6f-136">Hizmetin adı için `Northwind`yazın.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="7fd6f-137">Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7fd6f-138">Varsayılan olarak, kod Düzenleyicisi penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="7fd6f-139">**Çözüm Gezgini**, hizmet Northwind adına *. svc.cs* veya *. svc. vb*uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="7fd6f-140">Veri Hizmeti kodunda, veri hizmetinin varlık kapsayıcısı olan tür ile veri hizmetini tanımlayan sınıfın tanımındaki açıklama `/* TODO: put your data source class name here */` değiştirin. Bu durumda, `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="7fd6f-141">Sınıf tanımı aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7fd6f-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="7fd6f-142">Veri hizmeti kaynaklarına erişimi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="7fd6f-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="7fd6f-143">Veri Hizmeti kodunda, `InitializeService` işlevindeki yer tutucu kodunu aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7fd6f-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="7fd6f-144">Bu, yetkili istemcilerin belirtilen varlık kümelerine yönelik kaynaklara okuma ve yazma erişimi olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7fd6f-145">ASP.NET uygulamasına erişebilen tüm istemciler de veri hizmeti tarafından sunulan kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="7fd6f-146">Bir üretim verileri hizmetinde, kaynaklara yetkisiz erişimi engellemek için uygulamanın kendisi de güvence altına alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="7fd6f-147">Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7fd6f-147">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7fd6f-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7fd6f-148">Next steps</span></span>

<span data-ttu-id="7fd6f-149">Northwind örnek veritabanına dayalı bir OData akışını kullanıma sunan yeni bir veri hizmetini başarıyla oluşturdunuz ve ASP.NET Web uygulamasında izinleri olan istemciler için akışa erişimi etkinleştirdiniz.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="7fd6f-150">Ardından, Visual Studio 'dan veri hizmetini başlatacak ve bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek OData akışına erişebileceksiniz:</span><span class="sxs-lookup"><span data-stu-id="7fd6f-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7fd6f-151">Hizmete bir Web tarayıcısından erişin</span><span class="sxs-lookup"><span data-stu-id="7fd6f-151">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="7fd6f-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fd6f-152">See also</span></span>

- <span data-ttu-id="7fd6f-153">[ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7fd6f-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>

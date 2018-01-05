---
title: "Veri hizmeti oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57e305fd8b03e8d46c1fdcb7dd551f32062a1009
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-data-service"></a><span data-ttu-id="69ff8-102">Veri hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="69ff8-102">Creating the Data Service</span></span>
<span data-ttu-id="69ff8-103">Bu görevde kullanan bir örnek veri hizmeti oluşturacak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanıma sunmak için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind örnek veritabanı üzerinde temel akış.</span><span class="sxs-lookup"><span data-stu-id="69ff8-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="69ff8-104">Görev aşağıdaki temel adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="69ff8-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="69ff8-105">Oluşturma bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması.</span><span class="sxs-lookup"><span data-stu-id="69ff8-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="69ff8-106">Veri modeli kullanarak tanımlayın [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] araçları.</span><span class="sxs-lookup"><span data-stu-id="69ff8-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="69ff8-107">Veri Hizmeti Web uygulamasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69ff8-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="69ff8-108">Veri hizmeti erişimini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="69ff8-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69ff8-109">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Bu görevi tamamladığınızda oluşturduğunuz Web uygulaması üzerinde çalıştığı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştirme sunucusu tarafından sağlanan [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69ff8-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="69ff8-110">Geliştirme Sunucusu, yalnızca yerel bilgisayardan erişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="69ff8-110"> Development Server only supports access from the local computer.</span></span> <span data-ttu-id="69ff8-111">Ayrıca test ve geliştirme sırasında veri hizmeti sorunlarını kolaylaştırmak için Internet Information Services (IIS) kullanarak veri hizmeti barındıran uygulamayı çalıştırmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="69ff8-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="69ff8-112">Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span><span class="sxs-lookup"><span data-stu-id="69ff8-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="69ff8-113">ASP.NET Web uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69ff8-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="69ff8-114">İçinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], **dosya** menüsünde, select **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-114">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="69ff8-115">İçinde **yeni proje** iletişim kutusunda, ya da altında [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] seçin **Web** şablonu ve ardından **ASP.NET Web uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-115">In the **New Project** dialog box, under either [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69ff8-116">Kullanırsanız [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, yeni bir Web uygulaması yerine yeni bir Web sitesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="69ff8-116">If you use [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="69ff8-117">Tür `NorthwindService` projesinin adı olarak.</span><span class="sxs-lookup"><span data-stu-id="69ff8-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="69ff8-118">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="69ff8-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="69ff8-119">(İsteğe bağlı) Web uygulamanız için belirli bir bağlantı noktası numarası belirtin.</span><span class="sxs-lookup"><span data-stu-id="69ff8-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="69ff8-120">Not: bağlantı noktası numarası `12345` hızlı geri kalanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69ff8-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="69ff8-121">İçinde **Çözüm Gezgini**, adına sağ tıklayın [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] az önce oluşturduğunuz proje ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="69ff8-122">Seçin **Web** sekmesini tıklatın ve değerini ayarlama **belirli bir bağlantı noktası** metin kutusuna `12345`.</span><span class="sxs-lookup"><span data-stu-id="69ff8-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="69ff8-123">Veri modeli tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="69ff8-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="69ff8-124">İçinde **Çözüm Gezgini**, adına sağ tıklayın [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Yeni Öğe Ekle.**</span><span class="sxs-lookup"><span data-stu-id="69ff8-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="69ff8-125">İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **veri** şablonu ve ardından **ADO.NET varlık veri modeli**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="69ff8-126">Veri modeli ad için `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="69ff8-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="69ff8-127">İçinde [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Sihirbazı'nı seçin **veritabanından Oluştur**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="69ff8-128">Aşağıdaki adımlardan birini yaparak veri modeli veritabanına bağlanmak ve ardından **sonraki**:</span><span class="sxs-lookup"><span data-stu-id="69ff8-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="69ff8-129">Önceden yapılandırılmış bir veritabanı bağlantısı yoksa tıklatın **yeni bağlantı** ve yeni bir bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69ff8-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="69ff8-130">Daha fazla bilgi için bkz: [nasıl yapılır: SQL Server veritabanları için bağlantıları oluşturma](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="69ff8-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="69ff8-131">Bu [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] örnek, iliştirilmiş Northwind örnek veritabanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69ff8-131">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="69ff8-132">\-veya -</span><span class="sxs-lookup"><span data-stu-id="69ff8-132">\- or -</span></span>  
  
    -   <span data-ttu-id="69ff8-133">Northwind veritabanına bağlanmak için zaten yapılandırılmış bir veritabanı bağlantısı varsa, bu bağlantıyı bağlantılar listesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="69ff8-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="69ff8-134">Sihirbazın son sayfasında, veritabanındaki tüm tablolar için onay kutularını seçin ve görünümleri ve saklı yordamlar için onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="69ff8-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="69ff8-135">Tıklatın **son** sihirbazı kapatın.</span><span class="sxs-lookup"><span data-stu-id="69ff8-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69ff8-136">Bu üretilen veri modeli varlık türlerine yabancı anahtar özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="69ff8-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="69ff8-137">Veri modeli kullanılarak oluşturulan [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 bu yabancı anahtar özelliklerini içermez.</span><span class="sxs-lookup"><span data-stu-id="69ff8-137">Data models created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="69ff8-138">Bu nedenle, istemci veri hizmeti sınıflarını kullanılarak oluşturulmuş Northwind veri hizmete erişmek için oluşturulan herhangi bir istemci uygulama güncelleştirmelisiniz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Northwind veri hizmetinin bu sürümü erişmeye çalışmadan önce 2008.</span><span class="sxs-lookup"><span data-stu-id="69ff8-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="69ff8-139">Veri hizmetini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69ff8-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="69ff8-140">İçinde **Çözüm Gezgini**, adına sağ tıklayın, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proje ve ardından **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="69ff8-141">İçinde **Yeni Öğe Ekle** iletişim kutusunda **WCF veri hizmeti**.</span><span class="sxs-lookup"><span data-stu-id="69ff8-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="69ff8-142">Hizmet ad için `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="69ff8-142">For the name of the service, type `Northwind`.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="69ff8-143">Visual Studio yeni hizmet için XML biçimlendirme ve kodun dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69ff8-143">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="69ff8-144">Varsayılan olarak Kod Düzenleyicisi penceresini açar.</span><span class="sxs-lookup"><span data-stu-id="69ff8-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="69ff8-145">İçinde **Çözüm Gezgini**, hizmet adı, Northwind, uzantıya sahip olacaktır. svc.cs veya. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="69ff8-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="69ff8-146">Veri Hizmeti kodunu açıklamayı değiştirin `/* TODO: put your data source class name here */` , varlık kapsayıcısının veri modelinin türü olan veri hizmeti tanımlayan sınıf tanımında bu durumda olduğu `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="69ff8-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="69ff8-147">Sınıf tanımı bu görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="69ff8-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="69ff8-148">Veri Hizmeti kaynaklarına erişimi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="69ff8-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="69ff8-149">Veri Hizmeti için kodda yer tutucu kodu `InitializeService` aşağıdaki işleviyle:</span><span class="sxs-lookup"><span data-stu-id="69ff8-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="69ff8-150">Bu, yetkili istemcilerin okuma ve yazma erişimi kaynaklara belirtilen varlık kümeleri için sağlar.</span><span class="sxs-lookup"><span data-stu-id="69ff8-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69ff8-151">Erişebilmeniz için herhangi bir istemci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama aynı zamanda veri hizmeti tarafından sunulan kaynaklara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="69ff8-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="69ff8-152">Bir üretim verileri Hizmeti'nde kaynaklara yetkisiz erişimi önlemek için ayrıca uygulamanın kendisinin güvenli.</span><span class="sxs-lookup"><span data-stu-id="69ff8-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="69ff8-153">Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="69ff8-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="69ff8-154">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="69ff8-154">Next Steps</span></span>  
 <span data-ttu-id="69ff8-155">Sunan yeni bir veri hizmeti başarıyla oluşturdunuz bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Northwind örnek veritabanı ve size göre akış akışına izinlere sahip istemciler için erişim etkinleştirdiğinizden [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması.</span><span class="sxs-lookup"><span data-stu-id="69ff8-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="69ff8-156">Ardından, veri hizmetinden başlar [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] ve size erişim [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] HTTP GET isteklerini bir Web tarayıcısı aracılığıyla göndererek akış:</span><span class="sxs-lookup"><span data-stu-id="69ff8-156">Next, you will start the data service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="69ff8-157">Web Tarayıcısından Hizmete Erişme</span><span class="sxs-lookup"><span data-stu-id="69ff8-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="69ff8-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69ff8-158">See Also</span></span>  
 [<span data-ttu-id="69ff8-159">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="69ff8-159">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)

---
title: ".NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)"
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
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 563d08a5907c8248a74ba992de17ac3dd0679827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="6ccba-102">.NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)</span><span class="sxs-lookup"><span data-stu-id="6ccba-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="6ccba-103">Bu, son görevdir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="6ccba-103">This is the final task of the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] quickstart.</span></span> <span data-ttu-id="6ccba-104">Bu görevde, bir konsol uygulaması çözüme eklemek için bir başvuru ekleyin [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış bu yeni istemci uygulaması ve erişim [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] oluşturulan istemci veri hizmeti sınıfları ve istemci kullanarak istemci uygulamasından akışı kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="6ccba-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the client application by using the generated client data service classes and client libraries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ccba-105">Bir .NET Framework tabanlı bir istemci uygulaması veri akışına erişmek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6ccba-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="6ccba-106">Veri Hizmeti tüketen uygulama bileşeni tarafından erişilebilen bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="6ccba-106">The data service can be accessed by any application component that consumes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="6ccba-107">Daha fazla bilgi için bkz: [veri hizmeti istemci uygulamasında kullanma](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6ccba-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="6ccba-108">Visual Studio kullanarak istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6ccba-108">To create the client application by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="6ccba-109">İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="6ccba-110">İçinde **proje türleri**, tıklatın **Windows**ve ardından **WPF uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="6ccba-110">In **Project types**, click **Windows**, and then select **WPF Application** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="6ccba-111">Girin `NorthwindClient` proje adı ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6ccba-112">MainWindow.xaml dosyasını açın ve XAML kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6ccba-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="6ccba-113">Veri hizmeti başvurusu projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="6ccba-113">To add a data service reference to the project</span></span>  
  
1.  <span data-ttu-id="6ccba-114">NorthwindClient projesine sağ tıklayın, **hizmet Başvurusu Ekle**ve ardından **bulma**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-114">Right-click the NorthwindClient project, click **Add Service Reference**, and then click **Discover**.</span></span>  
  
     <span data-ttu-id="6ccba-115">Bu ilk görevde oluşturduğunuz Northwind veri hizmeti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6ccba-115">This displays the Northwind data service that you created in the first task.</span></span>  
  
2.  <span data-ttu-id="6ccba-116">İçinde **Namespace** metin kutusunda, `Northwind`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6ccba-117">Bu, yeni bir kod dosyası erişmek ve nesneler olarak veri hizmeti kaynakları ile etkileşim kurmak için kullanılan veri sınıfları içeren projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="6ccba-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="6ccba-118">Veri sınıflarını ad alanında oluşturulan `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="6ccba-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="6ccba-119">WPF uygulamasında veri hizmeti verilere erişmek için</span><span class="sxs-lookup"><span data-stu-id="6ccba-119">To access data service data in the WPF application</span></span>  
  
1.  <span data-ttu-id="6ccba-120">İçinde **Çözüm Gezgini** altında **NorthwindClient**, projeyi sağ tıklatın ve **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="6ccba-121">Başvuru Ekle iletişim kutusunda tıklatın **.NET** sekmesinde, System.Data.Services.Client.dll derlemesi seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-121">In the Add Reference dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span> <span data-ttu-id="6ccba-122">İçinde **Çözüm Gezgini** altında **NorthwindClient**MainWindow.xaml dosyası için kod sayfasını açın ve aşağıdakileri ekleyin `using` deyimi (`Imports` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="6ccba-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  <span data-ttu-id="6ccba-123">Bu veri hizmeti sorgular ve sonucu bağlar aşağıdaki kodu ekleyin bir <xref:System.Data.Services.Client.DataServiceCollection%601> içine `MainWindow` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="6ccba-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ccba-124">Ana bilgisayar adını değiştirmeniz gerekir `localhost:12345` Northwind veri hizmeti örneğiniz barındırma bağlantı noktası ve sunucu.</span><span class="sxs-lookup"><span data-stu-id="6ccba-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  <span data-ttu-id="6ccba-125">Değişiklikleri kaydeder aşağıdaki kodu ekleyin `MainWindow` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="6ccba-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="6ccba-126">Derleme ve NorthwindClient uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6ccba-126">To build and run the NorthwindClient application</span></span>  
  
1.  <span data-ttu-id="6ccba-127">İçinde **Çözüm Gezgini**, NorthwindClient projesine sağ tıklatın ve **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>  
  
2.  <span data-ttu-id="6ccba-128">Uygulamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6ccba-128">Press F5 to start the application.</span></span>  
  
     <span data-ttu-id="6ccba-129">Bu çözüm oluşturur ve istemci uygulaması başlatır.</span><span class="sxs-lookup"><span data-stu-id="6ccba-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="6ccba-130">Veri hizmetinden istenen ve konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6ccba-130">Data is requested from the service and displayed in the console.</span></span>  
  
3.  <span data-ttu-id="6ccba-131">Bir değeri **miktar** veri kılavuzu ve ardından sütunu **kaydetmek**.</span><span class="sxs-lookup"><span data-stu-id="6ccba-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>  
  
     <span data-ttu-id="6ccba-132">Değişiklikler veri hizmetine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6ccba-132">Changes are saved to the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ccba-133">NorthwindClient uygulamasının bu sürümü, ekleme ve silme varlıklarının desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6ccba-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6ccba-134">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="6ccba-134">Next Steps</span></span>  
 <span data-ttu-id="6ccba-135">Northwind örnek erişen istemci uygulaması başarıyla oluşturdunuz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="6ccba-135">You have successfully created the client application that accesses the sample Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="6ccba-136">Ayrıca tamamladınız [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="6ccba-136">You have also completed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] quickstart.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6ccba-137">erişen bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] besleme yeri bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama, bkz: [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="6ccba-137"> accessing an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccba-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ccba-138">See Also</span></span>  
 [<span data-ttu-id="6ccba-139">Başlarken</span><span class="sxs-lookup"><span data-stu-id="6ccba-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [<span data-ttu-id="6ccba-140">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6ccba-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

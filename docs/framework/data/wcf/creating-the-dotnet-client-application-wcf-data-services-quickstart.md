---
title: .NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: efea92fa5176641ac64265dfffd44a088115bb61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305942"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="b82c5-102">.NET Framework istemci uygulaması oluşturma (WCF Veri Hizmetleri Hızlı Başlangıç)</span><span class="sxs-lookup"><span data-stu-id="b82c5-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="b82c5-103">Bu, WCF Veri Hizmetleri Hızlı Başlangıç Son görevdir.</span><span class="sxs-lookup"><span data-stu-id="b82c5-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="b82c5-104">Bu görevde, bir konsol uygulaması çözüme ekleyin, bir başvuru ekleyin [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bu yeni istemci uygulamasına akışı ve OData istemci kitaplıkları ve oluşturulan istemci veri hizmeti sınıfları kullanarak istemci uygulamasından akışına erişim .</span><span class="sxs-lookup"><span data-stu-id="b82c5-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="b82c5-105">.NET Framework tabanlı bir istemci uygulama bir veri akışına erişmek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b82c5-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="b82c5-106">Veri Hizmeti, bir OData akışına kullanan herhangi bir uygulama bileşeni tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b82c5-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="b82c5-107">Daha fazla bilgi için [bir istemci uygulamasında veri hizmeti kullanma](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b82c5-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="b82c5-108">Visual Studio kullanarak istemci uygulamasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b82c5-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="b82c5-109">İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="b82c5-110">Sol bölmede seçin **yüklü** > [**Visual C#**  veya **Visual Basic**] > **Windows Masaüstü**ve ardından seçin **WPF uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="b82c5-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="b82c5-111">Girin `NorthwindClient` proje adı ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="b82c5-112">MainWindow.xaml dosyasını açın ve XAML kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b82c5-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="b82c5-113">Projeye veri hizmeti başvurusu eklemek için</span><span class="sxs-lookup"><span data-stu-id="b82c5-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="b82c5-114">İçinde **Çözüm Gezgini**, northwindclient & lt projeye sağ tıklayın, **Ekle** > **hizmet başvurusu**ve ardından **Bul** .</span><span class="sxs-lookup"><span data-stu-id="b82c5-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="b82c5-115">Bu ilk görevde oluşturduğunuz Northwind verileri hizmeti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b82c5-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="b82c5-116">İçinde **Namespace** metin kutusunda, `Northwind`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="b82c5-117">Bu, yeni bir kod dosyası erişmek ve veri hizmeti kaynaklarına nesneler olarak etkileşim için kullanılan veri sınıfları içeren projeyi ekler.</span><span class="sxs-lookup"><span data-stu-id="b82c5-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="b82c5-118">Veri sınıfları ad alanında oluşturulan `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="b82c5-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="b82c5-119">WPF uygulamasında veri hizmeti verilere erişmek için</span><span class="sxs-lookup"><span data-stu-id="b82c5-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="b82c5-120">İçinde **Çözüm Gezgini** altında **; northwindclient & lt**, projeye sağ tıklayın ve tıklayın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="b82c5-121">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET** sekmesinde System.Data.Services.Client.dll derlemeyi seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="b82c5-122">İçinde **Çözüm Gezgini** altında **; northwindclient & lt**MainWindow.xaml dosyanın kod sayfasını açın ve aşağıdakini ekleyin `using` deyimi (`Imports` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="b82c5-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3. <span data-ttu-id="b82c5-123">Bu veri hizmetini sorgular ve sonuca bağlar aşağıdaki kodu bir <xref:System.Data.Services.Client.DataServiceCollection%601> içine `MainWindow` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b82c5-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="b82c5-124">Ana bilgisayar adını değiştirmelisiniz `localhost:12345` Northwind verileri hizmeti örneğinizi barındırma bağlantı noktası ve sunucu.</span><span class="sxs-lookup"><span data-stu-id="b82c5-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4. <span data-ttu-id="b82c5-125">Değişiklikleri kaydeder aşağıdaki kodu ekleyin `MainWindow` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b82c5-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="b82c5-126">Northwindclient & lt uygulaması derleme ve çalıştırma için</span><span class="sxs-lookup"><span data-stu-id="b82c5-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="b82c5-127">İçinde **Çözüm Gezgini**; northwindclient & lt projeye sağ tıklayın ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="b82c5-128">Tuşuna **F5** uygulamayı başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="b82c5-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="b82c5-129">Bu çözüm derlenir ve istemci uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="b82c5-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="b82c5-130">Veriler hizmetten istenen ve konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b82c5-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="b82c5-131">Bir değeri de düzenlemeniz **miktar** veri kılavuzu ve ardından sütunun **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="b82c5-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="b82c5-132">Veri hizmetine değişiklikler kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="b82c5-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b82c5-133">Ekleme ve silme varlıklarının; northwindclient & lt uygulamanın bu sürümü desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="b82c5-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b82c5-134">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b82c5-134">Next Steps</span></span>

<span data-ttu-id="b82c5-135">Bulunan örnek Northwind OData akışındaki erişen istemci uygulaması başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="b82c5-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="b82c5-136">WCF Veri Hizmetleri hızlı başlangıç ayrıca tamamladınız!</span><span class="sxs-lookup"><span data-stu-id="b82c5-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="b82c5-137">Gelen OData erişme hakkında daha fazla bilgi akışına bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulaması, bakın [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="b82c5-137">For more information about accessing an OData feed from a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b82c5-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b82c5-138">See also</span></span>

- [<span data-ttu-id="b82c5-139">Başlarken</span><span class="sxs-lookup"><span data-stu-id="b82c5-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="b82c5-140">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b82c5-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

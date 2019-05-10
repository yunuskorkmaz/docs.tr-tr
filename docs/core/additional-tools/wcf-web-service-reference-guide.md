---
title: WCF Web servisi Başvurusu Ekle
description: Microsoft WCF Web Service Reference Provider .NET Core ve ASP.NET Core projeleri için .NET Framework projeleri için hizmet Başvurusu Ekle benzer işlevsellik ekleyen aracı genel bakış.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 806f6e90aedc669c3a56ce1cde64311bdd4af32c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750500"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="78c54-103">WCF Web hizmeti başvurusu sağlayıcısı aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="78c54-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="78c54-104">Yıllar içinde birçok Visual Studio Geliştirici üretkenliğini keyif aldığınızı, [ **hizmet Başvurusu Ekle** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) .NET Framework projelerini web hizmetlerine erişmek gerektiğinde sağlanan aracı.</span><span class="sxs-lookup"><span data-stu-id="78c54-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="78c54-105">**WCF Web Service Reference** sağlayan bir hizmet Başvurusu Ekle işlev gibi bir deneyim için .NET Core ve ASP.NET Core projeleri Visual Studio bağlı hizmeti uzantısı bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="78c54-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="78c54-106">Bu araç, bir ağ konumu üzerinde mevcut çözümde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve web erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren bir .NET Core uyumlu kaynak dosyası oluşturur hizmeti.</span><span class="sxs-lookup"><span data-stu-id="78c54-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78c54-107">Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78c54-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="78c54-108">Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="78c54-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78c54-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="78c54-109">Prerequisites</span></span>

* <span data-ttu-id="78c54-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="78c54-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="78c54-111">Uzantısını kullanma</span><span class="sxs-lookup"><span data-stu-id="78c54-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="78c54-112">**WCF Web Service Reference** seçenektir aşağıdaki proje şablonları kullanılarak oluşturulan projeler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="78c54-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
> * <span data-ttu-id="78c54-113">**Görsel C#**   >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="78c54-113">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="78c54-114">**Görsel C#**   >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="78c54-114">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="78c54-115">**Görsel C#**   >  **Web** > **ASP.NET Core Web uygulaması**</span><span class="sxs-lookup"><span data-stu-id="78c54-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="78c54-116">Kullanarak **ASP.NET Core Web uygulaması** proje şablonu örnek olarak, bu makalede gösterilmektedir, projeye WCF hizmet başvurusu ekleme yoluyla:</span><span class="sxs-lookup"><span data-stu-id="78c54-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="78c54-117">Çözüm Gezgini'nde çift tıklayarak **bağlı hizmetler** proje düğümü (.NET Core veya .NET Standard projesi üzerinde sağ tıkladığınızda bu seçenek kullanılabilir **bağımlılıkları** düğümü Çözüm Gezgini'nde projeye).</span><span class="sxs-lookup"><span data-stu-id="78c54-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="78c54-118">**Bağlı hizmetler** sayfası, aşağıdaki görüntüde gösterildiği gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="78c54-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![.NET Core için Visual Studio bağlı Hizmetler'i sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="78c54-120">Üzerinde **bağlı hizmetler** sayfasında **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="78c54-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="78c54-121">Bu işlem sonrasında **yapılandırma WCF Web Service Reference** Sihirbazı:</span><span class="sxs-lookup"><span data-stu-id="78c54-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![.NET Core için Visual Studio hizmet uç noktası sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="78c54-123">Bir hizmet seçin.</span><span class="sxs-lookup"><span data-stu-id="78c54-123">Select a service.</span></span>

    <span data-ttu-id="78c54-124">3a.</span><span class="sxs-lookup"><span data-stu-id="78c54-124">3a.</span></span> <span data-ttu-id="78c54-125">Çeşitli Hizmetleri arama seçenekleri kapsamında sunulan **yapılandırma WCF Web Service Reference** Sihirbazı:</span><span class="sxs-lookup"><span data-stu-id="78c54-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="78c54-126">Geçerli çözümde tanımlanan Hizmetleri aramak için tıklayın **bulma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="78c54-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="78c54-127">Belirtilen adresteki barındırılan hizmetler aramak için bir hizmeti URL'sini girin. **adresi** kutusuna ve tıklatın **Git** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="78c54-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="78c54-128">Web hizmeti meta veri bilgilerini içeren bir WSDL dosyası seçmek için tıklatın **Gözat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="78c54-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="78c54-129">3b.</span><span class="sxs-lookup"><span data-stu-id="78c54-129">3b.</span></span> <span data-ttu-id="78c54-130">Arama sonuçları listesinden hizmeti seçin **Hizmetleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="78c54-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="78c54-131">Gerekirse, karşılık gelen oluşturulan kodun ad alanını girin **Namespace** metin kutusu.</span><span class="sxs-lookup"><span data-stu-id="78c54-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="78c54-132">3c.</span><span class="sxs-lookup"><span data-stu-id="78c54-132">3c.</span></span> <span data-ttu-id="78c54-133">Tıklayın **sonraki** açmak için düğmeyi **veri türü seçenekleri** ve **istemci seçenekleri** sayfaları.</span><span class="sxs-lookup"><span data-stu-id="78c54-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="78c54-134">Alternatif olarak, **son** düğmesine varsayılan seçenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="78c54-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="78c54-135">**Veri türü seçenekleri** form, oluşturulan hizmet başvurusu yapılandırma ayarları iyileştirmek sağlar:</span><span class="sxs-lookup"><span data-stu-id="78c54-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![.NET Core için Visual Studio veri türü Seçenekleri sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="78c54-137">**Bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu seçeneğini, hizmet başvurusu kod oluşturma için gerekli veri türleri, projenizin başvurulan derlemeleri birinde tanımlandığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="78c54-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="78c54-138">Derleme zamanı tür çakışmasına veya çalışma zamanı sorunlarını önlemek için bu var olan veri türleri yeniden kullan önemlidir.</span><span class="sxs-lookup"><span data-stu-id="78c54-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="78c54-139">Tür bilgileri yüklenirken proje bağımlılıkları sayısı ve diğer sistem performans etkenlere bağlı olarak bir gecikme olabilir.</span><span class="sxs-lookup"><span data-stu-id="78c54-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="78c54-140">**Son** düğmesi devre sürece yükleme sırasında **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu olarak işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="78c54-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="78c54-141">Tıklayın **son** işiniz bittiğinde.</span><span class="sxs-lookup"><span data-stu-id="78c54-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="78c54-142">İlerleme durumunu, aracın görüntüleme oluştu:</span><span class="sxs-lookup"><span data-stu-id="78c54-142">While displaying progress, the tool:</span></span>

* <span data-ttu-id="78c54-143">WCF hizmetinden meta verileri indirir.</span><span class="sxs-lookup"><span data-stu-id="78c54-143">Downloads metadata from the WCF service.</span></span>
* <span data-ttu-id="78c54-144">Hizmet başvuru kodu adındaki bir dosyada oluşturur *reference.cs*ve projenizi altına ekler **bağlı hizmetler** düğümü.</span><span class="sxs-lookup"><span data-stu-id="78c54-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
* <span data-ttu-id="78c54-145">Derleme ve hedef platformda çalıştırmak için gerekli NuGet paket başvuruları içeren proje dosyasına (.csproj) güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="78c54-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio ilerleme durumu penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="78c54-147">Bu işlemleri tamamladığınızda, oluşturulan WCF istemci türü örneği oluşturun ve hizmet işlemleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="78c54-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="78c54-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="78c54-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="78c54-149">Geri bildirim ve sorular</span><span class="sxs-lookup"><span data-stu-id="78c54-149">Feedback & questions</span></span>

<span data-ttu-id="78c54-150">Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="78c54-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="78c54-151">Mevcut bir soru veya sorunlarla gözden geçirebilirsiniz [WCF deponun GitHub üzerinde en](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="78c54-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="78c54-152">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="78c54-152">Release notes</span></span>

* <span data-ttu-id="78c54-153">Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="78c54-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>

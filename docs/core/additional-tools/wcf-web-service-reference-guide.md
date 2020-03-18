---
title: WCF Web Hizmeti Başvurusu Ekle
description: .NET Framework projeleri için Hizmet Başvurusu Ekle'ye benzer şekilde .NET Core ve ASP.NET Core projeleri için işlevsellik ekleyen Microsoft WCF Web Hizmeti Başvuru Sağlayıcısı Aracına genel bakış.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715680"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="3a385-103">WCF Web Hizmeti Başvuru Sağlayıcı Aracını Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a385-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="3a385-104">Yıllar içinde, birçok Visual Studio geliştiricisi, [**.NET**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) Framework projelerinin web hizmetlerine erişmek için gerekli olduğunda Hizmet Başvurusu Ekle aracının sağladığı üretkenliğin keyfini çıkarmış oldu.</span><span class="sxs-lookup"><span data-stu-id="3a385-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="3a385-105">**WCF Web Service Reference** aracı, .NET Core ve ASP.NET Core projeleri için Hizmet Başvurusu Ekle işlevi gibi bir deneyim sağlayan Visual Studio'ya bağlı bir hizmet uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="3a385-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="3a385-106">Bu araç, geçerli çözümdeki bir web hizmetinden, ağ konumundan veya WSDL dosyasından meta verileri alır ve web'e erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodunu içeren bir .NET Core uyumlu kaynak dosyası oluşturur Hizmet.</span><span class="sxs-lookup"><span data-stu-id="3a385-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a385-107">Yalnızca güvenilir bir kaynaktan gelen hizmetlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a385-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="3a385-108">Güvenilmeyen bir kaynaktan referans eklemek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="3a385-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a385-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3a385-109">Prerequisites</span></span>

- <span data-ttu-id="3a385-110">[Visual Studio 2017 sürüm 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) veya sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="3a385-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="3a385-111">Uzantı nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="3a385-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="3a385-112">**WCF Web Hizmeti Başvurusu** seçeneği, aşağıdaki proje şablonları kullanılarak oluşturulan projeler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="3a385-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="3a385-113">**Görsel C#** > **.NET Çekirdek**</span><span class="sxs-lookup"><span data-stu-id="3a385-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="3a385-114">**Görsel C#** > **.NET Standardı**</span><span class="sxs-lookup"><span data-stu-id="3a385-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="3a385-115">**Visual C#** > **Web** > **ASP.NET Çekirdek Web Uygulaması**</span><span class="sxs-lookup"><span data-stu-id="3a385-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="3a385-116">ASP.NET **Çekirdek Web Uygulaması** proje şablonu örnek olarak kullanarak, bu makale projeye bir WCF hizmet başvurusu ekleyerek size yol gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a385-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="3a385-117">Çözüm Gezgini'nde, projenin **Bağlı Hizmetler** düğümüne çift tıklayın (.NET Core veya .NET Standard projesi için bu seçenek, Çözüm Gezgini'nde projenin **Bağımlılıklar** düğümüne sağ tıkladığınızda kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="3a385-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="3a385-118">**Bağlı Hizmetler** sayfası aşağıdaki resimde gösterildiği gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="3a385-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![.NET Core için Visual Studio Bağlantılı Hizmetler sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="3a385-120">Bağlı **Hizmetler** sayfasında, **Microsoft WCF Web Hizmeti Başvuru Sağlayıcısı'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="3a385-121">Bu, **Yapılandırılan WCF Web Hizmeti Başvurusu** sihirbazını getirir:</span><span class="sxs-lookup"><span data-stu-id="3a385-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![.NET Core için Visual Studio Service Endpoint sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="3a385-123">Bir hizmet seçin.</span><span class="sxs-lookup"><span data-stu-id="3a385-123">Select a service.</span></span>

    <span data-ttu-id="3a385-124">3a.</span><span class="sxs-lookup"><span data-stu-id="3a385-124">3a.</span></span> <span data-ttu-id="3a385-125">**Yapılandırma WCF Web Hizmeti Başvuru** sihirbazı içinde çeşitli hizmetler arama seçenekleri vardır:</span><span class="sxs-lookup"><span data-stu-id="3a385-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="3a385-126">Geçerli çözümde tanımlanan hizmetleri aramak için **Keşfet** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="3a385-127">Belirli bir adreste barındırılan hizmetleri aramak için **Adres** kutusuna bir hizmet URL'si girin ve **Git** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="3a385-128">Web hizmeti meta veri bilgilerini içeren bir WSDL dosyası seçmek için **Gözat** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="3a385-129">3b' ye kadar.</span><span class="sxs-lookup"><span data-stu-id="3a385-129">3b.</span></span> <span data-ttu-id="3a385-130">**Hizmetler** kutusundaki arama sonuçları listesinden hizmeti seçin.</span><span class="sxs-lookup"><span data-stu-id="3a385-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="3a385-131">Gerekirse, ilgili **Namespace** metin kutusuna oluşturulan kodun ad alanını girin.</span><span class="sxs-lookup"><span data-stu-id="3a385-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="3a385-132">3c' ye kadar.</span><span class="sxs-lookup"><span data-stu-id="3a385-132">3c.</span></span> <span data-ttu-id="3a385-133">**Veri Türü Seçenekleri** ve **İstemci Seçenekleri** sayfalarını açmak için **İleri** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="3a385-134">Alternatif olarak, varsayılan seçenekleri kullanmak için **Bitir** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="3a385-135">**Veri Türü Seçenekleri** formu, oluşturulan hizmet başvurusu yapılandırma ayarlarını hassaslaştırmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="3a385-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![.NET Core için Visual Studio Veri türü seçenekleri sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="3a385-137">Başvurulan derlemeler onay kutusu **seçeneğindeki Yeniden Kullanım türleri,** hizmet başvuru kodu oluşturma için gereken veri türleri projenizin başvurulan derlemelerinden birinde tanımlandığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a385-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="3a385-138">Derleme zamanı türü çakışmasını veya çalışma zamanı sorunlarını önlemek için bu varolan veri türlerini yeniden kullanmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3a385-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="3a385-139">Proje bağımlılıklarının ve diğer sistem performans faktörlerinin sayısına bağlı olarak, tür bilgileri yüklenirken gecikme olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a385-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="3a385-140">**Başvurulan derlemeler** onay kutusundaki Yeniden Kullan türleri işaretlenmemiş sayılmadığı sürece, Yükleme sırasında **Bitiş** düğmesi devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="3a385-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="3a385-141">Bittiğinde **Bitir'i** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3a385-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="3a385-142">İlerleme görüntülerken, araç:</span><span class="sxs-lookup"><span data-stu-id="3a385-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="3a385-143">WCF hizmetinden meta veri indirir.</span><span class="sxs-lookup"><span data-stu-id="3a385-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="3a385-144">*reference.cs*adlı bir dosyada hizmet başvuru kodunu oluşturur ve **Bağlı Hizmetler** düğümü altında projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="3a385-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="3a385-145">Proje dosyasını (.csproj) hedef platformda derlemek ve çalıştırmak için gereken NuGet paket referanslarıyla güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="3a385-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio İlerleme penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="3a385-147">Bu işlemler tamamlandığında, oluşturulan WCF istemci türünün bir örneğini oluşturabilir ve hizmet işlemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a385-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a385-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a385-148">See also</span></span>

- [<span data-ttu-id="3a385-149">Windows Communication Foundation uygulamaları yla başlayın</span><span class="sxs-lookup"><span data-stu-id="3a385-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="3a385-150">Visual Studio'da Windows Communication Foundation hizmetleri ve WCF veri hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3a385-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="3a385-151">WCF desteklenen özellikler .NET Core'da</span><span class="sxs-lookup"><span data-stu-id="3a385-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="3a385-152">Geri bildirim & sorular</span><span class="sxs-lookup"><span data-stu-id="3a385-152">Feedback & questions</span></span>

<span data-ttu-id="3a385-153">Herhangi bir sorunuz veya geri bildiriminiz varsa, [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) aracını kullanarak [Geliştirici Topluluğu'nda](https://developercommunity.visualstudio.com/) bildirin.</span><span class="sxs-lookup"><span data-stu-id="3a385-153">If you have any questions or feedback, report it at [Developer Community](https://developercommunity.visualstudio.com/) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="3a385-154">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="3a385-154">Release notes</span></span>

- <span data-ttu-id="3a385-155">Bilinen sorunlar da dahil olmak üzere güncelleştirilmiş sürüm bilgileri için [Yayın notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="3a385-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>

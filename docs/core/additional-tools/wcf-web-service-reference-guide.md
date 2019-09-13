---
title: WCF Web hizmeti başvurusu Ekle
description: .NET Framework projelerine yönelik Hizmet Başvurusu Ekle benzer şekilde .NET Core ve ASP.NET Core projelerine yönelik işlevsellik ekleyen Microsoft WCF Web Service Reference Provider aracına genel bakış.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 11a18161db0fde522442e2412c4522811c5dd40a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926453"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="d179b-103">WCF Web hizmeti başvuru sağlayıcısı aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="d179b-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="d179b-104">Yıllarca, birçok Visual Studio geliştiricisi, .NET Framework projeleri Web hizmetlerine erişmek için gereken [**hizmet başvurusu Ekle**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) aracın üretkenliğini sağladı.</span><span class="sxs-lookup"><span data-stu-id="d179b-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="d179b-105">**WCF Web hizmeti başvuru** Aracı, .NET Core ve ASP.NET Core projeleri için hizmet başvurusu Ekle işlevselliği gibi bir deneyim sağlayan Visual Studio bağlı bir hizmet uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="d179b-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="d179b-106">Bu araç, geçerli çözümdeki bir Web hizmetinden, bir ağ konumunda veya bir WSDL dosyasından meta verileri alır ve Web 'e erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren .NET Core ile uyumlu bir kaynak dosyası oluşturur hizmetle.</span><span class="sxs-lookup"><span data-stu-id="d179b-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d179b-107">Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d179b-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="d179b-108">Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="d179b-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d179b-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d179b-109">Prerequisites</span></span>

* <span data-ttu-id="d179b-110">[Visual Studio 2017 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) veya sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d179b-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="d179b-111">Uzantıyı kullanma</span><span class="sxs-lookup"><span data-stu-id="d179b-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="d179b-112">**WCF Web hizmeti başvuru** seçeneği, aşağıdaki proje şablonları kullanılarak oluşturulan projeler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d179b-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> * <span data-ttu-id="d179b-113">**Visual C#**  .net >  **Core**</span><span class="sxs-lookup"><span data-stu-id="d179b-113">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="d179b-114">**Görsel C#**  .NET Standard  > </span><span class="sxs-lookup"><span data-stu-id="d179b-114">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="d179b-115">**Visual C#**  Web >  ASP.NET CoreWeb > uygulaması</span><span class="sxs-lookup"><span data-stu-id="d179b-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="d179b-116">Örnek olarak **ASP.NET Core Web uygulaması** proje şablonunu kullanarak, bu makalede projeye bir WCF hizmeti başvurusu ekleme işlemi adım adım gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d179b-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="d179b-117">Çözüm Gezgini, projenin **bağlı hizmetler** düğümüne çift tıklayın (bir .NET Core veya .NET Standard projesi için, Çözüm Gezgini) projenin **Bağımlılıklar** düğümüne sağ tıkladığınızda bu seçenek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d179b-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="d179b-118">**Bağlı hizmetler** sayfası, aşağıdaki görüntüde gösterildiği gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="d179b-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![.NET Core için Visual Studio bağlı hizmetler sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="d179b-120">**Bağlı hizmetler** sayfasında, **Microsoft WCF Web Service Reference Provider**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="d179b-121">Bu, **WCF Web hizmeti başvurusunu yapılandırma** Sihirbazı 'nı getirir:</span><span class="sxs-lookup"><span data-stu-id="d179b-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![.NET Core için Visual Studio hizmeti uç noktası sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="d179b-123">Bir hizmet seçin.</span><span class="sxs-lookup"><span data-stu-id="d179b-123">Select a service.</span></span>

    <span data-ttu-id="d179b-124">3a.</span><span class="sxs-lookup"><span data-stu-id="d179b-124">3a.</span></span> <span data-ttu-id="d179b-125">**WCF Web hizmeti başvurusunu yapılandırma** Sihirbazı 'nda kullanılabilen birkaç hizmet arama seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="d179b-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="d179b-126">Geçerli çözümde tanımlanan Hizmetleri aramak için **bul** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="d179b-127">Belirtilen bir adreste barındırılan Hizmetleri aramak için, **Adres** kutusuna bir hizmet URL 'si girin ve **Git** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="d179b-128">Web hizmeti meta veri bilgilerini içeren bir WSDL dosyası seçmek için, **Gözden** geçirme düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="d179b-129">3b.</span><span class="sxs-lookup"><span data-stu-id="d179b-129">3b.</span></span> <span data-ttu-id="d179b-130">**Hizmetler** kutusundaki arama sonuçları listesinden hizmeti seçin.</span><span class="sxs-lookup"><span data-stu-id="d179b-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="d179b-131">Gerekirse, ilgili **ad alanı** metin kutusunda oluşturulan kod için ad alanını girin.</span><span class="sxs-lookup"><span data-stu-id="d179b-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="d179b-132">3c.</span><span class="sxs-lookup"><span data-stu-id="d179b-132">3c.</span></span> <span data-ttu-id="d179b-133">**Veri türü seçeneklerini** ve **istemci seçenekleri** sayfalarını açmak için **İleri** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="d179b-134">Alternatif olarak, varsayılan seçenekleri kullanmak için **son** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="d179b-135">**Veri türü seçenekleri** formu, oluşturulan hizmet başvurusu yapılandırma ayarlarını iyileştirmenize olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="d179b-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![.NET Core için Visual Studio veri türü seçenekleri sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="d179b-137">**Başvurulan derlemelerde türleri yeniden kullan** onay kutusu seçeneği, hizmet başvuru kodu oluşturma için gereken veri türleri projenizin Başvurulmuş derlemelerinden birinde tanımlandığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d179b-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="d179b-138">Derleme zamanı türü çakışmasına veya çalışma zamanı sorunlarından kaçınmak için bu mevcut veri türlerini yeniden kullanmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d179b-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="d179b-139">Proje bağımlılıklarının sayısına ve diğer sistem performansı faktörlere bağlı olarak tür bilgisi yüklenirken bir gecikme olabilir.</span><span class="sxs-lookup"><span data-stu-id="d179b-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="d179b-140">**Başvurulan derlemelerde türleri yeniden kullan** onay kutusu Işaretli değilse **son** düğmesi yükleme sırasında devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d179b-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="d179b-141">İşiniz bittiğinde **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d179b-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="d179b-142">İlerleme durumunu görüntülerken araç:</span><span class="sxs-lookup"><span data-stu-id="d179b-142">While displaying progress, the tool:</span></span>

* <span data-ttu-id="d179b-143">WCF hizmetinden meta verileri indirir.</span><span class="sxs-lookup"><span data-stu-id="d179b-143">Downloads metadata from the WCF service.</span></span>
* <span data-ttu-id="d179b-144">Hizmet başvuru kodunu *Reference.cs*adlı bir dosyada oluşturur ve **bağlı hizmetler** düğümü altında projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="d179b-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
* <span data-ttu-id="d179b-145">Hedef platformda derlemek ve çalıştırmak için gereken NuGet paket başvuruları ile proje dosyasını (. csproj) güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="d179b-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio Ilerleme penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="d179b-147">Bu işlemler tamamlandığında, oluşturulan WCF istemci türünün bir örneğini oluşturabilir ve hizmet işlemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d179b-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d179b-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d179b-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="d179b-149">Geri bildirim & soruları</span><span class="sxs-lookup"><span data-stu-id="d179b-149">Feedback & questions</span></span>

<span data-ttu-id="d179b-150">Sorularınız veya geri bildiriminiz varsa [GitHub ' da bir sorun açın](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="d179b-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="d179b-151">Ayrıca, [GitHub 'DAKI WCF](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)deposundaki mevcut soruları veya sorunları da inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d179b-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="d179b-152">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="d179b-152">Release notes</span></span>

* <span data-ttu-id="d179b-153">Bilinen sorunlar da dahil olmak üzere, güncelleştirilmiş sürüm bilgileri için [sürüm notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="d179b-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>

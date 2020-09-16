---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 58d720f164c4c35f3de4c282e9aa983d11e4040b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555230"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="8065c-102">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="8065c-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="8065c-103">Bu örnek, barındırma katmanının ad alanındaki sınıflarla tümleşmesini gösterir <xref:System.Web.Routing> .</span><span class="sxs-lookup"><span data-stu-id="8065c-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="8065c-104">Ad alanındaki sınıflar, <xref:System.Web.Routing> bir uygulamanın bir fiziksel kaynağa doğrudan karşılık gelen URL 'leri kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8065c-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="8065c-105">Web yönlendirme kullanımı, geliştiricinin daha sonra gerçek WCF hizmetlerine geri eşlenmiş HTTP için sanal adresler oluşturmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8065c-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="8065c-106">Bu, bir WCF hizmeti fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya. html veya. aspx gibi dosyalar içermeyen URL 'Ler ile erişilmesi gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="8065c-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="8065c-107">Bu örnek, <xref:System.Web.Routing.RouteTable> Global. asax içinde tanımlanan çalışan hizmetlerle eşlenen sanal URI 'ler oluşturmak için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8065c-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="8065c-108"><xref:System.Web.Routing>Ad alanındaki sınıflar yalnızca http üzerinden barındırılan hizmetler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="8065c-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="8065c-109">Bu örnek, iki RSS akışı oluşturmak için WCF kullanır: bir `movies` akış ve `channels` akış.</span><span class="sxs-lookup"><span data-stu-id="8065c-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="8065c-110">Hizmetleri etkinleştirmeye yönelik URL 'Ler bir uzantı içermez ve `Application_Start` `Global` sınıfından türetilen sınıfın yöntemine kaydedilir <xref:System.Web.HttpApplication> .</span><span class="sxs-lookup"><span data-stu-id="8065c-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8065c-111">Bu örnek yalnızca Internet Information Services (IIS) 7,0 ve üzeri sürümlerde çalışarak IIS 6,0, uzantı-daha seyrek URL 'Leri desteklemek için farklı bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="8065c-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="8065c-112">Bu örneği indirmek için</span><span class="sxs-lookup"><span data-stu-id="8065c-112">To download this sample</span></span>
  
<span data-ttu-id="8065c-113">Bu örnek bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8065c-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="8065c-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8065c-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="8065c-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8065c-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8065c-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8065c-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8065c-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8065c-117">To use this sample</span></span>  
  
1. <span data-ttu-id="8065c-118">Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="8065c-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="8065c-119">Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="8065c-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="8065c-120">Örnek için bir dizin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8065c-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="8065c-121">. Svc dosya uzantısına sahip bir dosya olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8065c-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="8065c-122">Adres çubuğunda `movies` URL 'ye ekleyin, böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8065c-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="8065c-123">Filmler akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8065c-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="8065c-124">Adres çubuğunda `channels` URL 'ye ekleyin, böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8065c-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="8065c-125">Kanallar akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8065c-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="8065c-126">ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="8065c-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="8065c-127">Geliştirme sunucusu çıkmadığından, bildirim alanı simgesine sağ tıklayın ve **Durdur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="8065c-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="8065c-128">IIS 'de barındırıldığında bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8065c-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="8065c-129">Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="8065c-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="8065c-130">CTRL + SHIFT + B tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="8065c-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="8065c-131">Internet Information Services (IIS) Yöneticisi 'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8065c-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="8065c-132">IIS Yöneticisi 'nde **varsayılan Web sitesine** sağ tıklayın ve **Uygulama Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="8065c-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="8065c-133">**Diğer ad**için, yazın `WebRoutingIntegration` .</span><span class="sxs-lookup"><span data-stu-id="8065c-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="8065c-134">**Fiziksel yol**için, projenin içindeki hizmet klasörünü seçin.</span><span class="sxs-lookup"><span data-stu-id="8065c-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="8065c-135">**Tamam**'a basın.</span><span class="sxs-lookup"><span data-stu-id="8065c-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="8065c-136">Web uygulamasına sağ tıklayıp **Uygulamayı Yönet** ' i seçerek uygulamayı başlatın ve sonra da ' yi **inceleyin**.</span><span class="sxs-lookup"><span data-stu-id="8065c-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="8065c-137">Adres çubuğunda `movies` URL 'ye ekleyin, böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8065c-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="8065c-138">Filmler akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8065c-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="8065c-139">Adres çubuğunda `channels` URL 'ye ekleyin, böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8065c-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="8065c-140">Kanallar akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8065c-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="8065c-141">ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="8065c-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="8065c-142">Bu örnek, barındırma katmanının <xref:System.Web.Routing> http üzerinden barındırılan hizmet isteklerini yönlendirmek için ad alanındaki sınıflarla birlikte oluşturma yeteneğine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8065c-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8065c-143">Sürüm 2 olarak ayarlandıysa, varsayılan uygulama havuzu sürümünü .NET Framework 4 ' e güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8065c-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8065c-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8065c-144">See also</span></span>

- <span data-ttu-id="8065c-145">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8065c-145">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

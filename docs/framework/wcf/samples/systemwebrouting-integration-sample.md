---
description: 'Daha fazla bilgi edinin: SystemWebRouting Integration Sample'
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 84b442dfb7f0e5877f742fb055aea49a5625bb78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668662"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="82e3f-103">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="82e3f-103">SystemWebRouting Integration Sample</span></span>

<span data-ttu-id="82e3f-104">Bu örnek, barındırma katmanının ad alanındaki sınıflarla tümleşmesini gösterir <xref:System.Web.Routing> .</span><span class="sxs-lookup"><span data-stu-id="82e3f-104">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="82e3f-105">Ad alanındaki sınıflar, <xref:System.Web.Routing> bir uygulamanın bir fiziksel kaynağa doğrudan karşılık gelen URL 'leri kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-105">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="82e3f-106">Web yönlendirme kullanımı, geliştiricinin daha sonra gerçek WCF hizmetlerine geri eşlenmiş HTTP için sanal adresler oluşturmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-106">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="82e3f-107">Bu, bir WCF hizmeti fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya. html veya. aspx gibi dosyalar içermeyen URL 'Ler ile erişilmesi gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="82e3f-107">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="82e3f-108">Bu örnek, <xref:System.Web.Routing.RouteTable> Global. asax içinde tanımlanan çalışan hizmetlerle eşlenen sanal URI 'ler oluşturmak için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-108">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="82e3f-109"><xref:System.Web.Routing>Ad alanındaki sınıflar yalnızca http üzerinden barındırılan hizmetler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="82e3f-109">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="82e3f-110">Bu örnek, iki RSS akışı oluşturmak için WCF kullanır: bir `movies` akış ve `channels` akış.</span><span class="sxs-lookup"><span data-stu-id="82e3f-110">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="82e3f-111">Hizmetleri etkinleştirmeye yönelik URL 'Ler bir uzantı içermez ve `Application_Start` `Global` sınıfından türetilen sınıfın yöntemine kaydedilir <xref:System.Web.HttpApplication> .</span><span class="sxs-lookup"><span data-stu-id="82e3f-111">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82e3f-112">Bu örnek yalnızca Internet Information Services (IIS) 7,0 ve üzeri sürümlerde çalışarak IIS 6,0, uzantı-daha seyrek URL 'Leri desteklemek için farklı bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="82e3f-112">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="82e3f-113">Bu örneği indirmek için</span><span class="sxs-lookup"><span data-stu-id="82e3f-113">To download this sample</span></span>
  
<span data-ttu-id="82e3f-114">Bu örnek bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-114">This sample may already be installed on your computer.</span></span> <span data-ttu-id="82e3f-115">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="82e3f-115">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="82e3f-116">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="82e3f-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82e3f-117">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="82e3f-117">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="82e3f-118">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="82e3f-118">To use this sample</span></span>  
  
1. <span data-ttu-id="82e3f-119">Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-119">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="82e3f-120">Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-120">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="82e3f-121">Örnek için bir dizin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-121">A directory listing for the sample appears.</span></span> <span data-ttu-id="82e3f-122">. Svc dosya uzantısına sahip bir dosya olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-122">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="82e3f-123">Adres çubuğunda `movies` URL 'ye ekleyin, böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-123">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="82e3f-124">Filmler akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-124">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="82e3f-125">Adres çubuğunda `channels` URL 'ye ekleyin, böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-125">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="82e3f-126">Kanallar akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-126">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="82e3f-127">ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-127">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="82e3f-128">Geliştirme sunucusu çıkmadığından, bildirim alanı simgesine sağ tıklayın ve **Durdur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="82e3f-128">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="82e3f-129">IIS 'de barındırıldığında bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="82e3f-129">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="82e3f-130">Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-130">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="82e3f-131">CTRL + SHIFT + B tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="82e3f-131">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="82e3f-132">Internet Information Services (IIS) Yöneticisi 'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82e3f-132">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="82e3f-133">IIS Yöneticisi 'nde **varsayılan Web sitesine** sağ tıklayın ve **Uygulama Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="82e3f-133">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="82e3f-134">**Diğer ad** için, yazın `WebRoutingIntegration` .</span><span class="sxs-lookup"><span data-stu-id="82e3f-134">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="82e3f-135">**Fiziksel yol** için, projenin içindeki hizmet klasörünü seçin.</span><span class="sxs-lookup"><span data-stu-id="82e3f-135">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="82e3f-136">**Tamam**'a basın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-136">Press **OK**.</span></span>  
  
4. <span data-ttu-id="82e3f-137">Web uygulamasına sağ tıklayıp **Uygulamayı Yönet** ' i seçerek uygulamayı başlatın ve sonra da ' yi **inceleyin**.</span><span class="sxs-lookup"><span data-stu-id="82e3f-137">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="82e3f-138">Adres çubuğunda `movies` URL 'ye ekleyin, böylece okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-138">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="82e3f-139">Filmler akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-139">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="82e3f-140">Adres çubuğunda `channels` URL 'ye ekleyin, böylece okur `http://localhost:[port]/channels` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-140">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="82e3f-141">Kanallar akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-141">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="82e3f-142">ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="82e3f-142">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="82e3f-143">Bu örnek, barındırma katmanının <xref:System.Web.Routing> http üzerinden barındırılan hizmet isteklerini yönlendirmek için ad alanındaki sınıflarla birlikte oluşturma yeteneğine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-143">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82e3f-144">Sürüm 2 olarak ayarlandıysa, varsayılan uygulama havuzu sürümünü .NET Framework 4 ' e güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82e3f-144">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e3f-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e3f-145">See also</span></span>

- <span data-ttu-id="82e3f-146">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="82e3f-146">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

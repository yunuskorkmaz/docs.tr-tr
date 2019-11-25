---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: def876b13fdc938970e02d63febedf39a240ebac
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141841"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="7fcd1-102">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="7fcd1-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="7fcd1-103">Bu örnek, barındırma katmanının <xref:System.Web.Routing> ad alanındaki sınıflarla tümleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="7fcd1-104"><xref:System.Web.Routing> ad alanındaki sınıflar, bir uygulamanın bir fiziksel kaynağa doğrudan karşılık gelen URL 'Leri kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="7fcd1-105">Web yönlendirme kullanımı, geliştiricinin daha sonra gerçek WCF hizmetlerine geri eşlenmiş HTTP için sanal adresler oluşturmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="7fcd1-106">Bu, bir WCF hizmeti fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya. html veya. aspx gibi dosyalar içermeyen URL 'Ler ile erişilmesi gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="7fcd1-107">Bu örnek, Global. asax içinde tanımlanan çalışan hizmetlerle eşlenen sanal URI 'Ler oluşturmak için <xref:System.Web.Routing.RouteTable> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
> <span data-ttu-id="7fcd1-108"><xref:System.Web.Routing> ad alanındaki sınıflar yalnızca HTTP üzerinden barındırılan hizmetler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="7fcd1-109">Bu örnek, iki RSS akışı oluşturmak için WCF kullanır: bir `movies` akışı ve `channels` akışı.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="7fcd1-110">Hizmetleri etkinleştirmeye yönelik URL 'Ler bir uzantı içermez ve <xref:System.Web.HttpApplication> sınıfından türetilen `Global` sınıfının `Application_Start` metoduna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fcd1-111">Bu örnek yalnızca Internet Information Services (IIS) 7,0 ve üzeri sürümlerde çalışarak IIS 6,0, uzantı-daha seyrek URL 'Leri desteklemek için farklı bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="7fcd1-112">Bu örneği indirmek için</span><span class="sxs-lookup"><span data-stu-id="7fcd1-112">To download this sample</span></span>
  
<span data-ttu-id="7fcd1-113">Bu örnek bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="7fcd1-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="7fcd1-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7fcd1-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7fcd1-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7fcd1-117">To use this sample</span></span>  
  
1. <span data-ttu-id="7fcd1-118">Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="7fcd1-119">Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="7fcd1-120">Örnek için bir dizin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="7fcd1-121">. Svc dosya uzantısına sahip bir dosya olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="7fcd1-122">Adres çubuğunda URL 'ye `movies` ekleyin, böylece `http://localhost:[port]/movies` okuyup ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="7fcd1-123">Filmler akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="7fcd1-124">Adres çubuğunda URL 'ye `channels` ekleyin, böylece `http://localhost:[port]/channels` okur ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="7fcd1-125">Kanallar akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="7fcd1-126">ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="7fcd1-127">Geliştirme sunucusu çıkmadığından, bildirim alanı simgesine sağ tıklayın ve **Durdur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="7fcd1-128">IIS 'de barındırıldığında bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7fcd1-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="7fcd1-129">Visual Studio 'yu kullanarak WebRoutingIntegration. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="7fcd1-130">CTRL + SHIFT + B tuşlarına basarak projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="7fcd1-131">Internet Information Services (IIS) Yöneticisi 'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="7fcd1-132">IIS Yöneticisi 'nde **varsayılan Web sitesine** sağ tıklayın ve **Uygulama Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="7fcd1-133">**Diğer ad**için `WebRoutingIntegration`yazın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="7fcd1-134">**Fiziksel yol**için, projenin içindeki hizmet klasörünü seçin.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="7fcd1-135">**Tamam**'a basın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="7fcd1-136">Web uygulamasına sağ tıklayıp **Uygulamayı Yönet** ' i seçerek uygulamayı başlatın ve sonra da ' yi **inceleyin**.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="7fcd1-137">Adres çubuğunda URL 'ye `movies` ekleyin, böylece `http://localhost:[port]/movies` okur ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="7fcd1-138">Filmler akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="7fcd1-139">Adres çubuğunda URL 'ye `channels` ekleyin, böylece `http://localhost:[port]/channels` okur ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="7fcd1-140">Kanallar akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="7fcd1-141">ALT + F4 tuşlarına basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="7fcd1-142">Bu örnek, barındırma katmanının, HTTP üzerinden barındırılan hizmetlerin isteklerini yönlendirmek için <xref:System.Web.Routing> ad alanındaki sınıflarla oluşturma yeteneğine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fcd1-143">Sürüm 2 olarak ayarlandıysa, varsayılan uygulama havuzu sürümünü .NET Framework 4 ' e güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fcd1-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fcd1-144">See also</span></span>

- [<span data-ttu-id="7fcd1-145">AppFabric barındırma ve kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="7fcd1-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

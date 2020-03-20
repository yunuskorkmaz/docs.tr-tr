---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143960"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="6e964-102">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="6e964-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="6e964-103">Bu örnek, barındırma katmanının ad alanındaki sınıflarla tümleştirmesini <xref:System.Web.Routing> gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e964-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="6e964-104">Ad alanındaki <xref:System.Web.Routing> sınıflar, bir uygulamanın fiziksel kaynağa doğrudan karşılık olmayan URL'leri kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6e964-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="6e964-105">Web yönlendirmesi kullanmak, geliştiricinin HTTP için gerçek WCF hizmetlerine eşlenen sanal adresler oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6e964-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="6e964-106">Bu, bir WCF hizmetinin fiziksel bir dosya veya kaynak gerektirmeden barındırılması gerektiğinde veya hizmetlere .html veya .aspx gibi dosyalar içermeyen URL'lerle erişilmesi gerektiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e964-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="6e964-107">Bu örnek, global.asax'ta tanımlanan hizmetleri çalıştırmak için eşharitasını alan sanal URL'ler oluşturmak için sınıfın nasıl kullanılacağını <xref:System.Web.Routing.RouteTable> gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e964-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="6e964-108"><xref:System.Web.Routing> Ad alanındaki sınıflar yalnızca HTTP üzerinden barındırılan hizmetler için çalışır.</span><span class="sxs-lookup"><span data-stu-id="6e964-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="6e964-109">Bu örnekte wcf iki RSS akışı `movies` oluşturmak `channels` için kullanır: bir besleme ve bir besleme.</span><span class="sxs-lookup"><span data-stu-id="6e964-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="6e964-110">Hizmetleri etkinleştirmek için URL'ler bir uzantı içermez `Application_Start` ve `Global` <xref:System.Web.HttpApplication> sınıftan türetilen sınıfın yöntemine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6e964-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e964-111">Bu örnek yalnızca Internet Information Services (IIS) 7.0 ve sonraki yerlerde çalışır, çünkü IIS 6.0 uzantısız URL'leri desteklemek için farklı bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e964-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="6e964-112">Bu örneği indirmek için</span><span class="sxs-lookup"><span data-stu-id="6e964-112">To download this sample</span></span>
  
<span data-ttu-id="6e964-113">Bu örnek bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e964-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="6e964-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6e964-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="6e964-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="6e964-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e964-116">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e964-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6e964-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6e964-117">To use this sample</span></span>  
  
1. <span data-ttu-id="6e964-118">Visual Studio'yu kullanarak WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6e964-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="6e964-119">Çözümü çalıştırmak ve Web geliştirme sunucusunu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6e964-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="6e964-120">Örnek için bir dizin listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e964-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="6e964-121">.svc dosya uzantısı olan dosya olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e964-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="6e964-122">Adres çubuğunda URL'ye ekleyin, `movies` böylece `http://localhost:[port]/movies` okuyup ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6e964-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="6e964-123">Film akışı tarayıcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="6e964-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="6e964-124">Adres çubuğunda URL'ye ekleyin, `channels` böylece `http://localhost:[port]/channels` okunacak ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6e964-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="6e964-125">Kanal akışı tarayıcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="6e964-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="6e964-126">ALT+F4 tuşuna basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="6e964-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="6e964-127">Geliştirme sunucusu çıkmamışsa, bildirim alanı simgesine sağ tıklayın ve **Durdur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="6e964-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="6e964-128">IIS'de barındırıldığında bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6e964-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="6e964-129">Visual Studio'yu kullanarak WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6e964-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="6e964-130">CTRL+SHIFT+B tuşuna basarak projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6e964-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="6e964-131">Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6e964-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="6e964-132">IIS Manager'da **Varsayılan Web Sitesi'ni** sağ tıklatın ve **Uygulama Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="6e964-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="6e964-133">Takma **ad**için , `WebRoutingIntegration`yazın .</span><span class="sxs-lookup"><span data-stu-id="6e964-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="6e964-134">Fiziksel **Yol**için, proje içindeki Hizmet klasörünü seçin.</span><span class="sxs-lookup"><span data-stu-id="6e964-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="6e964-135">**Tamam**'a basın.</span><span class="sxs-lookup"><span data-stu-id="6e964-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="6e964-136">Web uygulamasını sağ tıklayarak ve **Uygulamayı Yönet'i** seçerek uygulamayı başlatın ve ardından **Gözat.**</span><span class="sxs-lookup"><span data-stu-id="6e964-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="6e964-137">Adres çubuğunda URL'ye ekleyin, `movies` böylece `http://localhost:[port]/movies` okunacak ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6e964-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="6e964-138">Film akışı tarayıcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="6e964-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="6e964-139">Adres çubuğunda URL'ye ekleyin, `channels` böylece `http://localhost:[port]/channels` okunacak ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6e964-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="6e964-140">Kanal akışı tarayıcıda görünür.</span><span class="sxs-lookup"><span data-stu-id="6e964-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="6e964-141">ALT+F4 tuşuna basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="6e964-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="6e964-142">Bu örnek, barındırma katmanının http üzerinden barındırılan <xref:System.Web.Routing> hizmetlerin isteklerini yönlendirmek için ad alanındaki sınıflarla birlikte beste yapabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6e964-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e964-143">Sürüm 2 olarak ayarlanmışsa varsayılan uygulama havuzu sürümünü .NET Framework 4 olarak güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e964-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e964-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e964-144">See also</span></span>

- <span data-ttu-id="6e964-145">[AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6e964-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

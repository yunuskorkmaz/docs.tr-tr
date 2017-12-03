---
title: "SystemWebRouting Tümleştirme Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c38c7af4988e6e47ee307f5cd7a8b6733b043a7c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="863c2-102">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="863c2-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="863c2-103">Bu örnek sınıflar ile barındırma katmanın tümleştirme gösterir <xref:System.Web.Routing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="863c2-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="863c2-104">Sınıflarda <xref:System.Web.Routing> ad alanı izin doğrudan fiziksel bir kaynağa karşılık gelmeyen URL'leri kullanmak bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="863c2-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="863c2-105">Web yönlendirme kullanarak sağlar sonra geri gerçek eşlenen HTTP için sanal adres oluşturmak üzere Geliştirici [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="863c2-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="863c2-106">Bu, bir WCF Hizmeti gerektirmeden fiziksel dosya veya kaynak barındırılan gerekir ya da hizmetleri .html veya .aspx gibi dosya içermediğini URL'ler ile erişilmesi gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="863c2-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="863c2-107">Bu örnek nasıl kullanılacağını gösteren <xref:System.Web.Routing.RouteTable> sanal URI'ler global.asax dosyasında tanımlanmış hizmetlerini çalıştırmak için bu harita oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="863c2-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="863c2-108">Bu örnekte, WCF kullanılarak oluşturulan iki RSS akışları vardır: bir `movies` akış ve `channels` akış.</span><span class="sxs-lookup"><span data-stu-id="863c2-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="863c2-109">Hizmetleri etkinleştirmek için URL'leri bir uzantıyı içermeyen ve kayıtlı `Application_Start` yöntemi `Global` türetilmiş sınıf <xref:System.Web.HttpApplication.Application_Start> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="863c2-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="863c2-110">Sınıflarda <xref:System.Web.Routing> ad alanı yalnızca çalışmak için HTTP üzerinden barındırılan hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="863c2-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="863c2-111">Bu örnek yalnızca çalışır [!INCLUDE[iisver](../../../../includes/iisver-md.md)], olarak [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uzantısız URL'lerin desteklemek için farklı bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="863c2-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="863c2-112">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="863c2-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="863c2-113">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="863c2-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="863c2-114">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="863c2-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="863c2-115">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="863c2-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="863c2-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="863c2-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="863c2-117">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="863c2-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="863c2-118">Çözümü çalıştırın ve Web geliştirme sunucusu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="863c2-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="863c2-119">Bir dizin için örnek listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="863c2-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="863c2-120">Hiçbir dosya .svc dosya uzantısına sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="863c2-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="863c2-121">Adres çubuğunda eklemek `movies` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / filmler ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="863c2-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="863c2-122">Film akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="863c2-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="863c2-123">Adres çubuğunda eklemek `channels` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / Kanallar ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="863c2-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="863c2-124">Kanallar akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="863c2-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="863c2-125">Web tarayıcısı ALT + F4 tuşlarına basarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="863c2-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="863c2-126">Geliştirme Sunucusu yaptı değil, bildirim alanı simgesini sağ tıklatın ve seçin **durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="863c2-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="863c2-127">IIS içinde barındırıldığında Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="863c2-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="863c2-128">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="863c2-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="863c2-129">CTRL + SHIFT + B tuşuna basarak projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="863c2-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="863c2-130">Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="863c2-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="863c2-131">IIS Yöneticisi'nde sağ tıklayın **varsayılan Web sitesi** seçip **bir uygulama eklemek**.</span><span class="sxs-lookup"><span data-stu-id="863c2-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="863c2-132">İçin **diğer**, yazın `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="863c2-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="863c2-133">İçin **fiziksel yolu**, proje içindeki hizmeti klasörünü seçin.</span><span class="sxs-lookup"><span data-stu-id="863c2-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="863c2-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="863c2-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="863c2-135">Web uygulaması sağ tıklayıp seçerek uygulamayı başlatmak **yönetmek uygulama** ve ardından **Gözat**.</span><span class="sxs-lookup"><span data-stu-id="863c2-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="863c2-136">Adres çubuğunda eklemek `movies` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / filmler ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="863c2-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="863c2-137">Film akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="863c2-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="863c2-138">Adres çubuğunda eklemek `channels` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / Kanallar ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="863c2-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="863c2-139">Kanallar akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="863c2-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="863c2-140">Web tarayıcısı ALT + F4 tuşlarına basarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="863c2-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="863c2-141">Bu örnek barındırma katman içindeki sınıflarla oluşturma kapasitesine sahip olduğunu gösteren <xref:System.Web.Routing> HTTP üzerinden barındırılan hizmetleri istekleri yönlendirme için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="863c2-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="863c2-142">Lütfen varsayılan uygulama havuzunu sürüme güncelleştirin [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] sürüm 2 ayarlarsanız.</span><span class="sxs-lookup"><span data-stu-id="863c2-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863c2-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="863c2-143">See Also</span></span>  
 [<span data-ttu-id="863c2-144">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="863c2-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

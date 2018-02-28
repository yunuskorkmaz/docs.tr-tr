---
title: "SystemWebRouting Tümleştirme Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de8869956a59cb47623dbc4d84763e19d6f181bf
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="44bae-102">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="44bae-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="44bae-103">Bu örnek sınıflar ile barındırma katmanın tümleştirme gösterir <xref:System.Web.Routing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="44bae-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="44bae-104">Sınıflarda <xref:System.Web.Routing> ad alanı izin doğrudan fiziksel bir kaynağa karşılık gelmeyen URL'leri kullanmak bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="44bae-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="44bae-105">Web yönlendirme kullanarak sağlar sonra geri gerçek eşlenen HTTP için sanal adres oluşturmak üzere Geliştirici [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="44bae-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="44bae-106">Bu, bir WCF Hizmeti gerektirmeden fiziksel dosya veya kaynak barındırılan gerekir ya da hizmetleri .html veya .aspx gibi dosya içermediğini URL'ler ile erişilmesi gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="44bae-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="44bae-107">Bu örnek nasıl kullanılacağını gösteren <xref:System.Web.Routing.RouteTable> sanal URI'ler global.asax dosyasında tanımlanmış hizmetlerini çalıştırmak için bu harita oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44bae-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
>  <span data-ttu-id="44bae-108">Sınıflarda <xref:System.Web.Routing> ad alanı yalnızca çalışmak için HTTP üzerinden barındırılan hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="44bae-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="44bae-109">Bu örnek iki RSS akışları oluşturmak için WCF kullanır: bir `movies` akış ve `channels` akış.</span><span class="sxs-lookup"><span data-stu-id="44bae-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="44bae-110">Hizmetleri etkinleştirmek için URL'leri bir uzantıyı içermeyen ve kayıtlı `Application_Start` yöntemi `Global` türetilmiş sınıf <xref:System.Web.HttpApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44bae-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44bae-111">Bu örnek yalnızca Internet Information Services (IIS) 7.0 çalışır ve daha sonra IIS 6. 0 ' farklı bir yöntem uzantısız URL'lerin desteklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="44bae-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="44bae-112">Bu örnek karşıdan yüklemek için</span><span class="sxs-lookup"><span data-stu-id="44bae-112">To download this sample</span></span>
  
<span data-ttu-id="44bae-113">Bu örnek, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="44bae-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="44bae-114">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="44bae-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="44bae-115">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="44bae-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44bae-116">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="44bae-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="44bae-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="44bae-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="44bae-118">Visual Studio kullanarak WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="44bae-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="44bae-119">Çözümü çalıştırın ve Web geliştirme sunucusu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="44bae-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="44bae-120">Bir dizin için örnek listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44bae-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="44bae-121">Hiçbir dosya .svc dosya uzantısına sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="44bae-121">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="44bae-122">Adres çubuğunda eklemek `movies` URL'si, bu nedenle, BT'nin okur http://localhost: [bağlantı noktası] / filmler ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="44bae-122">In the address bar, add `movies` to the URL, so that it reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="44bae-123">Film akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44bae-123">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="44bae-124">Adres çubuğunda eklemek `channels` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / Kanallar ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="44bae-124">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="44bae-125">Kanallar akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44bae-125">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="44bae-126">Web tarayıcısı ALT + F4 tuşlarına basarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="44bae-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="44bae-127">Geliştirme Sunucusu yaptı değil, bildirim alanı simgesini sağ tıklatın ve seçin **durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="44bae-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="44bae-128">IIS içinde barındırıldığında Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="44bae-128">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="44bae-129">Visual Studio kullanarak WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="44bae-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="44bae-130">CTRL + SHIFT + B tuşuna basarak projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44bae-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="44bae-131">Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="44bae-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="44bae-132">IIS Yöneticisi'nde sağ tıklayın **varsayılan Web sitesi** seçip **bir uygulama eklemek**.</span><span class="sxs-lookup"><span data-stu-id="44bae-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="44bae-133">İçin **diğer**, yazın `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="44bae-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="44bae-134">İçin **fiziksel yolu**, proje içindeki hizmeti klasörünü seçin.</span><span class="sxs-lookup"><span data-stu-id="44bae-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="44bae-135">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="44bae-135">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="44bae-136">Web uygulaması sağ tıklayıp seçerek uygulamayı başlatmak **yönetmek uygulama** ve ardından **Gözat**.</span><span class="sxs-lookup"><span data-stu-id="44bae-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="44bae-137">Adres çubuğunda eklemek `movies` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / filmler ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="44bae-137">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="44bae-138">Film akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44bae-138">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="44bae-139">Adres çubuğunda eklemek `channels` URL'si, bu nedenle olan okuma http://localhost: [bağlantı noktası] / Kanallar ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="44bae-139">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="44bae-140">Kanallar akış tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44bae-140">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="44bae-141">Web tarayıcısı ALT + F4 tuşlarına basarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="44bae-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="44bae-142">Bu örnek barındırma katman içindeki sınıflarla oluşturma kapasitesine sahip olduğunu gösteren <xref:System.Web.Routing> HTTP üzerinden barındırılan hizmetleri istekleri yönlendirme için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="44bae-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44bae-143">Varsayılan uygulama havuzunu sürüme güncelleştirmelisiniz [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] sürüm 2 ayarlarsanız.</span><span class="sxs-lookup"><span data-stu-id="44bae-143">You must update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bae-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44bae-144">See Also</span></span>  
 [<span data-ttu-id="44bae-145">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="44bae-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

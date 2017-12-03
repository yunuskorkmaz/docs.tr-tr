---
title: "Dinamik Yeniden Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3146da86dcbe22f72ebedec57c87ac0a29ed1946
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="6010c-102">Dinamik Yeniden Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6010c-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="6010c-103">Bu örnek gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="6010c-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="6010c-104">Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6010c-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="6010c-105">Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hesaplayıcı yönlendirme hizmeti kullanarak iletişim kurmak için örnek.</span><span class="sxs-lookup"><span data-stu-id="6010c-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="6010c-106">Bu örnek nasıl yönlendirme hizmeti dinamik olarak çalışma zamanı sırasında yeniden yapılandırılabilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="6010c-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6010c-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="6010c-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6010c-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6010c-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6010c-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6010c-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6010c-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6010c-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="6010c-111">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="6010c-111">Sample Details</span></span>  
 <span data-ttu-id="6010c-112">Yönlendirme hizmeti çalışma zamanı sırasında dinamik olarak yapılandırmak için bu örnek yeni bir oluşturur beş saniyede bir süreölçer harekete <xref:System.ServiceModel.Routing.RoutingConfiguration> nesne ve uygular.</span><span class="sxs-lookup"><span data-stu-id="6010c-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="6010c-113">Bu yapılandırma, normal hesaplayıcı uç nokta veya yuvarlama hesaplayıcı endpoint başvurur.</span><span class="sxs-lookup"><span data-stu-id="6010c-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="6010c-114">Bir hizmeti veya diğer, yönlendirme hizmeti hangisinin bağlı olarak yapılandırılmış döndürülen kendi iletileri hesaplayıcı istemci uygulaması olan o zaman için rota.</span><span class="sxs-lookup"><span data-stu-id="6010c-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="6010c-115">Yönlendirme hizmetin capabilitiy özel bir davranış aracılığıyla dinamik yeniden yapılandırılması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6010c-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="6010c-116">Bu özel davranışı için bir geri çağırma edilir beş saniyede tetiklenen basit iş parçacığı süreölçer içeren bir hizmet uzantısı ekler `UpdateRules` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6010c-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="6010c-117">Bu geri çağırma oluşturur ve yeni yönlendirme yapılandırması uygular.</span><span class="sxs-lookup"><span data-stu-id="6010c-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="6010c-118">Gerçek bir dağıtımda bulunan bu geri çağırma sonucunda başka türden bir olay, bir SQL olay bildirim ya da bir WS-bulma Duyurusu gibi büyük olasılıkla gerçekleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="6010c-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6010c-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6010c-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="6010c-120">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], DynamicReconfiguration.sln açın.</span><span class="sxs-lookup"><span data-stu-id="6010c-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="6010c-121">Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="6010c-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="6010c-122">Tuşuna **F5** veya **CTRL + SHIFT + B** içinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6010c-122">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="6010c-123">Otomatik gerekli projeleri bastığınızda başlatılan isteyip **F5**, çözüme sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6010c-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="6010c-124">Seçin **başlangıç projesi** düğümü altında **ortak özellikleri** sol bölmede.</span><span class="sxs-lookup"><span data-stu-id="6010c-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="6010c-125">Seçin **birden fazla başlangıç projesi** radyo düğmesinin ve tüm projeleri için ayarlanmış **Başlat** eylem.</span><span class="sxs-lookup"><span data-stu-id="6010c-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="6010c-126">Proje ile yapı **CTRL + SHIFT + B**, aşağıdaki uygulamalar başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6010c-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="6010c-127">Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="6010c-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="6010c-128">Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="6010c-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="6010c-129">Yönlendirme hesap makinesi hizmetinin (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="6010c-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="6010c-130">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="6010c-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="6010c-131">Hesaplayıcı istemci konsol penceresinde istemci başlatmak ve hesaplayıcı hizmet işlemlerini çağırma için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6010c-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="6010c-132">Yönlendirme hizmeti iletileri yuvarlama hesaplayıcı ve normal hesaplayıcı dönüşümlü yönlendirme yapılandırması değişiklikleri dinamik olarak beş saniyede yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="6010c-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="6010c-133">Yönlendirme hizmeti ileti göndermek için yapılandırılan hangi uç noktası bağlı olarak farklı çıkışları istemci konsol penceresinde vardır.</span><span class="sxs-lookup"><span data-stu-id="6010c-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="6010c-134">Sürekli olarak beş saniyeden fazla ENTER tuşuna basarak devam ve hizmet sonuçlarından değişikliği gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="6010c-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="6010c-135">Yönlendirici hizmeti yuvarlama hesaplayıcı hizmetine iletileri yönlendirmek üzere yapılandırılırsa çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6010c-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="6010c-136">Yönlendirme hizmeti normal hesaplayıcı hizmetine iletileri yönlendirmek üzere yapılandırılırsa çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6010c-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="6010c-137">Hesaplayıcı hizmeti ve yuvarlama hesaplayıcı hizmeti ilgili konsol pencerelerini çağrılan işlemlerinin bir günlük çıkışı da yazdırın.</span><span class="sxs-lookup"><span data-stu-id="6010c-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="6010c-138">İstemci konsol penceresinde "Çık" yazın ve ENTER tuşuna basarak çıkın.</span><span class="sxs-lookup"><span data-stu-id="6010c-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="6010c-139">Hizmetler konsolunda Windows Hizmetleri sonlandırmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6010c-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="6010c-140">Senaryo</span><span class="sxs-lookup"><span data-stu-id="6010c-140">Scenario</span></span>  
 <span data-ttu-id="6010c-141">Bu örnek, birden çok türleri veya hizmetleri uygulaması bir uç noktası aracılığıyla açığa çıkarılması izin vererek içerik tabanlı bir yönlendirici işlevi gören yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="6010c-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="6010c-142">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="6010c-142">Real World Scenario</span></span>  
 <span data-ttu-id="6010c-143">Contoso tüm genel olarak, bunlar birden çok farklı türlerdeki Hizmetleri için erişim sunar tek bir uç nokta kullanıma sunmak için kendi Hizmetleri sanallaştırmayı istiyor.</span><span class="sxs-lookup"><span data-stu-id="6010c-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="6010c-144">Bu durumda, gelen isteklerin gönderilmesi gerektiğini belirlemek için yönlendirme hizmetin içerik tabanlı Yönlendirme yetenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="6010c-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6010c-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6010c-145">See Also</span></span>  
 [<span data-ttu-id="6010c-146">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="6010c-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

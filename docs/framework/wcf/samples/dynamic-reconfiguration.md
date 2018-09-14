---
title: Dinamik Yeniden Yapılandırma
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508215"
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="fa1dd-102">Dinamik Yeniden Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa1dd-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="fa1dd-103">Bu örnek, Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="fa1dd-104">Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="fa1dd-105">Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-105">This sample adapts the standard WCF Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="fa1dd-106">Bu örnek nasıl yönlendirme hizmeti dinamik olarak çalışma zamanı sırasında yapılandırılabilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa1dd-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fa1dd-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fa1dd-109">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa1dd-110">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="fa1dd-111">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="fa1dd-111">Sample Details</span></span>  
 <span data-ttu-id="fa1dd-112">Yönlendirme hizmeti çalışma zamanı sırasında dinamik olarak yeniden yapılandırmak için bu örnek yeni bir oluşturur her beş saniyede bir zamanlayıcı harekete <xref:System.ServiceModel.Routing.RoutingConfiguration> nesne ve uygular.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="fa1dd-113">Bu yapılandırma, normal hesaplayıcı uç nokta veya yuvarlama hesaplayıcı uç nokta başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="fa1dd-114">Hesaplayıcı istemci uygulaması sahip bir hizmet veya diğer, yönlendirme hizmeti hangisinin bağlı olarak yapılandırılmış döndürülen iletileri yönlendirmek için o zaman.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="fa1dd-115">Yönlendirme hizmetin capabilitiy dinamik yeniden yapılandırma yoluyla özel bir davranış için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="fa1dd-116">Bu özel davranışı için bir geri çağırma sonuçlanır her beş saniyede tetiklenen basit bir iş parçacığı Zamanlayıcı içeren bir hizmet uzantısı ekler `UpdateRules` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="fa1dd-117">Bu geri çağırma oluşturur ve bu yeni yönlendirme yapılandırması uygular.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="fa1dd-118">Gerçek bir dağıtımda, bu geri çağırma büyük olasılıkla başka türde bir SQL olay bildirimi ya da bir WS-bulma Duyurusu gibi bir olay sonucunda ulaşılacağına.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fa1dd-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fa1dd-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="fa1dd-120">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], DynamicReconfiguration.sln açın.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="fa1dd-121">Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="fa1dd-122">Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="fa1dd-123">Bunu otomatik gerekli projeleri bastığınızda başlatma isterseniz **F5**, çözümü sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="fa1dd-124">Seçin **başlangıç projesi** düğümünde **ortak özellikler** sol bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="fa1dd-125">Seçin **birden fazla başlangıç projesi** radyo düğmesini ve tüm projeler için **Başlat** eylem.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="fa1dd-126">Projesiyle yapı **CTRL + SHIFT + B**, şu uygulamalar başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="fa1dd-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="fa1dd-127">Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="fa1dd-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="fa1dd-128">Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="fa1dd-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="fa1dd-129">Yönlendirme hesaplayıcı hizmeti (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="fa1dd-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="fa1dd-130">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="fa1dd-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="fa1dd-131">Konsol penceresinde hesaplayıcı istemcinin, istemci başlatmak ve hesaplayıcı hizmet işlemlerini aramak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="fa1dd-132">Yönlendirme hizmeti iletileri yuvarlama hesaplayıcı ve normal hesaplayıcı için alternatif yönlendirme yapılandırma değişiklikleri dinamik olarak beş saniyede yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="fa1dd-133">Yönlendirme hizmeti, ileti göndermek için yapılandırılır hangi uç noktaya bağlı olarak farklı çıkış istemci konsol penceresinde vardır.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="fa1dd-134">Sürekli olarak beş saniyeden fazla ENTER tuşuna basarak devam edin ve sonuçları hizmetinden değişiklik gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="fa1dd-135">Yönlendirici hizmeti iletileri yuvarlama hesaplayıcı hizmetine yönlendirmek üzere yapılandırılmışsa çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="fa1dd-136">Yönlendirme hizmeti iletileri normal hesaplayıcı hizmetine yönlendirmek üzere yapılandırılmışsa çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="fa1dd-137">Hesaplayıcı hizmetini ve yuvarlama hesaplayıcı hizmetini de ilgili konsol pencerelerini çağrılan işlem günlüğünü dışarı yazdırın.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="fa1dd-138">İstemci konsol penceresinde "Çık" yazın ve çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="fa1dd-139">Hizmetleri sonlandırmak için hizmetler Konsolu pencerelerinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="fa1dd-140">Senaryo</span><span class="sxs-lookup"><span data-stu-id="fa1dd-140">Scenario</span></span>  
 <span data-ttu-id="fa1dd-141">Bu örnek, birden çok türleri veya uygulama hizmetleri bir uç nokta sağlamak ve içerik tabanlı bir yönlendirici görevi gören yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="fa1dd-142">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="fa1dd-142">Real World Scenario</span></span>  
 <span data-ttu-id="fa1dd-143">Contoso tüm genel olarak, birden çok farklı türlerdeki Hizmetleri erişim sundukları tek bir uç nokta kullanıma sunmak için kendi hizmetlerini sanallaştırılması istemektedir.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="fa1dd-144">Bu durumda, gelen istekleri nereye gönderileceğini belirlemek için yönlendirme hizmetin içerik tabanlı yönlendirme becerilerinden.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1dd-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa1dd-145">See Also</span></span>  
 [<span data-ttu-id="fa1dd-146">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="fa1dd-146">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

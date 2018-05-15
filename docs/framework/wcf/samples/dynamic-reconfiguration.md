---
title: Dinamik Yeniden Yapılandırma
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: 81a2b494c48476e683053e12e58264e756201124
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="8a4be-102">Dinamik Yeniden Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8a4be-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="8a4be-103">Bu örnek Windows Communication Foundation (WCF) yönlendirme hizmeti gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="8a4be-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="8a4be-104">Yönlendirme hizmeti, içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştıran bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="8a4be-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="8a4be-105">Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a4be-105">This sample adapts the standard WCF Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="8a4be-106">Bu örnek nasıl yönlendirme hizmeti dinamik olarak çalışma zamanı sırasında yeniden yapılandırılabilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a4be-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a4be-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="8a4be-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8a4be-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a4be-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8a4be-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8a4be-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a4be-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8a4be-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="8a4be-111">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="8a4be-111">Sample Details</span></span>  
 <span data-ttu-id="8a4be-112">Yönlendirme hizmeti çalışma zamanı sırasında dinamik olarak yapılandırmak için bu örnek yeni bir oluşturur beş saniyede bir süreölçer harekete <xref:System.ServiceModel.Routing.RoutingConfiguration> nesne ve uygular.</span><span class="sxs-lookup"><span data-stu-id="8a4be-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="8a4be-113">Bu yapılandırma, normal hesaplayıcı uç nokta veya yuvarlama hesaplayıcı endpoint başvurur.</span><span class="sxs-lookup"><span data-stu-id="8a4be-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="8a4be-114">Bir hizmeti veya diğer, yönlendirme hizmeti hangisinin bağlı olarak yapılandırılmış döndürülen kendi iletileri hesaplayıcı istemci uygulaması olan o zaman için rota.</span><span class="sxs-lookup"><span data-stu-id="8a4be-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="8a4be-115">Yönlendirme hizmetin capabilitiy özel bir davranış aracılığıyla dinamik yeniden yapılandırılması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a4be-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="8a4be-116">Bu özel davranışı için bir geri çağırma edilir beş saniyede tetiklenen basit iş parçacığı süreölçer içeren bir hizmet uzantısı ekler `UpdateRules` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a4be-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="8a4be-117">Bu geri çağırma oluşturur ve yeni yönlendirme yapılandırması uygular.</span><span class="sxs-lookup"><span data-stu-id="8a4be-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="8a4be-118">Gerçek bir dağıtımda bulunan bu geri çağırma sonucunda başka türden bir olay, bir SQL olay bildirim ya da bir WS-bulma Duyurusu gibi büyük olasılıkla gerçekleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="8a4be-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8a4be-119">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8a4be-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="8a4be-120">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], DynamicReconfiguration.sln açın.</span><span class="sxs-lookup"><span data-stu-id="8a4be-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="8a4be-121">Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8a4be-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="8a4be-122">Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a4be-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="8a4be-123">Otomatik gerekli projeleri bastığınızda başlatılan isteyip **F5**, çözüme sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8a4be-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="8a4be-124">Seçin **başlangıç projesi** düğümü altında **ortak özellikleri** sol bölmede.</span><span class="sxs-lookup"><span data-stu-id="8a4be-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="8a4be-125">Seçin **birden fazla başlangıç projesi** radyo düğmesinin ve tüm projeleri için ayarlanmış **Başlat** eylem.</span><span class="sxs-lookup"><span data-stu-id="8a4be-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="8a4be-126">Proje ile yapı **CTRL + SHIFT + B**, aşağıdaki uygulamalar başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8a4be-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="8a4be-127">Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="8a4be-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="8a4be-128">Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="8a4be-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="8a4be-129">Yönlendirme hesap makinesi hizmetinin (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="8a4be-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="8a4be-130">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="8a4be-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="8a4be-131">Hesaplayıcı istemci konsol penceresinde istemci başlatmak ve hesaplayıcı hizmet işlemlerini çağırma için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8a4be-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="8a4be-132">Yönlendirme hizmeti iletileri yuvarlama hesaplayıcı ve normal hesaplayıcı dönüşümlü yönlendirme yapılandırması değişiklikleri dinamik olarak beş saniyede yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8a4be-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="8a4be-133">Yönlendirme hizmeti ileti göndermek için yapılandırılan hangi uç noktası bağlı olarak farklı çıkışları istemci konsol penceresinde vardır.</span><span class="sxs-lookup"><span data-stu-id="8a4be-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="8a4be-134">Sürekli olarak beş saniyeden fazla ENTER tuşuna basarak devam ve hizmet sonuçlarından değişikliği gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="8a4be-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="8a4be-135">Yönlendirici hizmeti yuvarlama hesaplayıcı hizmetine iletileri yönlendirmek üzere yapılandırılırsa çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8a4be-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="8a4be-136">Yönlendirme hizmeti normal hesaplayıcı hizmetine iletileri yönlendirmek üzere yapılandırılırsa çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8a4be-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="8a4be-137">Hesaplayıcı hizmeti ve yuvarlama hesaplayıcı hizmeti ilgili konsol pencerelerini çağrılan işlemlerinin bir günlük çıkışı da yazdırın.</span><span class="sxs-lookup"><span data-stu-id="8a4be-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="8a4be-138">İstemci konsol penceresinde "Çık" yazın ve ENTER tuşuna basarak çıkın.</span><span class="sxs-lookup"><span data-stu-id="8a4be-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="8a4be-139">Hizmetler konsolunda Windows Hizmetleri sonlandırmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8a4be-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="8a4be-140">Senaryo</span><span class="sxs-lookup"><span data-stu-id="8a4be-140">Scenario</span></span>  
 <span data-ttu-id="8a4be-141">Bu örnek, birden çok türleri veya hizmetleri uygulaması bir uç noktası aracılığıyla açığa çıkarılması izin vererek içerik tabanlı bir yönlendirici işlevi gören yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a4be-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="8a4be-142">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="8a4be-142">Real World Scenario</span></span>  
 <span data-ttu-id="8a4be-143">Contoso tüm genel olarak, bunlar birden çok farklı türlerdeki Hizmetleri için erişim sunar tek bir uç nokta kullanıma sunmak için kendi Hizmetleri sanallaştırmayı istiyor.</span><span class="sxs-lookup"><span data-stu-id="8a4be-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="8a4be-144">Bu durumda, gelen isteklerin gönderilmesi gerektiğini belirlemek için yönlendirme hizmetin içerik tabanlı Yönlendirme yetenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a4be-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a4be-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a4be-145">See Also</span></span>  
 [<span data-ttu-id="8a4be-146">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="8a4be-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

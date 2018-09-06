---
title: Gelişmiş Filtreler
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805448"
---
# <a name="advanced-filters"></a><span data-ttu-id="11bde-102">Gelişmiş Filtreler</span><span class="sxs-lookup"><span data-stu-id="11bde-102">Advanced Filters</span></span>
<span data-ttu-id="11bde-103">Bu örnek, bir Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="11bde-103">This sample demonstrates a Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="11bde-104">Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="11bde-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="11bde-105">Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="11bde-105">This sample adapts the standard WCF Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="11bde-106">Bu örnek, içerik tabanlı yönlendirme mantığı kullanarak ileti filtreleri ve İleti Filtresi tabloları tanımlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="11bde-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11bde-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="11bde-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="11bde-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="11bde-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11bde-109">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="11bde-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11bde-110">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="11bde-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="11bde-111">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="11bde-111">Sample Details</span></span>  
 <span data-ttu-id="11bde-112">Aşağıdaki tablo, yönlendirme hizmeti İleti Filtresi tabloya eklenen ileti filtreleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="11bde-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="11bde-113">Filtrele</span><span class="sxs-lookup"><span data-stu-id="11bde-113">Filter</span></span>|<span data-ttu-id="11bde-114">Kural</span><span class="sxs-lookup"><span data-stu-id="11bde-114">Rule</span></span>|<span data-ttu-id="11bde-115">Öncelik</span><span class="sxs-lookup"><span data-stu-id="11bde-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="11bde-116">(Üst bilgi varsa)</span><span class="sxs-lookup"><span data-stu-id="11bde-116">If (has header)</span></span>|<span data-ttu-id="11bde-117">Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="11bde-117">Rounding</span></span>|<span data-ttu-id="11bde-118">2</span><span class="sxs-lookup"><span data-stu-id="11bde-118">2</span></span>|  
|<span data-ttu-id="11bde-119">Varsa (Ep2 üzerinde gösterilen)</span><span class="sxs-lookup"><span data-stu-id="11bde-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="11bde-120">Normal</span><span class="sxs-lookup"><span data-stu-id="11bde-120">Regular</span></span>|<span data-ttu-id="11bde-121">1.</span><span class="sxs-lookup"><span data-stu-id="11bde-121">1</span></span>|  
|<span data-ttu-id="11bde-122">Varsa (Adres2 ile gösterilmiştir)</span><span class="sxs-lookup"><span data-stu-id="11bde-122">If (showed up with Address2)</span></span>|<span data-ttu-id="11bde-123">Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="11bde-123">Rounding</span></span>|<span data-ttu-id="11bde-124">1.</span><span class="sxs-lookup"><span data-stu-id="11bde-124">1</span></span>|  
|<span data-ttu-id="11bde-125">Varsa (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="11bde-125">If (RoundRobin1)</span></span>|<span data-ttu-id="11bde-126">Normal</span><span class="sxs-lookup"><span data-stu-id="11bde-126">Regular</span></span>|<span data-ttu-id="11bde-127">0</span><span class="sxs-lookup"><span data-stu-id="11bde-127">0</span></span>|  
|<span data-ttu-id="11bde-128">Varsa (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="11bde-128">If (RoundRobin2)</span></span>|<span data-ttu-id="11bde-129">Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="11bde-129">Rounding</span></span>|<span data-ttu-id="11bde-130">0</span><span class="sxs-lookup"><span data-stu-id="11bde-130">0</span></span>|  
  
 <span data-ttu-id="11bde-131">İleti filtreleri ve İleti Filtresi tabloları oluşturulur ve kod aracılığıyla ya da uygulama yapılandırma dosyasında yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="11bde-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="11bde-132">Bu örnek için kodu RoutingService\routing.cs dosyasında aracılığıyla tanımlanan veya RoutingService\App.config dosyasında uygulama yapılandırma dosyasında tanımlanan İleti Filtresi tablo ve ileti filtreleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11bde-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="11bde-133">Aşağıdaki paragraflara İleti Filtresi tablo ve ileti filtreleri için bu örnek kod aracılığıyla nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="11bde-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="11bde-134">İlk olarak, bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> için özel üstbilgi görünür.</span><span class="sxs-lookup"><span data-stu-id="11bde-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="11bde-135">Unutmayın <xref:System.ServiceModel.WSHttpBinding> sonuçları SOAP 1.2, SOAP 1.2 ad alanını kullanacak şekilde tanımlanan bir XPath ifadesi kullanarak, Zarf sürümü.</span><span class="sxs-lookup"><span data-stu-id="11bde-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="11bde-136">Varsayılan ad alanı yöneticisini <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s zaten kullanılabilen /s12 SOAP 1.2 ad alanı için bir önek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11bde-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="11bde-137">Ancak, varsayılan ad alanı yöneticisi, bu ön eki tanımlanmalıdır bu nedenle, gerçek üstbilgi değerinin tanımlamak için istemcinin kullandığı özel ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="11bde-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="11bde-138">Bu filtre ile bu üstbilgi görünür herhangi bir ileti eşleşir.</span><span class="sxs-lookup"><span data-stu-id="11bde-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="11bde-139">İkinci filtre bir <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, herhangi bir ileti alındı eşleşen `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="11bde-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="11bde-140">Uç nokta adı, bir hizmet uç noktası nesnesi oluşturulurken tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="11bde-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="11bde-141">Üçüncü filtre bir <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="11bde-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="11bde-142">Bu, bir uç noktada adres ön eki (veya ön bölümü) koşuluyla eşleşen bir adres ile hatırlarsınız herhangi bir ileti ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="11bde-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="11bde-143">Bu örnekte, adres ön eki olarak tanımlanan "http://localhost/routingservice/router/rounding/".</span><span class="sxs-lookup"><span data-stu-id="11bde-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="11bde-144">İçin gönderilen tüm gelen iletileri buna "http://localhost/routingservice/router/rounding/\*" Bu filtreden eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="11bde-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/\*" are matched by this filter.</span></span> <span data-ttu-id="11bde-145">Bu durumda, yuvarlama hesaplayıcı noktadaki görünmesini iletileri olduğu adresi olan "http://localhost/routingservice/router/rounding/calculator".</span><span class="sxs-lookup"><span data-stu-id="11bde-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="11bde-146">Son iki ileti filtreleri özel <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span><span class="sxs-lookup"><span data-stu-id="11bde-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="11bde-147">Bu örnekte, "RoundRobin" İleti Filtresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11bde-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="11bde-148">Bu ileti filtresi sağlanan RoutingService\RoundRobinMessageFilter.cs dosyasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="11bde-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="11bde-149">Aynı gruba ayarlandığında, bu filtreler yalnızca bunlardan birinin yanıt verdiği, ileti eşleştiğinden ve bunlar yapmamanızı, raporlama arasında alternatif `true` birer güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="11bde-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="11bde-150">Ardından, tüm iletiler için eklenen bir <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="11bde-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="11bde-151">Bunun yapılması, İleti Filtresi tablosu filtreleri yürütür sırasını etkilemek için öncelikleri belirtilir.</span><span class="sxs-lookup"><span data-stu-id="11bde-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="11bde-152">Filtre yürütülür öncelik o kadar yüksektir, çabuk; bir filtre yürütülür düşük önceliği, daha sonra.</span><span class="sxs-lookup"><span data-stu-id="11bde-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="11bde-153">Böylece öncelik 2 sırasında bir filtre önce bir filtre 1 öncelikli olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="11bde-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="11bde-154">Belirtilmemişse varsayılan öncelik düzeyi 0'dır.</span><span class="sxs-lookup"><span data-stu-id="11bde-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="11bde-155">İleti filtreleme tablosu tüm filtreleri verilen öncelik düzeyinde sonraki en düşük öncelik düzeyi taşımadan önce yürütür.</span><span class="sxs-lookup"><span data-stu-id="11bde-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="11bde-156">Belirli bir öncelik bir eşleşme bulunursa, ardından İleti Filtresi tablosu sonraki daha düşük öncelikli olarak bulmaya çalışırken devam etmez.</span><span class="sxs-lookup"><span data-stu-id="11bde-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11bde-157">Bu örnek İleti Filtresi öncelikleri kullanma işlemini gösterir, ancak genel olarak, daha yüksek performanslı ve daha iyi bir tasarım tasarım ve sağlayacak şekilde düzgün çalışması için öncelik gerektirmez, filtreleri yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="11bde-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="11bde-158">Eklenecek ilk filtre XPath filtresi ve önceliği 2'ye ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="11bde-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="11bde-159">Yürütülen ilk ileti filtresi budur.</span><span class="sxs-lookup"><span data-stu-id="11bde-159">This is the first message filter that executes.</span></span> <span data-ttu-id="11bde-160">Ne diğer filtrelerle sonuçlarını olacağını, ne olursa olsun üst bulursa ileti yuvarlama hesaplayıcı uç noktaya yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="11bde-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="11bde-161">Öncelik 1, iki filtre eklenir.</span><span class="sxs-lookup"><span data-stu-id="11bde-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="11bde-162">İleti önceliği 2 sırasında XPath filtresi ile eşleşmiyorsa yeniden, bu yalnızca çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="11bde-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="11bde-163">Bu iki filtre, açılırken ileti burada açıklanan belirlemek için iki farklı yollar gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11bde-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="11bde-164">İletinin iki uç noktalardan biri ulaşmadığını görmek için iki filtre etkili bir şekilde kontrol edin çünkü ikisi birden değil dönüş çünkü bunlar aynı öncelik düzeyinde çalıştırılabilir `true` aynı anda.</span><span class="sxs-lookup"><span data-stu-id="11bde-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="11bde-165">Son olarak, öncelik 0 (en düşük önceliğe) RoundRobin çalıştırmak için filtreler ileti.</span><span class="sxs-lookup"><span data-stu-id="11bde-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="11bde-166">Aynı ada sahip filtreler yapılandırıldığından, bunlardan yalnızca biri aynı anda eşleşir.</span><span class="sxs-lookup"><span data-stu-id="11bde-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="11bde-167">Özel üst bilgi sahip tüm iletiler yönlendirilir ve tüm bunları belirli sanallaştırılmış Uç noktalara yönelik RoundRobin ileti filtreler tarafından işlenen iletilerin yalnızca varsayılan yönlendirici uç noktasına özel olmadan ele alınan iletileri olduklarından, üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="11bde-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="11bde-168">Bu iletiler bir iletinin her çağrı için geçiş işlemleri yarısını normal hesaplayıcı bitiş noktasına gidin ve diğer yarısı yuvarlama hesaplayıcı bitiş noktasına gidin.</span><span class="sxs-lookup"><span data-stu-id="11bde-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="11bde-169">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="11bde-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="11bde-170">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedFilters.sln açın.</span><span class="sxs-lookup"><span data-stu-id="11bde-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="11bde-171">Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="11bde-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="11bde-172">Visual Studio'da F5'e ya da CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="11bde-172">Press F5 or CTRL+SHIFT+B in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="11bde-173">Otomatik gerekli projeleri F5 tuşuna bastığınızda başlatma isterseniz, çözüme sağ tıklayıp seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="11bde-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="11bde-174">Seçin **başlangıç projesi** düğümünde **ortak özellikler** sol bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="11bde-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="11bde-175">Seçin **birden fazla başlangıç projesi** radyo düğmesini ve tüm projeler için **Başlat** eylem.</span><span class="sxs-lookup"><span data-stu-id="11bde-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="11bde-176">CTRL + SHIFT + B ile proje oluşturuyorsanız, aşağıdaki uygulamalar başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="11bde-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="11bde-177">Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="11bde-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="11bde-178">Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="11bde-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="11bde-179">Yönlendirme hesaplayıcı hizmeti (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="11bde-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="11bde-180">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="11bde-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="11bde-181">Hesaplayıcı istemci konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11bde-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="11bde-182">İstemci, aralarından seçim yapabileceğiniz hedef uç noktaları listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="11bde-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="11bde-183">Bir hedef uç noktası, karşılık gelen bir harf yazarak seçin ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11bde-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="11bde-184">Ardından, istemci özel bir başlık eklemek isteyip istemediğimi sorar.</span><span class="sxs-lookup"><span data-stu-id="11bde-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="11bde-185">Tuşuna Evet veya Hayır, N ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="11bde-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="11bde-186">Yaptığınız seçimlere bağlı olarak, farklı bir çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="11bde-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="11bde-187">Çıkış iletileri için özel bir başlık eklediyseniz döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11bde-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="11bde-188">Özel üst bilgi içermeyen yuvarlama hesaplayıcı uç nokta seçerseniz çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11bde-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="11bde-189">Özel üst bilgi içermeyen normal hesaplayıcı uç nokta seçerseniz çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11bde-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="11bde-190">Özel üst bilgi içermeyen yönlendirici varsayılan uç nokta seçerseniz çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="11bde-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="11bde-191">Hesaplayıcı hizmetini ve yuvarlama hesaplayıcı hizmetini de yazdırır ilgili konsol pencerelerini çağrılan işlem günlüğünü dışarı.</span><span class="sxs-lookup"><span data-stu-id="11bde-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="11bde-192">İstemci konsol penceresine `quit` çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11bde-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="11bde-193">Hizmetleri sonlandırmak için hizmetler Konsolu pencerelerinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11bde-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="11bde-194">Kod veya App.config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="11bde-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="11bde-195">Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir.</span><span class="sxs-lookup"><span data-stu-id="11bde-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="11bde-196">Ayrıca RoutingService\App.config dosya adını bir şeye tanınmıyor şekilde değiştirin ve yöntem çağrısına açıklamasını kaldırın `ConfigureRouterViaCode()` RoutingService\routing.cs içinde.</span><span class="sxs-lookup"><span data-stu-id="11bde-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="11bde-197">Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="11bde-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="11bde-198">Senaryo</span><span class="sxs-lookup"><span data-stu-id="11bde-198">Scenario</span></span>  
 <span data-ttu-id="11bde-199">Bu örnek, birden çok türleri veya uygulama hizmetleri bir uç nokta sağlamak ve içerik tabanlı bir yönlendirici görevi gören yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="11bde-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="11bde-200">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="11bde-200">Real World Scenario</span></span>  
 <span data-ttu-id="11bde-201">Contoso tüm genel olarak, birden çok farklı türlerdeki Hizmetleri erişim sundukları tek bir uç nokta kullanıma sunmak için kendi hizmetlerini sanallaştırılması istemektedir.</span><span class="sxs-lookup"><span data-stu-id="11bde-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="11bde-202">Bu durumda, gelen istekleri nereye gönderileceğini belirlemek için yönlendirme hizmetin içerik tabanlı yönlendirme becerilerinden.</span><span class="sxs-lookup"><span data-stu-id="11bde-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11bde-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11bde-203">See Also</span></span>  
 [<span data-ttu-id="11bde-204">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="11bde-204">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

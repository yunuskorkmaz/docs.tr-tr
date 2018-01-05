---
title: "Gelişmiş Filtreler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 357b57bb39ca31b48d21cb83209a72d0b3d12a62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-filters"></a><span data-ttu-id="63918-102">Gelişmiş Filtreler</span><span class="sxs-lookup"><span data-stu-id="63918-102">Advanced Filters</span></span>
<span data-ttu-id="63918-103">Bu örnek gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="63918-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="63918-104">Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni.</span><span class="sxs-lookup"><span data-stu-id="63918-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="63918-105">Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yönlendirme hizmeti kullanarak iletişim kurmak için hesap makinesi örnek.</span><span class="sxs-lookup"><span data-stu-id="63918-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="63918-106">Bu örnek ileti filtreleri ve İleti Filtresi tabloları kullanılarak içerik tabanlı yönlendirme mantığını tanımlamak üzere nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="63918-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63918-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="63918-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="63918-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="63918-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="63918-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="63918-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63918-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="63918-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="63918-111">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="63918-111">Sample Details</span></span>  
 <span data-ttu-id="63918-112">Aşağıdaki tabloda, yönlendirme hizmeti İleti Filtresi tabloya eklenen ileti filtreleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="63918-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="63918-113">Filtrele</span><span class="sxs-lookup"><span data-stu-id="63918-113">Filter</span></span>|<span data-ttu-id="63918-114">Kural</span><span class="sxs-lookup"><span data-stu-id="63918-114">Rule</span></span>|<span data-ttu-id="63918-115">Öncelik</span><span class="sxs-lookup"><span data-stu-id="63918-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="63918-116">(Başlık varsa)</span><span class="sxs-lookup"><span data-stu-id="63918-116">If (has header)</span></span>|<span data-ttu-id="63918-117">Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="63918-117">Rounding</span></span>|<span data-ttu-id="63918-118">2</span><span class="sxs-lookup"><span data-stu-id="63918-118">2</span></span>|  
|<span data-ttu-id="63918-119">Varsa (Ep2 üzerinde gösterilen)</span><span class="sxs-lookup"><span data-stu-id="63918-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="63918-120">Normal</span><span class="sxs-lookup"><span data-stu-id="63918-120">Regular</span></span>|<span data-ttu-id="63918-121">1.</span><span class="sxs-lookup"><span data-stu-id="63918-121">1</span></span>|  
|<span data-ttu-id="63918-122">Varsa (Adres2 ile gösterilmiştir)</span><span class="sxs-lookup"><span data-stu-id="63918-122">If (showed up with Address2)</span></span>|<span data-ttu-id="63918-123">Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="63918-123">Rounding</span></span>|<span data-ttu-id="63918-124">1.</span><span class="sxs-lookup"><span data-stu-id="63918-124">1</span></span>|  
|<span data-ttu-id="63918-125">Varsa (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="63918-125">If (RoundRobin1)</span></span>|<span data-ttu-id="63918-126">Normal</span><span class="sxs-lookup"><span data-stu-id="63918-126">Regular</span></span>|<span data-ttu-id="63918-127">0</span><span class="sxs-lookup"><span data-stu-id="63918-127">0</span></span>|  
|<span data-ttu-id="63918-128">Varsa (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="63918-128">If (RoundRobin2)</span></span>|<span data-ttu-id="63918-129">Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="63918-129">Rounding</span></span>|<span data-ttu-id="63918-130">0</span><span class="sxs-lookup"><span data-stu-id="63918-130">0</span></span>|  
  
 <span data-ttu-id="63918-131">İleti filtreleri ve İleti Filtresi tabloları oluşturulabilir ve kod aracılığıyla veya uygulama yapılandırma dosyasında yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="63918-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="63918-132">Bu örnek için ileti filtreleri ve kodlarda RoutingService\routing.cs dosyasında tanımlanan veya RoutingService\App.config dosya uygulama yapılandırma dosyasında tanımlanan İleti Filtresi tabloları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63918-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="63918-133">Aşağıdaki paragraflara ileti filtreleri ve İleti Filtresi tabloları kod aracılığıyla bu örnek için nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="63918-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="63918-134">İlk olarak, bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> için özel üstbilgi arar.</span><span class="sxs-lookup"><span data-stu-id="63918-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="63918-135">Unutmayın <xref:System.ServiceModel.WSHttpBinding> sonuçları SOAP 1.2 ad alanını kullanmak için tanımlanmış bir XPath ifadesi SOAP 1.2 kullanarak, Zarf sürümü.</span><span class="sxs-lookup"><span data-stu-id="63918-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="63918-136">Varsayılan ad alanı yöneticisini <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s zaten kullanılabilir /s12 SOAP 1.2 ad alanı için bir önek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63918-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="63918-137">Ancak, varsayılan ad alanı yöneticisi bu önek tanımlanmalıdır böylece gerçek üstbilgi değerini tanımlamak için istemcinin kullandığı özel ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="63918-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="63918-138">Bu başlığıyla görüntülenir herhangi bir iletisi bu filtre ile eşleşen.</span><span class="sxs-lookup"><span data-stu-id="63918-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="63918-139">İkinci filtresi bir <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, alındı herhangi bir iletisi eşleşen `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="63918-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="63918-140">Bir hizmet uç noktası nesnesi oluşturulduğunda, uç nokta adı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="63918-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="63918-141">Üçüncü filtresi bir <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="63918-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="63918-142">Bu uç noktada sağlanan adres ön eki (veya ön bölümü) eşleşen bir adres ile gösterilen herhangi bir iletisi eşleşir.</span><span class="sxs-lookup"><span data-stu-id="63918-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="63918-143">Bu örnekte adres ön eki "http://localhost/routingservice/router/rounding/" tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="63918-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="63918-144">Başka bir deyişle, bu filtre tarafından gönderilen gelen iletiler için "http://localhost/routingservice/router/rounding/ *" eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="63918-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/*" are matched by this filter.</span></span> <span data-ttu-id="63918-145">Bu durumda, adresi "http://localhost/routingservice/router/rounding/calculator" olan yuvarlama hesaplayıcı noktadaki görünmesini iletileri olur.</span><span class="sxs-lookup"><span data-stu-id="63918-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="63918-146">Son iki ileti filtreleri özel <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span><span class="sxs-lookup"><span data-stu-id="63918-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="63918-147">Bu örnekte, "RoundRobin" İleti Filtresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63918-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="63918-148">Bu ileti filtresi sağlanan RoutingService\RoundRobinMessageFilter.cs dosyasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63918-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="63918-149">Aynı gruba ayarlandığında bu filtreler yalnızca bunlardan birinin yanıt şekilde ileti eşleşen ve bunlar yapmamanızı, raporlama arasında alternatif `true` birer birer.</span><span class="sxs-lookup"><span data-stu-id="63918-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="63918-150">Ardından, tüm bu iletilerin eklenen bir <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="63918-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="63918-151">Bunu yaparken öncelikleri İleti Filtresi tablosu filtreleri yürütür sırasını etkilemek için belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="63918-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="63918-152">Filtre yürütülen öncelik o kadar yüksektir, çabuk; bir filtre yürütülen düşük önceliği, daha sonra.</span><span class="sxs-lookup"><span data-stu-id="63918-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="63918-153">Bu nedenle öncelikle 2 bir filtre önce bir filtre 1 öncelikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="63918-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="63918-154">Belirtilmezse varsayılan öncelik düzeyi 0'dır.</span><span class="sxs-lookup"><span data-stu-id="63918-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="63918-155">Bir ileti Filtresi tablosu verilen öncelik düzeyindeki tüm filtreleri sonraki en düşük öncelik düzeyi taşımadan önce yürütür.</span><span class="sxs-lookup"><span data-stu-id="63918-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="63918-156">Bir eşleşme belirli bir öncelikte bulunursa, ardından İleti Filtresi tablosu eşleşmeleri sonraki daha düşük öncelikli olarak bulunmaya çalışılırken devam etmez.</span><span class="sxs-lookup"><span data-stu-id="63918-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63918-157">Bu örnek İleti Filtresi öncelikleri kullanmayı gösterir, ancak genel olarak, daha fazla kullanıcı olduğunu ve tasarımı tasarım daha iyi ve düzgün çalışması için öncelik gerektirmeyen gibi filtrelerinizi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="63918-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="63918-158">Eklenecek ilk filtreyi XPath filtresi ve önceliği 2'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="63918-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="63918-159">Yürütür ilk ileti filtresi budur.</span><span class="sxs-lookup"><span data-stu-id="63918-159">This is the first message filter that executes.</span></span> <span data-ttu-id="63918-160">Ne diğer filtreler sonuçlarını olacağını, ne olursa olsun özel üstbilgi bulursa ileti yuvarlama hesaplayıcı uç noktasına yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="63918-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="63918-161">Öncelik 1 olduğunda, iki filtre eklenir.</span><span class="sxs-lookup"><span data-stu-id="63918-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="63918-162">XPath filtresi öncelikli 2 ileti eşleşmiyorsa yeniden, bunlar yalnızca çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="63918-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="63918-163">Bu iki filtre gösterdi olduğunda ileti burada açıklanan belirlemek için iki farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63918-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="63918-164">İki filtre etkili bir şekilde iletinin iki uç noktalardan biri ulaşmadığını denetleyin, bunların her ikisi de return çünkü bunlar aynı öncelik düzeyinde çalıştırılamıyor `true` aynı anda.</span><span class="sxs-lookup"><span data-stu-id="63918-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="63918-165">Son olarak, öncelikli RoundRobin çalıştırmak 0 (en düşük öncelik) filtreleri iletisi.</span><span class="sxs-lookup"><span data-stu-id="63918-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="63918-166">Aynı ada sahip filtreler yapılandırıldığından, yalnızca bunlardan birinin aynı anda eşleşir.</span><span class="sxs-lookup"><span data-stu-id="63918-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="63918-167">Özel Başlık sahip tüm iletiler yönlendirilir ve tüm bunları belirli sanallaştırılmış Uç noktalara ele RoundRobin ileti filtreler tarafından işlenen iletiler yalnızca varsayılan yönlendirici uç özel olmadan ele alınan iletileri olduklarından, Üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="63918-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="63918-168">Her çağrı için bir ileti üzerinde bu iletileri geçiş için işlemleri yarısı normal hesaplayıcı bitiş noktasına gidin ve diğer yarısı yuvarlama hesaplayıcı bitiş noktasına gidin.</span><span class="sxs-lookup"><span data-stu-id="63918-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="63918-169">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="63918-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="63918-170">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedFilters.sln açın.</span><span class="sxs-lookup"><span data-stu-id="63918-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="63918-171">Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="63918-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="63918-172">F5 veya CTRL + SHIFT + B tuşuna basın [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63918-172">Press F5 or CTRL+SHIFT+B in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="63918-173">Otomatik gerekli projeleri F5 tuşuna bastığınızda başlatılan istediğiniz varsa, çözüme sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="63918-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="63918-174">Seçin **başlangıç projesi** düğümü altında **ortak özellikleri** sol bölmede.</span><span class="sxs-lookup"><span data-stu-id="63918-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="63918-175">Seçin **birden fazla başlangıç projesi** radyo düğmesinin ve tüm projeleri için ayarlanmış **Başlat** eylem.</span><span class="sxs-lookup"><span data-stu-id="63918-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="63918-176">CTRL + SHIFT + B projeyle oluşturuyorsanız, aşağıdaki uygulamalar başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="63918-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="63918-177">Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="63918-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="63918-178">Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="63918-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="63918-179">Yönlendirme hesap makinesi hizmetinin (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="63918-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="63918-180">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="63918-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="63918-181">Hesaplayıcı istemci konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="63918-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="63918-182">İstemci aralarından seçim yapabileceğiniz hedef uç noktaları listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="63918-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="63918-183">Karşılık gelen harfini yazarak bir hedef uç noktası seçin ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="63918-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="63918-184">Ardından, istemci bir özel üst bilgi eklemek isteyip istemediğinizi sorar.</span><span class="sxs-lookup"><span data-stu-id="63918-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="63918-185">E'ye Evet veya Hayır, N ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="63918-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="63918-186">Yaptığınız seçimleri bağlı olarak, farklı bir çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63918-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="63918-187">Çıktı iletileri bir özel üst bilgi eklediyseniz döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63918-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="63918-188">Özel üst bilgi içermeyen yuvarlama hesaplayıcı endpoint seçerseniz çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63918-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="63918-189">Özel üstbilgi olmadan normal hesaplayıcı endpoint seçerseniz çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63918-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="63918-190">Özel üst bilgi içermeyen varsayılan yönlendirici endpoint seçerseniz çıkış döndürülen verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63918-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="63918-191">Hesaplayıcı hizmeti ve yuvarlama hesaplayıcı Hizmeti ayrıca yazdırır ilgili konsol pencerelerini çağrılan işlemlerinin bir günlük çıkışı.</span><span class="sxs-lookup"><span data-stu-id="63918-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="63918-192">İstemci konsol penceresine `quit` ve çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="63918-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="63918-193">Hizmetler konsolunda Windows Hizmetleri sonlandırmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="63918-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="63918-194">Kod ya da App.config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="63918-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="63918-195">Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir.</span><span class="sxs-lookup"><span data-stu-id="63918-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="63918-196">Ayrıca RoutingService\App.config dosyasının adı başka bir şey için tanınmıyor şekilde değiştirin ve yöntem çağrısının açıklamasını kaldırın `ConfigureRouterViaCode()` RoutingService\routing.cs içinde.</span><span class="sxs-lookup"><span data-stu-id="63918-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="63918-197">Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="63918-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="63918-198">Senaryo</span><span class="sxs-lookup"><span data-stu-id="63918-198">Scenario</span></span>  
 <span data-ttu-id="63918-199">Bu örnek, birden çok türleri veya hizmetleri uygulaması bir uç noktası aracılığıyla açığa çıkarılması izin vererek içerik tabanlı bir yönlendirici işlevi gören yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="63918-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="63918-200">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="63918-200">Real World Scenario</span></span>  
 <span data-ttu-id="63918-201">Contoso tüm genel olarak, bunlar birden çok farklı türlerdeki Hizmetleri için erişim sunar tek bir uç nokta kullanıma sunmak için kendi Hizmetleri sanallaştırmayı istiyor.</span><span class="sxs-lookup"><span data-stu-id="63918-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="63918-202">Bu durumda, gelen isteklerin gönderilmesi gerektiğini belirlemek için yönlendirme hizmetin içerik tabanlı Yönlendirme yetenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="63918-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63918-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63918-203">See Also</span></span>  
 [<span data-ttu-id="63918-204">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="63918-204">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

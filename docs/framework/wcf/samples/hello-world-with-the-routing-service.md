---
title: "Yönlendirme Hizmeti ile Merhaba Dünya"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1d068894c9ad28d786c7b433c56b6d0fd79acc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="1d15f-102">Yönlendirme Hizmeti ile Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="1d15f-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="1d15f-103">Bu örnek gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="1d15f-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Routing Service.</span></span> <span data-ttu-id="1d15f-104">Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1d15f-104">The Routing Service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="1d15f-105">Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hesaplayıcı yönlendirme hizmeti kullanarak iletişim kurmak için örnek.</span><span class="sxs-lookup"><span data-stu-id="1d15f-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="1d15f-106">Bu örnekte, hesaplayıcı istemci yönlendirici tarafından kullanıma sunulan bir uç nokta ileti göndermek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1d15f-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="1d15f-107">Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmek ve hesaplayıcı hizmeti karşılık gelen bir uç nokta iletmek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1d15f-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="1d15f-108">Bu nedenle istemci tarafından gönderilen iletileri yönlendirici tarafından alınan ve gerçek hesaplayıcı hizmete yeniden yönlendirildi.</span><span class="sxs-lookup"><span data-stu-id="1d15f-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="1d15f-109">Hesaplayıcı hizmetinden gelen iletileri hangi sırayla bunları hesaplayıcı istemciye aktarır geri yönlendiriciye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1d15f-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="1d15f-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1d15f-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="1d15f-111">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], HelloRoutingService.sln açın.</span><span class="sxs-lookup"><span data-stu-id="1d15f-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open HelloRoutingService.sln.</span></span>  
  
2.  <span data-ttu-id="1d15f-112">F5 veya CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1d15f-112">Press F5 or CTRL+SHIFT+B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1d15f-113">F5 tuşuna basarsanız hesaplayıcı istemci otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="1d15f-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="1d15f-114">CTRL + SHIFT + B (yapı) tuşuna basarsanız, uygulamaları kendiniz başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d15f-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>  
    >   
    >  1.  <span data-ttu-id="1d15f-115">Hesaplayıcı istemci (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="1d15f-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>  
    > 2.  <span data-ttu-id="1d15f-116">Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="1d15f-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>  
    > 3.  <span data-ttu-id="1d15f-117">Yönlendirme Hizmeti (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="1d15f-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>  
  
3.  <span data-ttu-id="1d15f-118">İstemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1d15f-118">Press ENTER to start the client.</span></span>  
  
     <span data-ttu-id="1d15f-119">Şu çıktı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1d15f-119">You should see the following output:</span></span>  
  
     <span data-ttu-id="1d15f-120">Add(100,15.99) 115.99 =</span><span class="sxs-lookup"><span data-stu-id="1d15f-120">Add(100,15.99) = 115.99</span></span>  
  
     <span data-ttu-id="1d15f-121">Subtract(145,76.54) 68.46 =</span><span class="sxs-lookup"><span data-stu-id="1d15f-121">Subtract(145,76.54) = 68.46</span></span>  
  
     <span data-ttu-id="1d15f-122">Multiply(9,81.25) 731.25 =</span><span class="sxs-lookup"><span data-stu-id="1d15f-122">Multiply(9,81.25) = 731.25</span></span>  
  
     <span data-ttu-id="1d15f-123">Divide(22,7) 3.14285714285714 =</span><span class="sxs-lookup"><span data-stu-id="1d15f-123">Divide(22,7) = 3.14285714285714</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="1d15f-124">Kod ya da App.Config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="1d15f-124">Configurable via Code or App.Config</span></span>  
 <span data-ttu-id="1d15f-125">Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir.</span><span class="sxs-lookup"><span data-stu-id="1d15f-125">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="1d15f-126">Ayrıca, App.config dosyasının adı başka bir şey için tanınmıyor şekilde değiştirin ve ConfigureRouterViaCode() yöntemi çağrısına açıklamadan çıkarın.</span><span class="sxs-lookup"><span data-stu-id="1d15f-126">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="1d15f-127">Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1d15f-127">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="1d15f-128">Senaryo</span><span class="sxs-lookup"><span data-stu-id="1d15f-128">Scenario</span></span>  
 <span data-ttu-id="1d15f-129">Bu örnek, temel ileti Pompalama işlev gören yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d15f-129">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="1d15f-130">Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktaları kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="1d15f-130">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="1d15f-131">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="1d15f-131">Real World Scenario</span></span>  
 <span data-ttu-id="1d15f-132">Contoso adlandırma, adresleme, yapılandırma ve hizmetlerinin güvenliğini sahip esnekliğini artırmak ister.</span><span class="sxs-lookup"><span data-stu-id="1d15f-132">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="1d15f-133">Bunu yapmak için temel ileti Pompalama genel kullanıma yönelik bir uç nokta davranacak şekilde hizmetlerini önüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1d15f-133">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="1d15f-134">Bu ek güvenlik gerçek hizmetlerini önüne yerleştirin ve uygulamak çözümleri veya hizmet sürümü oluşturma daha sonraki bir tarihte ölçeklendirilmiş kolaylaştırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d15f-134">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d15f-135">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="1d15f-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1d15f-136">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1d15f-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1d15f-137">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1d15f-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1d15f-138">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1d15f-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="1d15f-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d15f-139">See Also</span></span>  
 [<span data-ttu-id="1d15f-140">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="1d15f-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

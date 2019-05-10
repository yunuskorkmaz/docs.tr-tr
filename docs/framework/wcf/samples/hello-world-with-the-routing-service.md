---
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 802135f61e1744acbfe5ae5fe4a6e92ec49d46b2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650037"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="dc39d-102">Yönlendirme Hizmeti ile Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="dc39d-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="dc39d-103">Bu örnek, Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc39d-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="dc39d-104">Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="dc39d-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="dc39d-105">Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc39d-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="dc39d-106">Bu örnekte, hesaplayıcı istemci yönlendirici tarafından sunulan bir uç noktaya iletileri göndermek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="dc39d-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="dc39d-107">Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmesini ve hesaplayıcı hizmetine karşılık gelen bir uç nokta iletmek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="dc39d-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="dc39d-108">Bu nedenle istemci tarafından gönderilen iletileri yönlendirici tarafından alınan ve gerçek hesaplayıcı hizmete yeniden yönlendirilen.</span><span class="sxs-lookup"><span data-stu-id="dc39d-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="dc39d-109">Hesaplayıcı hizmetinden gelen iletileri hangi sırayla bunları hesaplayıcı istemciye aktarır yeniden yönlendiriciye gönderilir.</span><span class="sxs-lookup"><span data-stu-id="dc39d-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="dc39d-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dc39d-110">To use this sample</span></span>

1. <span data-ttu-id="dc39d-111">Visual Studio 2012 kullanarak HelloRoutingService.sln açın.</span><span class="sxs-lookup"><span data-stu-id="dc39d-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="dc39d-112">F5 veya CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="dc39d-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="dc39d-113">F5 tuşuna basarsanız, hesaplayıcı istemci otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="dc39d-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="dc39d-114">CTRL + SHIFT + B (derleme) tuşuna basarsanız, kendiniz uygulamaları başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc39d-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="dc39d-115">Hesaplayıcı istemci (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="dc39d-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="dc39d-116">Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="dc39d-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="dc39d-117">Yönlendirme Hizmeti (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="dc39d-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="dc39d-118">İstemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc39d-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="dc39d-119">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="dc39d-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="dc39d-120">Kod veya App.Config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="dc39d-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="dc39d-121">Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir.</span><span class="sxs-lookup"><span data-stu-id="dc39d-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="dc39d-122">Ayrıca, App.config dosyasının adı bir şeye tanınmıyor şekilde değiştirin ve ConfigureRouterViaCode() yöntem çağrısına açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="dc39d-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="dc39d-123">Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="dc39d-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="dc39d-124">Senaryo</span><span class="sxs-lookup"><span data-stu-id="dc39d-124">Scenario</span></span>
 <span data-ttu-id="dc39d-125">Bu örnek, bir temel ileti pompası davranan yönlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc39d-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="dc39d-126">Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktaları kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="dc39d-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="dc39d-127">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="dc39d-127">Real World Scenario</span></span>
 <span data-ttu-id="dc39d-128">Contoso adlandırma, adres, yapılandırma ve güvenlik hizmetleri olan esnekliği artırmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="dc39d-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="dc39d-129">Bunu yapmak için bunlar bir temel ileti pompası genel kullanıma yönelik bir uç nokta yapması hizmetlerini önüne koyun.</span><span class="sxs-lookup"><span data-stu-id="dc39d-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="dc39d-130">Bu ek güvenlik gerçek hizmetlerini önüne yerleştirin ve uygulamak daha sonraki bir tarihte daraltılmasına çözümleri veya hizmet sürümü oluşturma kolaylaştırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc39d-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="dc39d-131">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="dc39d-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dc39d-132">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dc39d-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dc39d-133">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="dc39d-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dc39d-134">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc39d-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="dc39d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc39d-135">See also</span></span>

- [<span data-ttu-id="dc39d-136">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="dc39d-136">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

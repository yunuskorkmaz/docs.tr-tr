---
title: Yönlendirme Hizmeti ile Merhaba Dünya
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183640"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="efe37-102">Yönlendirme Hizmeti ile Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="efe37-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="efe37-103">Bu örnek, Windows Communication Foundation (WCF) Yönlendirme Hizmetini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="efe37-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="efe37-104">Yönlendirme Hizmeti, uygulamanıza içerik tabanlı bir yönlendirici eklemeyi kolaylaştıran bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="efe37-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="efe37-105">Bu örnek, Yönlendirme Hizmetini kullanarak iletişim kurmak için standart WCF Hesap Makinesi Örneğini uyarlar.</span><span class="sxs-lookup"><span data-stu-id="efe37-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="efe37-106">Bu örnekte, Hesap Makinesi istemcisi yönlendirici tarafından açığa çıkarılan bir bitiş noktasına ileti gönderecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="efe37-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="efe37-107">Yönlendirme Hizmeti, gönderilen tüm iletileri kabul etmek ve hesap makinesi hizmetine karşılık gelen bir bitiş noktasına iletmek için yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="efe37-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="efe37-108">Böylece istemciden gönderilen iletiler yönlendirici tarafından alınır ve gerçek Hesap Makinesi hizmetine yeniden yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="efe37-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="efe37-109">Hesap Makinesi hizmetinden gelen iletiler yönlendiriciye geri gönderilir ve bu da onları Hesap Makinesi istemcisine geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="efe37-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="efe37-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="efe37-110">To use this sample</span></span>

1. <span data-ttu-id="efe37-111">Visual Studio 2012'yi kullanarak HelloRoutingService.sln'yi açın.</span><span class="sxs-lookup"><span data-stu-id="efe37-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="efe37-112">F5 veya CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efe37-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="efe37-113">F5 tuşuna baslarsanız, Hesap Makinesi İstemci otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="efe37-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="efe37-114">CTRL+SHIFT+B (yapı) tuşuna basarsanız, uygulamaları kendiniz takip etmeye başlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="efe37-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="efe37-115">Hesap makinesi istemcisi (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="efe37-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="efe37-116">Hesap makinesi hizmeti (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="efe37-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="efe37-117">Yönlendirme hizmeti (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="efe37-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="efe37-118">İstemciyi başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efe37-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="efe37-119">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="efe37-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="efe37-120">Kod veya App.Config ile yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="efe37-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="efe37-121">Örnek gemiler, yönlendiricinin davranışını tanımlamak için bir App.config dosyası kullanacak şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="efe37-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="efe37-122">App.config dosyasının adını, tanınmaması ve YapılandırmaRouterViaCode() için yapılan yöntem çağrısının yorumsuz olması için başka bir şeyle de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efe37-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="efe37-123">Her iki yöntem de yönlendiriciden aynı davranışla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="efe37-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="efe37-124">Senaryo</span><span class="sxs-lookup"><span data-stu-id="efe37-124">Scenario</span></span>
 <span data-ttu-id="efe37-125">Bu örnek, yönlendiricinin temel bir mesaj pompası olarak hareket ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="efe37-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="efe37-126">Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış hedef uç noktaları kümesine aktarmak üzere yapılandırılan saydam bir proxy düğümü görevi görür.</span><span class="sxs-lookup"><span data-stu-id="efe37-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="efe37-127">Gerçek Dünya Senaryosu</span><span class="sxs-lookup"><span data-stu-id="efe37-127">Real World Scenario</span></span>
 <span data-ttu-id="efe37-128">Contoso, hizmetlerinin adlandırılması, ele alınması, yapılandırması ve güvenliği konusunda sahip olduğu esnekliği artırmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="efe37-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="efe37-129">Bunu yapmak için, bir kamu bakan bitiş noktası olarak hareket etmek için kendi hizmetlerinin önünde temel bir mesaj pompası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="efe37-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="efe37-130">Bu, gerçek hizmetlerinin önüne ek güvenlik yerleştirmelerine ve daha sonraki bir tarihte ölçeklenmiş çözümleri veya hizmet sürümünü uygulamayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="efe37-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efe37-131">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="efe37-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="efe37-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="efe37-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="efe37-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="efe37-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="efe37-134">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="efe37-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="efe37-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efe37-135">See also</span></span>

- <span data-ttu-id="efe37-136">[AppFabric Hosting ve Kalıcılık Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="efe37-136">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

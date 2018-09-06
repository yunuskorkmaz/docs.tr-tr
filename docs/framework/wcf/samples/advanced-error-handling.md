---
title: Gelişmiş Hata İşleme
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873922"
---
# <a name="advanced-error-handling"></a><span data-ttu-id="7daf4-102">Gelişmiş Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="7daf4-102">Advanced Error Handling</span></span>
<span data-ttu-id="7daf4-103">Bu örnek, Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="7daf4-104">Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="7daf4-105">Bu örnek nasıl yönlendirme hizmeti akıllı bir şekilde işlemleri ve çok noktaya yayın gibi daha karmaşık diğer ileti kavramları kullanarak hataları, kurtarır gösterir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7daf4-106">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="7daf4-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7daf4-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7daf4-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7daf4-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7daf4-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7daf4-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7daf4-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="7daf4-110">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="7daf4-110">Sample Details</span></span>  
 <span data-ttu-id="7daf4-111">Bu örnekte, yönlendirme hizmeti, bir ileti bir MSMQ sırası ve çok noktaya yayın bu ileti kuyrukları iki listelerine okumak için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7daf4-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="7daf4-112">Hizmet kuyruklar için kullanılan bir listesi ve başka bir günlük kuyruklar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7daf4-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="7daf4-113">Varsayılan olarak, bağlama MSMQ yönlendirme hizmeti için yapılandırılmış olduğundan, işlem kullanımını destekler, yönlendirme hizmeti ileti raporlama için gelen kuyruğu (önce işlem ve her bir listedeki en az bir kuyruk tarafından alınan olmasını sağlar `InQ`), iletiyi başarıyla yönlendirildi.</span><span class="sxs-lookup"><span data-stu-id="7daf4-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="7daf4-114">Bu nedenle, günlük kuyruklar hem de Hizmet Kuyrukları veya kullanılamaz olduğu durumlarda, yönlendirme hizmeti, ileti yönlendirilemeyen ve gelen sıra bazı işlemler yapması bildirir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="7daf4-115">Bu eylem, ileti sistemi edilemeyen iletiler sırasına taşıyarak oluşur.</span><span class="sxs-lookup"><span data-stu-id="7daf4-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7daf4-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7daf4-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="7daf4-117">Bu örneği çalıştırmadan önce MSMQ yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7daf4-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="7daf4-118">MSMQ yüklü değilse, örnek çalıştırılırken bir özel durum iletisi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7daf4-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="7daf4-119">MSMQ yüklemek için yönergeler bulunabilir [yükleme Message Queuing (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="7daf4-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="7daf4-120">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedErrorHandling.sln açın.</span><span class="sxs-lookup"><span data-stu-id="7daf4-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="7daf4-121">Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="7daf4-121">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="7daf4-122">CTRL + SHIFT + B ile bir uygulama oluşturuyorsanız, uygulamayı başlamalıdır. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="7daf4-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="7daf4-123">Konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7daf4-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="7daf4-124">İstemci her çalışması için kuyruklar farklı İstatistikler döndürür.</span><span class="sxs-lookup"><span data-stu-id="7daf4-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="7daf4-125">1 (hata sayısı) çalışması için döndürülen çıkış verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="7daf4-126">3 (birincil hizmeti ve kuyruk hataları günlüğe kaydetme) çalışması için döndürülen çıkış verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="7daf4-127">4 (birincil hizmet kuyruğu ve birincil ve yedek günlük sıra hataları) çalışması için döndürülen çıkış verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="7daf4-128">2 (birincil hizmet sırası hatası) çalışması için döndürülen çıkış verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="7daf4-129">Kod veya App.config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="7daf4-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="7daf4-130">Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="7daf4-131">Ayrıca RoutingService\App.config dosya adını bir şeye tanınmıyor şekilde değiştirin ve değerini değiştirme `configDriven` için RoutingService\Program.cs alanındaki `false` kod içinde tanımlanan yapılandırmasını kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="7daf4-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="7daf4-132">Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="7daf4-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="7daf4-133">Senaryo</span><span class="sxs-lookup"><span data-stu-id="7daf4-133">Scenario</span></span>  
 <span data-ttu-id="7daf4-134">Yönlendirme hizmeti işlemleri gibi gelişmiş Mesajlaşma işlevlerini işlemek ve bağlamını alır ve bu özelliklerin doğru hata senaryolarını işleme işleminin bir parçası olarak kullanabilir, bu örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="7daf4-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="7daf4-135">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="7daf4-135">Real World Scenario</span></span>  
 <span data-ttu-id="7daf4-136">Contoso işlem kullanmak isterse, gerekli tüm hizmetleri bile sırasında hata koşulları bilgilerini almasını sağlamak için yönlendirme hizmeti aracılığıyla alır.</span><span class="sxs-lookup"><span data-stu-id="7daf4-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="7daf4-137">Ayrıca, bunların doğru ve otomatik olarak işlenecek hataları ve hata durumunda bile hata işleme mantığı ne zaman kullanılır, bir iletinin teslim edilemeyen olduğunu bildirilmesini ister.</span><span class="sxs-lookup"><span data-stu-id="7daf4-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="7daf4-138">Bu amaç için bunlar belirli Uç noktalara beklendiği gibi yük devretmek için yönlendirme hizmeti yapılandırın ve yönlendirme hizmeti oluşturma, tamamlama ve geri alma/iptal etme işlemleri ve alma bağlamları içeren hata durumları işler. gerekli.</span><span class="sxs-lookup"><span data-stu-id="7daf4-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7daf4-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7daf4-139">See Also</span></span>  
 [<span data-ttu-id="7daf4-140">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="7daf4-140">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

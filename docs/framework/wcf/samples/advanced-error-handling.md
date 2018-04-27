---
title: Gelişmiş Hata İşleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35911a80e7686a1023f42115f785fb64d949aeff
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="advanced-error-handling"></a><span data-ttu-id="032c6-102">Gelişmiş Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="032c6-102">Advanced Error Handling</span></span>
<span data-ttu-id="032c6-103">Bu örnek gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="032c6-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="032c6-104">Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni.</span><span class="sxs-lookup"><span data-stu-id="032c6-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="032c6-105">Bu örnek nasıl yönlendirme hizmeti akıllıca hataları, işlemleri ve çok noktaya yayın gibi daha karmaşık diğer ileti kavramları kullanarak kurtarır gösterir.</span><span class="sxs-lookup"><span data-stu-id="032c6-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="032c6-106">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="032c6-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="032c6-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="032c6-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="032c6-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="032c6-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="032c6-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="032c6-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="032c6-110">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="032c6-110">Sample Details</span></span>  
 <span data-ttu-id="032c6-111">Bu örnekte, yönlendirme hizmeti ileti bu iletiyi bir MSMQ sırası ve çok noktaya yayın için sıraların iki liste okumak için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="032c6-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="032c6-112">Bir liste için Hizmet Kuyrukları kullanılır ve başka bir günlük sıraları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="032c6-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="032c6-113">Varsayılan olarak, bağlaması MSMQ yönlendirme hizmeti için yapılandırılmış olduğundan, kullanım işlemleri kullanımını destekler, yönlendirme hizmeti ileti Gelen sırası (raporlamadan önce işlem ve her listedeki en az bir kuyruk tarafından alınan emin yapar `InQ`), iletiyi başarıyla yönlendirildi.</span><span class="sxs-lookup"><span data-stu-id="032c6-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="032c6-114">Bu nedenle, her iki hizmet kuyrukları veya hem günlük sıra kullanılamaz olduğu durumda, ileti yönlendirilemeyen ve gelen sırası bazı işlemler yapması yönlendirme hizmeti raporlar.</span><span class="sxs-lookup"><span data-stu-id="032c6-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="032c6-115">Bu eylem sistem sahipsiz sıraya ileti taşınırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="032c6-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="032c6-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="032c6-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="032c6-117">Bu örneği çalıştırmadan önce MSMQ yükleyin.</span><span class="sxs-lookup"><span data-stu-id="032c6-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="032c6-118">MSMQ yüklü değilse, bir özel durum iletisi örnek çalıştırırken döndürülür.</span><span class="sxs-lookup"><span data-stu-id="032c6-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="032c6-119">MSMQ yüklemek için yönergeleri bulunabilir [yükleme Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="032c6-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="032c6-120">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedErrorHandling.sln açın.</span><span class="sxs-lookup"><span data-stu-id="032c6-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="032c6-121">Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="032c6-121">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="032c6-122">CTRL + SHIFT + B uygulamasıyla yapılandırdıysanız, uygulamayı başlatmanız gerekir. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="032c6-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="032c6-123">Konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="032c6-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="032c6-124">İstemci, her örneği için kuyrukları farklı istatistikleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="032c6-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="032c6-125">Durum 1 (hata sayısı) için döndürülen çıktının verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="032c6-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="032c6-126">Durum 3 (birincil hizmet ve sıra hataları günlüğe kaydetme) için döndürülen çıktının verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="032c6-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="032c6-127">Durum 4 (birincil hizmet sırası ve birincil ve yedek günlüğü sıra hatası) için döndürülen çıktının verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="032c6-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="032c6-128">Durum 2 (birincil hizmet sırası arızası) için döndürülen çıktının verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="032c6-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="032c6-129">Kod ya da App.config aracılığıyla yapılandırılabilir</span><span class="sxs-lookup"><span data-stu-id="032c6-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="032c6-130">Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir.</span><span class="sxs-lookup"><span data-stu-id="032c6-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="032c6-131">Ayrıca RoutingService\App.config dosyasının adı başka bir şey için tanınmıyor şekilde değiştirin ve değerini değiştirmek `configDriven` RoutingService\Program.cs için alanındaki `false` kod içinde tanımlanan yapılandırmasını kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="032c6-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="032c6-132">Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="032c6-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="032c6-133">Senaryo</span><span class="sxs-lookup"><span data-stu-id="032c6-133">Scenario</span></span>  
 <span data-ttu-id="032c6-134">Bu örnek, yönlendirme hizmeti işlemleri gibi gelişmiş Mesajlaşma işlevlerini işlemek ve içerik almak ve doğru hata senaryolarını işleme bir parçası olarak bu özellikleri kullanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="032c6-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="032c6-135">Gerçek dünya senaryosu</span><span class="sxs-lookup"><span data-stu-id="032c6-135">Real World Scenario</span></span>  
 <span data-ttu-id="032c6-136">Gerekli tüm hizmetleri hata koşulları sırasında bile bilgi aldığından emin olmak üzere yönlendirme hizmeti aracılığıyla Contoso işlem kullanmak isterse alır.</span><span class="sxs-lookup"><span data-stu-id="032c6-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="032c6-137">Ayrıca, bunların doğru ve otomatik olarak işlenecek hataları ve hata işleme mantığı bile ne zaman kullanıldığı bir ileti teslim edilemeyen durumda bildirilecek hataları ister.</span><span class="sxs-lookup"><span data-stu-id="032c6-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="032c6-138">Bu amaçla belirli Uç noktalara beklendiği gibi devretmek için yönlendirme hizmeti yapılandırın ve yönlendirme hizmeti oluşturulması, tamamlama ve geri alma/durduruluyor işlemleri/alma bağlamlarının içeren hata durumları işleme gerekli.</span><span class="sxs-lookup"><span data-stu-id="032c6-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032c6-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="032c6-139">See Also</span></span>  
 [<span data-ttu-id="032c6-140">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="032c6-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

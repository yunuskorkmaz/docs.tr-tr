---
title: Döngüsel İzleme
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: cd1a0c85dd42a7f064e75c7efdacb9ea46ef445d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002418"
---
# <a name="circular-tracing"></a><span data-ttu-id="33f9c-102">Döngüsel İzleme</span><span class="sxs-lookup"><span data-stu-id="33f9c-102">Circular Tracing</span></span>
<span data-ttu-id="33f9c-103">Bu örnek, bir döngüsel arabellek İzleme dinleyicisi uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="33f9c-104">Sık karşılaşılan bir senaryodur üretim Hizmetleri için uzun süreler için kullanılabilen hizmetler ve izleme günlüğü düşük bir düzeyde etkin ' dir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="33f9c-105">Bu hizmetler, çok fazla disk alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="33f9c-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="33f9c-106">Bir hizmet sorunlarını giderirken, izleme günlüğü en son verileri sorununuzu çözmek için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="33f9c-107">Bu örnek yalnızca en son izlemeleri, yapılandırılabilir bir veri miktarına kadar diskte tutulur bir döngüsel arabellek İzleme dinleyicisi uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="33f9c-108">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve özel İzleme dinleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33f9c-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="33f9c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="33f9c-110">Bu örnek, aşina olduğunuzu varsayar [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek ve okuma için sağlanan belgeleri [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="33f9c-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="33f9c-111">Döngüsel arabellek İzleme dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="33f9c-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="33f9c-112">Döngüsel arabellek İzleme dinleyicisi uygulamasının arkasında kavramı her kadar ikiye toplam istenen izleme günlük verilerini depolayabilir iki dosya sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="33f9c-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="33f9c-113">Dinleyici bir dosya oluşturur ve isteğe bağlı olarak, bu noktada ikinci bir dosyaya geçer veri boyutu, ilk yarısında, sınıra ulaşana kadar bu dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="33f9c-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="33f9c-114">Dinleyici ikinci dosya - sınırına ulaştığında yeni izlemeleri ilk dosyanın üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="33f9c-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="33f9c-115">Bu dinleyici türetildiği `XmlWriteTraceListener` ve günlükleri ile görüntülenmesine izin verir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="33f9c-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="33f9c-116">Günlükleri görüntülemek çalışırken, iki günlük dosyaları kolayca günlük dosyalarının her ikisi de aynı anda hizmet izleme Görüntüleyicisi Aracı'nda açarak tasarlanabilen.</span><span class="sxs-lookup"><span data-stu-id="33f9c-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="33f9c-117">Hizmet izleme Görüntüleyicisi aracı otomatik olarak doğru sırayla görünecekleri izlemeleri sıralama üstlenir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="33f9c-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33f9c-118">Configuration</span></span>  
 <span data-ttu-id="33f9c-119">Bir hizmeti bir dinleyici ve kaynak öğeleri için aşağıdaki kodu ekleyerek döngüsel arabellek İzleme dinleyicisi kullanmak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="33f9c-120">En fazla dosya boyutunu ayarlayarak belirtilen `maxFileSizeKB` özniteliği döngüsel izleme dinleyicinin yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="33f9c-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="33f9c-121">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33f9c-121">This is demonstrated in the following code.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33f9c-122">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="33f9c-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="33f9c-123">Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33f9c-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="33f9c-124">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33f9c-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="33f9c-125">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33f9c-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33f9c-126">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="33f9c-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="33f9c-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="33f9c-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33f9c-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="33f9c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33f9c-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="33f9c-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="33f9c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33f9c-130">See also</span></span>

- [<span data-ttu-id="33f9c-131">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="33f9c-131">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)

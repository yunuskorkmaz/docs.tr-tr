---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59291b6a57ba602e5fea84dcd571a8d767b7cc04
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806815"
---
# <a name="extending-tracing"></a><span data-ttu-id="d4849-102">İzlemeyi Genişletme</span><span class="sxs-lookup"><span data-stu-id="d4849-102">Extending Tracing</span></span>
<span data-ttu-id="d4849-103">Bu örnek, Windows Communication Foundation (WCF) izleme özelliği, istemci ve hizmet kodu etkinliği kullanıcı tarafından tanımlanan izlemeleri yazarak genişletmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4849-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="d4849-104">Bu izleme etkinlikleri oluşturmak ve izlemeleri iş mantıksal birimler halinde gruplandırmak kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4849-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="d4849-105">Aktarımları (içinde aynı uç noktası) etkinlikleri ve yayma (uç noktalar arasında) ilişkilendirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d4849-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="d4849-106">Bu örnekte, hem istemci hem de hizmet için izleme etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d4849-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="d4849-107">İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz: [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="d4849-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="d4849-108">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d4849-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4849-109">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d4849-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4849-110">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d4849-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d4849-111">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d4849-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4849-112">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d4849-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4849-113">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d4849-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="d4849-114">İzleme ve Etkinlik yayma</span><span class="sxs-lookup"><span data-stu-id="d4849-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="d4849-115">Kullanıcı tanımlı Etkinlik izleme kendi iş mantıksal birimler Grup izlemeleri için izleme etkinliklerine oluşturmak, etkinlikleri aktarımları ve yayma ile ilişkilendirmek ve WCF izleme (örneğin, disk alanının maliyet performans maliyetini azaltmak olanak tanır. bir günlük dosyası).</span><span class="sxs-lookup"><span data-stu-id="d4849-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="d4849-116">Özel kaynakları ekleme</span><span class="sxs-lookup"><span data-stu-id="d4849-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="d4849-117">Kullanıcı tanımlı izlemeleri için hem istemci hem de hizmet kod eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d4849-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="d4849-118">İzleme kaynakları istemci veya hizmet yapılandırması dosyalara izin kaydedilir ve görüntülenen bu özel izlemeleri için ekleme [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d4849-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="d4849-119">Aşağıdaki kod adlı bir kullanıcı tarafından tanımlanan izleme kaynağı eklemeyi gösterir `ServerCalculatorTraceSource` yapılandırma dosyasına.</span><span class="sxs-lookup"><span data-stu-id="d4849-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a><span data-ttu-id="d4849-120">Bağıntı etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d4849-120">Correlating Activities</span></span>  
 <span data-ttu-id="d4849-121">Doğrudan uç noktalar arasında etkinliklerini ilişkilendirmek için `propagateActivity` özniteliği ayarlanmalıdır `true` içinde `System.ServiceModel` izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="d4849-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="d4849-122">Ayrıca, WCF etkinlikleri geçmeden izlemeleri yaymak için ServiceModel Etkinlik izleme kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4849-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="d4849-123">Bu, aşağıdaki kod örneğinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="d4849-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4849-124">ServiceModel etkinliği izleme devre dışı kapatma değil tarafından belirtilen izleme düzeyi sahip aynı `switchValue` özelliği ayarlamak kapalı.</span><span class="sxs-lookup"><span data-stu-id="d4849-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="d4849-125">Lessening performans maliyeti</span><span class="sxs-lookup"><span data-stu-id="d4849-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="d4849-126">Ayarı `ActivityTracing` içinde kapalı `System.ServiceModel` izleme kaynağı yalnızca kullanıcı tanımlı Etkinlik izleme, herhangi bir dahil ServiceModel etkinlik izlemeleri içeren bir izleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4849-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="d4849-127">Bu, çok daha küçük boyutu bir günlük dosyasında sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d4849-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="d4849-128">Ancak, izlemeleri işleme WCF ilişkilendirmek için Fırsat kaybolur.</span><span class="sxs-lookup"><span data-stu-id="d4849-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4849-129">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d4849-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d4849-130">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4849-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d4849-131">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4849-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d4849-132">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4849-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4849-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4849-133">See Also</span></span>  
 [<span data-ttu-id="d4849-134">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="d4849-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

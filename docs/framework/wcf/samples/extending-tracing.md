---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: c6d62f6c334261b0dc897a1c1a2cd71d40ee4f51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734928"
---
# <a name="extending-tracing"></a><span data-ttu-id="fc9a2-102">İzlemeyi Genişletme</span><span class="sxs-lookup"><span data-stu-id="fc9a2-102">Extending Tracing</span></span>
<span data-ttu-id="fc9a2-103">Bu örnek, istemci ve hizmet kodunda Kullanıcı tanımlı etkinlik izlemeleri yazarak Windows Communication Foundation (WCF) izleme özelliğinin nasıl genişletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="fc9a2-104">Bu, kullanıcının mantıksal iş birimlerine izleme etkinlikleri ve grup izlemeleri oluşturmalarına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="fc9a2-105">Ayrıca, etkinlikleri aktarımlar (aynı uç nokta içinde) ve yayma (uç noktalar arasında) ile ilişkilendirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="fc9a2-106">Bu örnekte, izleme hem istemci hem de hizmet için etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="fc9a2-107">İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [izleme ve mesaj günlüğü](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="fc9a2-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="fc9a2-108">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc9a2-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc9a2-110">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fc9a2-111">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-111">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fc9a2-112">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc9a2-113">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-113">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="fc9a2-114">İzleme ve etkinlik yayma</span><span class="sxs-lookup"><span data-stu-id="fc9a2-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="fc9a2-115">Kullanıcı tanımlı etkinlik izleme, kullanıcının izlemeleri mantıksal iş birimlerine göre gruplamak, aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirmek ve WCF izlemenin performans maliyetini azaltmak (örneğin, disk alanı maliyeti) için kendi izleme etkinliklerini oluşturmalarına olanak tanır. bir günlük dosyası).</span><span class="sxs-lookup"><span data-stu-id="fc9a2-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="fc9a2-116">Özel kaynak ekleme</span><span class="sxs-lookup"><span data-stu-id="fc9a2-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="fc9a2-117">Kullanıcı tanımlı izlemeler, hem istemci hem de hizmet koduna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="fc9a2-118">İstemci veya hizmet yapılandırma dosyalarına izleme kaynakları eklemek, bu özel izlemelerin [hizmet Izleme Görüntüleyicisi aracında (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kaydedilip görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="fc9a2-119">Aşağıdaki kod, `ServerCalculatorTraceSource` adlı Kullanıcı tanımlı izleme kaynağının yapılandırma dosyasına nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="fc9a2-120">Etkinlikleri ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="fc9a2-120">Correlating Activities</span></span>  
 <span data-ttu-id="fc9a2-121">Etkinlikleri doğrudan uç noktalar arasında ilişkilendirmek için, `propagateActivity` özniteliği `System.ServiceModel` izleme kaynağında `true` olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="fc9a2-122">Ayrıca, WCF etkinliklerinde ilerlemeden izlemeleri yaymak için, ServiceModel etkinliği Izlemenin kapalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="fc9a2-123">Bu, aşağıdaki kod örneğinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc9a2-124">ServiceModel etkinlik Izlemenin kapatılması, `switchValue` özelliği tarafından belirtilen izleme düzeyiyle aynı değildir ve kapalı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="fc9a2-125">Performans maliyetini azallama</span><span class="sxs-lookup"><span data-stu-id="fc9a2-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="fc9a2-126">`ActivityTracing` `System.ServiceModel` izleme kaynağında devre dışı olarak ayarlamak, yalnızca Kullanıcı tanımlı etkinlik izlemelerini içeren bir izleme dosyası oluşturur, hiçbir ServiceModel etkinlik izleme dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="fc9a2-127">Bu, çok daha küçük boyutta bir günlük dosyasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="fc9a2-128">Ancak, WCF işleme izlemelerinin ilişkilendirilmesi için fırsat kaybolur.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc9a2-129">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fc9a2-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fc9a2-130">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fc9a2-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fc9a2-132">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9a2-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc9a2-133">See also</span></span>

- <span data-ttu-id="fc9a2-134">[AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fc9a2-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

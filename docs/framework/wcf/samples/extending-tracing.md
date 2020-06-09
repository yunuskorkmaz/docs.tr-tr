---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59bdfeea41bac812840ffe166895050a6cd1ad2d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600522"
---
# <a name="extend-tracing"></a><span data-ttu-id="c84df-102">İzlemeyi Genişlet</span><span class="sxs-lookup"><span data-stu-id="c84df-102">Extend tracing</span></span>

<span data-ttu-id="c84df-103">Bu örnek, istemci ve hizmet kodunda Kullanıcı tanımlı etkinlik izlemeleri yazarak Windows Communication Foundation (WCF) izleme özelliğinin nasıl genişletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c84df-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="c84df-104">Kullanıcı tanımlı etkinlik izlemelerinin yazılması, kullanıcının mantıksal iş birimlerine izleme etkinlikleri ve grup izlemeleri oluşturmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c84df-104">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="c84df-105">Ayrıca, etkinlikleri aktarımlar (aynı uç nokta içinde) ve yayma (uç noktalar arasında) ile ilişkilendirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c84df-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="c84df-106">Bu örnekte, izleme hem istemci hem de hizmet için etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c84df-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="c84df-107">İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [izleme ve mesaj günlüğü](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="c84df-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="c84df-108">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="c84df-108">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c84df-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c84df-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c84df-110">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c84df-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c84df-111">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c84df-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c84df-112">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c84df-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c84df-113">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c84df-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="c84df-114">İzleme ve etkinlik yayma</span><span class="sxs-lookup"><span data-stu-id="c84df-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="c84df-115">Kullanıcı tanımlı etkinlik izleme, kullanıcının izlemeleri mantıksal iş birimlerine göre gruplamak, aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirmek ve WCF izlemenin (örneğin, bir günlük dosyasının disk alanı maliyeti) performans maliyetini azaltmak için kendi izleme etkinliklerini oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c84df-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="c84df-116">Özel Kaynak Ekle</span><span class="sxs-lookup"><span data-stu-id="c84df-116">Add custom sources</span></span>  
 <span data-ttu-id="c84df-117">Kullanıcı tanımlı izlemeler, hem istemci hem de hizmet koduna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c84df-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="c84df-118">İstemci veya hizmet yapılandırma dosyalarına izleme kaynakları eklemek, bu özel izlemelerin [hizmet Izleme Görüntüleyicisi aracında (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kaydedilmesini ve görüntülenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c84df-118">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="c84df-119">Aşağıdaki kod, yapılandırma dosyasına adlı Kullanıcı tanımlı izleme kaynağının nasıl ekleneceğini gösterir `ServerCalculatorTraceSource` .</span><span class="sxs-lookup"><span data-stu-id="c84df-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="c84df-120">Etkinlikleri ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="c84df-120">Correlate activities</span></span>  
 <span data-ttu-id="c84df-121">Etkinlikleri doğrudan uç noktalar arasında ilişkilendirmek için, `propagateActivity` özniteliği izleme kaynağında olarak ayarlanmalıdır `true` `System.ServiceModel` .</span><span class="sxs-lookup"><span data-stu-id="c84df-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="c84df-122">Ayrıca, WCF etkinliklerinde ilerlemeden izlemeleri yaymak için, ServiceModel etkinliği Izlemenin kapalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c84df-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="c84df-123">Bu, aşağıdaki kod örneğinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c84df-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c84df-124">ServiceModel etkinlik Izlemenin kapatılması, özelliği tarafından belirtilen izleme düzeyiyle aynı değildir ve `switchValue` kapalı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c84df-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="c84df-125">Performans maliyetini azaltır</span><span class="sxs-lookup"><span data-stu-id="c84df-125">Lessen performance cost</span></span>  
 <span data-ttu-id="c84df-126">`ActivityTracing` `System.ServiceModel` İzleme kaynağında kapalı ayarı, yalnızca Kullanıcı tanımlı etkinlik izlemelerini içeren bir izleme dosyası oluşturur ve bu da hiçbir ServiceModel etkinlik izlemeden dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="c84df-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="c84df-127">ServiceModel etkinliğinin dışlanması, daha küçük bir günlük dosyasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c84df-127">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="c84df-128">Ancak, WCF işleme izlemelerinin ilişkilendirilmesi için fırsat kaybolur.</span><span class="sxs-lookup"><span data-stu-id="c84df-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="c84df-129">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c84df-129">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c84df-130">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c84df-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c84df-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c84df-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c84df-132">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c84df-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84df-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c84df-133">See also</span></span>

- <span data-ttu-id="c84df-134">[AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c84df-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183684"
---
# <a name="extending-tracing"></a><span data-ttu-id="3bfc5-102">İzlemeyi Genişletme</span><span class="sxs-lookup"><span data-stu-id="3bfc5-102">Extending Tracing</span></span>
<span data-ttu-id="3bfc5-103">Bu örnek, istemci ve hizmet koduna kullanıcı tanımlı etkinlik izlemeleri yazarak Windows Communication Foundation (WCF) izleme özelliğinin nasıl genişletilebildiğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="3bfc5-104">Bu, kullanıcının izleme etkinlikleri oluşturmasına ve izlemeleri mantıksal çalışma birimlerine gruplandırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="3bfc5-105">Faaliyetleri aktarımlar (aynı uç nokta içinde) ve yayılma (uç noktalar arasında) yoluyla ilişkilendirmek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="3bfc5-106">Bu örnekte, izleme hem istemci hem de hizmet için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="3bfc5-107">İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirilen hakkında daha fazla bilgi için [Bkz.](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)</span><span class="sxs-lookup"><span data-stu-id="3bfc5-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="3bfc5-108">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bfc5-109">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3bfc5-110">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3bfc5-111">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3bfc5-112">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3bfc5-113">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="3bfc5-114">İzleme ve Aktivite Yayılımı</span><span class="sxs-lookup"><span data-stu-id="3bfc5-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="3bfc5-115">Kullanıcı tanımlı etkinlik izleme, kullanıcının izlemeleri mantıksal çalışma birimlerine gruplandırmak, aktarımlar ve yayılma yoluyla etkinlikleri ilişkilendirmek ve WCF izlemenin performans maliyetini (örneğin, disk alanı maliyeti) azaltması için kendi izleme etkinliklerini oluşturmasına olanak tanır bir günlük dosyasının).</span><span class="sxs-lookup"><span data-stu-id="3bfc5-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="3bfc5-116">Özel Kaynak Ekleme</span><span class="sxs-lookup"><span data-stu-id="3bfc5-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="3bfc5-117">Kullanıcı tanımlı izlemeler hem istemci hem de hizmet koduna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="3bfc5-118">İstemci veya hizmet yapılandırma dosyalarına izleme kaynakları eklemek, bu özel izlemelerin [Service Trace Viewer Tool 'da (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kaydedilmesine ve görüntülenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="3bfc5-119">Aşağıdaki kod, yapılandırma dosyasına kullanıcı `ServerCalculatorTraceSource` tanımlı bir izleme kaynağının nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="3bfc5-120">Korelasyon Faaliyetleri</span><span class="sxs-lookup"><span data-stu-id="3bfc5-120">Correlating Activities</span></span>  
 <span data-ttu-id="3bfc5-121">Etkinlikleri doğrudan uç noktalar arasında `propagateActivity` ilişkilendirmek için `true` öznitelik `System.ServiceModel` izleme kaynağına ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="3bfc5-122">Ayrıca, WCF etkinliklerinden geçmeden izlemeleri yaymak için ServiceModel Etkinlik İzleme solunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="3bfc5-123">Bu, aşağıdaki kod örneğinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bfc5-124">ServiceModel Etkinlik İzleme'yi kapatmak, özellik tarafından gösterilen izleme düzeyine `switchValue` sahip olmakla aynı şey değildir.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="3bfc5-125">Performans Maliyetini Azaltma</span><span class="sxs-lookup"><span data-stu-id="3bfc5-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="3bfc5-126">İzleme kaynağında kapalı `ActivityTracing` ayar, ServiceModel etkinlik izlerinin hiçbiri dahil edilmeden yalnızca kullanıcı tanımlı etkinlik izlemelerini içeren bir izleme dosyası oluşturur. `System.ServiceModel`</span><span class="sxs-lookup"><span data-stu-id="3bfc5-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="3bfc5-127">Bu çok daha küçük boyutlu bir günlük dosyası ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="3bfc5-128">Ancak, WCF işleme izlerini ilişkilendirme fırsatı kaybolur.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3bfc5-129">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3bfc5-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3bfc5-130">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3bfc5-131">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3bfc5-132">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bfc5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bfc5-133">See also</span></span>

- <span data-ttu-id="3bfc5-134">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3bfc5-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

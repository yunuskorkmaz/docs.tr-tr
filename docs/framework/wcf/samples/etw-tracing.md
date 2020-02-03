---
title: ETW İzleme
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: a62403e61e0566d5e7b753ff951bf4b316209b6f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742113"
---
# <a name="etw-tracing"></a><span data-ttu-id="7662d-102">ETW İzleme</span><span class="sxs-lookup"><span data-stu-id="7662d-102">ETW Tracing</span></span>
<span data-ttu-id="7662d-103">Bu örnek, Windows için olay Izleme (ETW) ve bu örnekle birlikte sunulan `ETWTraceListener` kullanarak uçtan uca (E2E) izlemenin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7662d-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="7662d-104">Örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ' i temel alır ve ETW izleme içerir.</span><span class="sxs-lookup"><span data-stu-id="7662d-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7662d-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="7662d-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7662d-106">Bu örnek, [izleme ve Ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)hakkında bilgi sahibi olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7662d-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="7662d-107"><xref:System.Diagnostics> izleme modelindeki her izleme kaynağı, verilerin nerede ve nasıl izlendiğinizi tespit eden birden fazla izleme dinleyicilerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7662d-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="7662d-108">Dinleyici türü, izleme verilerinin günlüğe kaydedildiği biçimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7662d-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="7662d-109">Aşağıdaki kod örneği, bir dinleyicinin yapılandırmaya nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7662d-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"   
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="7662d-110">Bu dinleyiciyi kullanmadan önce, bir ETW Izleme oturumunun başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7662d-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="7662d-111">Bu oturum, Logman. exe veya tracelog. exe kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="7662d-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="7662d-112">Bu örneğe eklenen bir SetupETW. bat dosyası, oturumu kapatmak ve günlük dosyasını tamamlamak için bir CleanupETW. bat dosyası ile birlikte ETW Izleme oturumunu ayarlayabilmeniz için eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7662d-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7662d-113">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="7662d-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="7662d-114">Bu araçlar hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="7662d-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="7662d-115">ETWTraceListener kullanılırken izlemeler ikili. etl dosyalarında günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7662d-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="7662d-116">ServiceModel izleme açık olduğunda, oluşturulan tüm izlemeler aynı dosyada görünür.</span><span class="sxs-lookup"><span data-stu-id="7662d-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="7662d-117">. Etl ve. svclog dosyalarını görüntülemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7662d-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="7662d-118">Görüntüleyici, bir iletiyi kaynağından hedefine ve tüketim noktasına izlemeyi olanaklı kılan sistemin uçtan uca bir görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7662d-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="7662d-119">ETW Izleme dinleyicisi döngüsel günlüğe yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="7662d-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="7662d-120">Bu özelliği etkinleştirmek için **Başlat**, **Çalıştır** ' a gidin ve `cmd` yazarak bir komut konsolunu başlatın.</span><span class="sxs-lookup"><span data-stu-id="7662d-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="7662d-121">Aşağıdaki komutta, `<logfilename>` parametresini günlük dosyanızın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7662d-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="7662d-122">`-f` ve `-max` anahtarları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7662d-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="7662d-123">İkili dairesel biçimi ve en fazla 1000MB günlük boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7662d-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="7662d-124">`-p` anahtarı, izleme sağlayıcısını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7662d-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="7662d-125">Örneğimizde, "XML ETW örnek sağlayıcısı" için GUID `"{411a0819-c24b-428c-83e2-26b41091702e}"`.</span><span class="sxs-lookup"><span data-stu-id="7662d-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="7662d-126">Oturumu başlatmak için aşağıdaki komutu yazın.</span><span class="sxs-lookup"><span data-stu-id="7662d-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="7662d-127">Günlüğe kaydetmeyi bitirdikten sonra, aşağıdaki komutla oturumu durdurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7662d-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="7662d-128">Bu işlem, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) veya tracerpt dahil olmak üzere seçim aracınkiyle işleyebilmeniz gereken ikili dairesel Günlükler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7662d-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="7662d-129">Ayrıca, döngüsel günlük kaydı gerçekleştirmek üzere alternatif bir dinleyici hakkında daha fazla bilgi için [dairesel izleme](../../../../docs/framework/wcf/samples/circular-tracing.md) örneğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7662d-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7662d-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7662d-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7662d-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7662d-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7662d-132">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7662d-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7662d-133">RegisterProvider. bat, SetupETW. bat ve CleanupETW. bat komutlarını kullanmak için bir yerel yönetici hesabı altında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7662d-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="7662d-134">Windows Vista veya sonraki bir sürümü kullanıyorsanız, komut istemi ' ni yükseltilmiş ayrıcalıklarla da çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7662d-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="7662d-135">Bunu yapmak için, komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7662d-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="7662d-136">Örneği çalıştırmadan önce, istemci ve sunucuda RegisterProvider. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7662d-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="7662d-137">Bu, hizmet Izleme Görüntüleyicisi tarafından okunabilen izlemeler üretmek için elde edilen ETWTracingSampleLog. etl dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7662d-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="7662d-138">Bu dosya C:\logs klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7662d-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="7662d-139">Bu klasör yoksa, oluşturulması veya bir izleme üretilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7662d-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="7662d-140">Ardından, ETW Izleme oturumunu başlatmak için istemci ve sunucu bilgisayarlarında SetupETW. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7662d-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="7662d-141">SetupETW. bat dosyası CS\Client klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7662d-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="7662d-142">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7662d-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="7662d-143">Örnek tamamlandığında, ETWTracingSampleLog. etl dosyası oluşturma işleminin tamamlanması için CleanupETW. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7662d-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="7662d-144">Hizmet Izleme Görüntüleyicisi içinden ETWTracingSampleLog. etl dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7662d-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="7662d-145">İkili biçimli dosyayı bir. svclog dosyası olarak kaydetmeniz istenecektir.</span><span class="sxs-lookup"><span data-stu-id="7662d-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="7662d-146">ETW ve ServiceModel izlemelerini görüntülemek için hizmet Izleme Görüntüleyicisi içinden yeni oluşturulan. svclog dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7662d-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7662d-147">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7662d-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7662d-148">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7662d-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7662d-149">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="7662d-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7662d-150">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7662d-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="7662d-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7662d-151">See also</span></span>

- <span data-ttu-id="7662d-152">[AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7662d-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

---
title: ETW İzleme
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183698"
---
# <a name="etw-tracing"></a><span data-ttu-id="6cf31-102">ETW İzleme</span><span class="sxs-lookup"><span data-stu-id="6cf31-102">ETW Tracing</span></span>
<span data-ttu-id="6cf31-103">Bu örnek, Windows için Olay İzleme (ETW) `ETWTraceListener` ve bu örnekle sağlanan Ları kullanarak Uçlardan Uca (E2E) izlemenin nasıl uygulanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="6cf31-104">Örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanmaktadır ve ETW izleme içerir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cf31-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6cf31-106">Bu örnek, İzleme ve [İleti Günlüğe Kaydetme'ye](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)aşina olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6cf31-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="6cf31-107">İzleme modelindeki <xref:System.Diagnostics> her izleme kaynağı, verilerin nerede ve nasıl izleyeceğini belirleyen birden çok izleme dinleyicisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="6cf31-108">Dinleyici türü, izleme verilerinin günlüğe kaydedildiği biçimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6cf31-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="6cf31-109">Aşağıdaki kod örneği, dinleyicinin yapılandırmaya nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="6cf31-110">Bu dinleyiciyi kullanmadan önce bir ETW İzleme Oturumu başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="6cf31-111">Bu oturum Logman.exe veya Tracelog.exe kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="6cf31-112">Bir SetupETW.bat dosyası oturumu kapatmak ve günlük dosyasını tamamlamak için bir CleanupETW.bat dosyası ile birlikte ETW İzleme Oturumu ayarlayabilirsiniz, böylece bu örnek ile birlikte dahildir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cf31-113">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="6cf31-114">Bu araçlar hakkında daha fazla bilgi için bkz.<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="6cf31-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="6cf31-115">ETWTraceListener kullanırken, izlemeler ikili .etl dosyalarında günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="6cf31-116">ServiceModel izleme açıkken, oluşturulan tüm izlemeler aynı dosyada görünür.</span><span class="sxs-lookup"><span data-stu-id="6cf31-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="6cf31-117">.etl ve .svclog günlük dosyalarını görüntülemek için [Service Trace Viewer Aracı'nı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="6cf31-118">Görüntüleyici, kaynağından hedefine ve tüketim noktasına kadar bir iletiyi izlemeyi mümkün kılan sistemin uçtan uca görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6cf31-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="6cf31-119">ETW Trace Listener dairesel günlüğe kaydetmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="6cf31-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="6cf31-120">Bu özelliği etkinleştirmek için **Başlat,** `cmd` **Çalıştır'a** gidin ve komut konsolunu başlatmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="6cf31-121">Aşağıdaki komutta, parametreyi `<logfilename>` günlük dosyanızın adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6cf31-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="6cf31-122">Ve `-f` `-max` anahtarları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="6cf31-123">Onlar ikili dairesel biçim ve 1000MB sırasıyla maksimum günlük boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="6cf31-124">Geçiş, `-p` izleme sağlayıcısını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="6cf31-125">Örneğimizde, `"{411a0819-c24b-428c-83e2-26b41091702e}"` "XML ETW Örnek Sağlayıcı" için GUID'dir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="6cf31-126">Oturumu başlatmak için aşağıdaki komutu yazın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="6cf31-127">Günlüğe kaydetmeyi bitirdikten sonra aşağıdaki komutla oturumu durdurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cf31-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="6cf31-128">Bu işlem, [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) veya Tracerpt dahil olmak üzere seçtiğiniz araçla işleyebileceğiniz ikili dairesel günlükler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6cf31-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="6cf31-129">Ayrıca dairesel günlük gerçekleştirmek için alternatif bir dinleyici hakkında daha fazla bilgi için [Dairesel İzleme](../../../../docs/framework/wcf/samples/circular-tracing.md) örneğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cf31-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6cf31-130">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6cf31-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6cf31-131">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6cf31-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6cf31-132">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6cf31-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6cf31-133">RegisterProvider.bat, SetupETW.bat ve CleanupETW.bat komutlarını kullanmak için yerel bir yönetici hesabı altında çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="6cf31-134">Windows Vista veya daha sonra kullanıyorsanız, komut istemini yüksek ayrıcalıklarla da çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="6cf31-135">Bunu yapmak için komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="6cf31-136">Örneği çalıştırmadan önce, istemci ve sunucuda RegisterProvider.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="6cf31-137">Bu, Service Trace Viewer tarafından okunabilen izlemeler oluşturmak için ortaya çıkan ETWTracingSampleLog.etl dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6cf31-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="6cf31-138">Bu dosya C:\logs klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="6cf31-139">Bu klasör yoksa, oluşturulmalı veya hiçbir iz oluşturulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="6cf31-140">Ardından, ETW İzleme Oturumu'nu başlatmak için istemci ve sunucu bilgisayarlarında SetupETW.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="6cf31-141">SetupETW.bat dosyası CS\Client klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="6cf31-142">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6cf31-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="6cf31-143">Örnek tamamlandığında, ETWTracingSampleLog.etl dosyasının oluşturulmasını tamamlamak için CleanupETW.bat'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="6cf31-144">ETWTracingSampleLog.etl dosyasını Service Trace Viewer içinden açın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="6cf31-145">İkili biçimlendirilmiş dosyayı .svclog dosyası olarak kaydetmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="6cf31-146">ETW ve ServiceModel izlerini görüntülemek için Service Trace Viewer içinden yeni oluşturulan .svclog dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6cf31-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6cf31-147">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf31-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6cf31-148">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6cf31-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6cf31-149">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="6cf31-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6cf31-150">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6cf31-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="6cf31-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cf31-151">See also</span></span>

- <span data-ttu-id="6cf31-152">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6cf31-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

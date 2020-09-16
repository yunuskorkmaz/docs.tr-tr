---
title: ETW İzleme
description: Bu örnek, Windows için olay Izleme (ETW) ve ETWTraceListener kullanarak uçtan uca (E2E) izlemenin nasıl uygulanacağını gösterir.
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 6e7526ef05d672b550599e3b12a4b083e9130b96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547147"
---
# <a name="etw-tracing"></a><span data-ttu-id="174a3-103">ETW İzleme</span><span class="sxs-lookup"><span data-stu-id="174a3-103">ETW Tracing</span></span>
<span data-ttu-id="174a3-104">Bu örnek, Windows için olay Izleme (ETW) ve `ETWTraceListener` Bu örnekle birlikte sunulan uçtan uca (e2e) izlemenin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="174a3-104">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="174a3-105">Örnek, [Başlarken](getting-started-sample.md) ' i temel alır ve ETW izleme içerir.</span><span class="sxs-lookup"><span data-stu-id="174a3-105">The sample is based on the [Getting Started](getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="174a3-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="174a3-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="174a3-107">Bu örnek, [izleme ve Ileti günlüğe kaydetme](tracing-and-message-logging.md)hakkında bilgi sahibi olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="174a3-107">This sample assumes that you are familiar with [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="174a3-108">İzleme modelindeki her izleme kaynağı, <xref:System.Diagnostics> verilerin nerede ve nasıl izlendiğinizi tespit eden birden fazla izleme dinleyicilerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="174a3-108">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="174a3-109">Dinleyici türü, izleme verilerinin günlüğe kaydedildiği biçimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="174a3-109">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="174a3-110">Aşağıdaki kod örneği, bir dinleyicinin yapılandırmaya nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="174a3-110">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="174a3-111">Bu dinleyiciyi kullanmadan önce, bir ETW Izleme oturumunun başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="174a3-111">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="174a3-112">Bu oturum, Logman.exe veya Tracelog.exe kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="174a3-112">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="174a3-113">Bu örneğe eklenen bir SetupETW.bat dosyası, oturumu kapatmak ve günlük dosyasını tamamlamak üzere bir CleanupETW.bat dosyası ile birlikte ETW Izleme oturumu ayarlayabilmeniz için eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="174a3-113">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="174a3-114">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="174a3-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="174a3-115">Bu araçlar hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="174a3-115">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="174a3-116">ETWTraceListener kullanılırken izlemeler ikili. etl dosyalarında günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="174a3-116">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="174a3-117">ServiceModel izleme açık olduğunda, oluşturulan tüm izlemeler aynı dosyada görünür.</span><span class="sxs-lookup"><span data-stu-id="174a3-117">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="174a3-118">. Etl ve. svclog dosyalarını görüntülemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="174a3-118">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="174a3-119">Görüntüleyici, bir iletiyi kaynağından hedefine ve tüketim noktasına izlemeyi olanaklı kılan sistemin uçtan uca bir görünümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="174a3-119">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="174a3-120">ETW Izleme dinleyicisi döngüsel günlüğe yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="174a3-120">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="174a3-121">Bu özelliği etkinleştirmek için **Başlat**, **Çalıştır** ve yazın ' a giderek `cmd` bir komut konsolu başlatın.</span><span class="sxs-lookup"><span data-stu-id="174a3-121">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="174a3-122">Aşağıdaki komutta, `<logfilename>` parametresini günlük dosyanızın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="174a3-122">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="174a3-123">`-f`Ve `-max` anahtarları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="174a3-123">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="174a3-124">İkili dairesel biçimi ve en fazla 1000MB günlük boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="174a3-124">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="174a3-125">`-p`Anahtar, izleme sağlayıcısını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="174a3-125">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="174a3-126">Örneğimizde, `"{411a0819-c24b-428c-83e2-26b41091702e}"` "XML ETW örnek sağlayıcısı" IÇIN GUID kullanılır.</span><span class="sxs-lookup"><span data-stu-id="174a3-126">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="174a3-127">Oturumu başlatmak için aşağıdaki komutu yazın.</span><span class="sxs-lookup"><span data-stu-id="174a3-127">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="174a3-128">Günlüğe kaydetmeyi bitirdikten sonra, aşağıdaki komutla oturumu durdurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="174a3-128">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="174a3-129">Bu işlem, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) veya tracerpt dahil olmak üzere seçim aracınkiyle işleyebileceğinizi ikili dairesel Günlükler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="174a3-129">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="174a3-130">Ayrıca, döngüsel günlük kaydı gerçekleştirmek üzere alternatif bir dinleyici hakkında daha fazla bilgi için [dairesel izleme](circular-tracing.md) örneğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="174a3-130">You can also review the [Circular Tracing](circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="174a3-131">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="174a3-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="174a3-132">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="174a3-132">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="174a3-133">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="174a3-133">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="174a3-134">RegisterProvider.bat, SetupETW.bat ve CleanupETW.bat komutlarını kullanmak için bir yerel yönetici hesabı altında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="174a3-134">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="174a3-135">Windows Vista veya sonraki bir sürümü kullanıyorsanız, komut istemi ' ni yükseltilmiş ayrıcalıklarla da çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="174a3-135">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="174a3-136">Bunu yapmak için, komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="174a3-136">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="174a3-137">Örneği çalıştırmadan önce, istemci ve sunucu üzerinde RegisterProvider.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="174a3-137">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="174a3-138">Bu, hizmet Izleme Görüntüleyicisi tarafından okunabilen izlemeler üretmek için elde edilen ETWTracingSampleLog. etl dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="174a3-138">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="174a3-139">Bu dosya C:\logs klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="174a3-139">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="174a3-140">Bu klasör yoksa, oluşturulması veya bir izleme üretilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="174a3-140">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="174a3-141">Ardından, ETW Izleme oturumunu başlatmak için istemci ve sunucu bilgisayarlarında SetupETW.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="174a3-141">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="174a3-142">SetupETW.bat dosyası CS\Client klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="174a3-142">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="174a3-143">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="174a3-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="174a3-144">Örnek tamamlandığında, ETWTracingSampleLog. etl dosyası oluşturma işleminin tamamlanması için CleanupETW.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="174a3-144">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="174a3-145">Hizmet Izleme Görüntüleyicisi içinden ETWTracingSampleLog. etl dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="174a3-145">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="174a3-146">İkili biçimli dosyayı bir. svclog dosyası olarak kaydetmeniz istenecektir.</span><span class="sxs-lookup"><span data-stu-id="174a3-146">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="174a3-147">ETW ve ServiceModel izlemelerini görüntülemek için hizmet Izleme Görüntüleyicisi içinden yeni oluşturulan. svclog dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="174a3-147">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="174a3-148">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="174a3-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="174a3-149">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="174a3-149">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="174a3-150">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="174a3-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="174a3-151">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="174a3-151">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="174a3-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="174a3-152">See also</span></span>

- <span data-ttu-id="174a3-153">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="174a3-153">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

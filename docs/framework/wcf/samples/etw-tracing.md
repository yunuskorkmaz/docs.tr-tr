---
title: "ETW İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d45852a8e03ac63ea6412e6f5b176f06fe83eb03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="etw-tracing"></a><span data-ttu-id="e1e0f-102">ETW İzleme</span><span class="sxs-lookup"><span data-stu-id="e1e0f-102">ETW Tracing</span></span>
<span data-ttu-id="e1e0f-103">Bu örnek olay izleme için Windows (ETW) kullanarak uçtan uca (E2E) izleme uygulamak nasıl gösterir ve `ETWTraceListener` Bu örnek ile sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="e1e0f-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve ETW İzleme içerir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1e0f-105">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e1e0f-106">Bu örnek aşina olduğunuzu varsayar [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="e1e0f-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="e1e0f-107">Her izleme kaynağı <xref:System.Diagnostics> izleme model verileri nerede ve nasıl izleneceğini belirlemek birden fazla iz dinleyicileri sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="e1e0f-108">Dinleyici türü izleme veriler günlüğe kaydedilir biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="e1e0f-109">Aşağıdaki kod örneği, yapılandırmaya dinleyiciyi ekleyin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="e1e0f-110">Bu dinleyici kullanmadan önce bir ETW izleme oturumunu başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="e1e0f-111">Bu oturumda Logman.exe veya Tracelog.exe kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="e1e0f-112">Oturumu kapatma ve günlük dosyası tamamlamak için bir CleanupETW.bat dosyasıyla birlikte ETW izleme oturumunu ayarlayabilirsiniz böylece SetupETW.bat dosya ile bu örnek dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1e0f-113">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="e1e0f-114">Bu araçlar hakkında daha fazla bilgi için bkz: [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)</span><span class="sxs-lookup"><span data-stu-id="e1e0f-114">For more information about these tools, see [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)</span></span>  
  
 <span data-ttu-id="e1e0f-115">ETWTraceListener kullanırken, izlemeleri ikili .etl dosyaları günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="e1e0f-116">ServiceModel izleme açık olan tüm oluşturulan izlemeleri aynı dosyada görünür.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="e1e0f-117">Kullanım [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .etl ve .svclog günlük dosyalarını görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="e1e0f-118">Görüntüleyici bir ileti hedefine kaynağından izlemenizi olanaklı kılan sistem uçtan uca görünümünü ve tüketiminin noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="e1e0f-119">ETW İzleme dinleyicisi döngüsel günlüğü destekler.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="e1e0f-120">Bu özelliği etkinleştirmek için şu adrese gidin **Başlat**, **çalıştırmak** ve türü `cmd` komut Konsolu'nu başlatın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="e1e0f-121">Aşağıdaki komutta, `<logfilename>` parametresiyle birlikte, günlük dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="e1e0f-122">`-f` Ve `-max` anahtarları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="e1e0f-123">Bunlar ikili döngüsel biçimi ve 1000 MB maksimum günlük dosyası boyutu sırasıyla belirtin.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="e1e0f-124">`-p` Anahtar izleme sağlayıcısı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="e1e0f-125">Örneğimizde `"{411a0819-c24b-428c-83e2-26b41091702e}"` GUID "XML ETW örnek" sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="e1e0f-126">Oturumu başlatmak için aşağıdaki komutu yazın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-126">To start the session, type in the following command.</span></span>  
  
```  
Logman start Wcf  
```  
  
 <span data-ttu-id="e1e0f-127">Günlük kaydı tamamladıktan sonra aşağıdaki komutu oturumla durdurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```  
Logman stop Wcf  
```  
  
 <span data-ttu-id="e1e0f-128">Bu işlem, seçeceğiniz araç ile işleyebilir ikili döngüsel günlükleri oluşturur dahil olmak üzere [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) veya Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="e1e0f-129">Ayrıca gözden geçirebilirsiniz [döngüsel izleme](../../../../docs/framework/wcf/samples/circular-tracing.md) döngüsel günlüğü gerçekleştirmek için alternatif bir dinleyici hakkında daha fazla bilgi için örnek.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1e0f-130">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="e1e0f-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e1e0f-131">Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1e0f-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e1e0f-132">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1e0f-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1e0f-133">RegisterProvider.bat, SetupETW.bat ve CleanupETW.bat komutlarını kullanmak için bir yerel yönetici hesabı altında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="e1e0f-134">Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya daha sonra da komut isteminde yükseltilmiş ayrıcalıklarla çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-134">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)] or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="e1e0f-135">Bunu yapmak için komut istemi simgesine sağ tıklayın ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="e1e0f-136">Örneği çalıştırmadan önce istemci ve sunucu üzerinde RegisterProvider.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="e1e0f-137">Bu hizmet izleme görüntüleyicisini tarafından okunabilir izlemeleri oluşturmak için sonuçta elde edilen ETWTracingSampleLog.etl dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="e1e0f-138">Bu dosya C:\logs klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="e1e0f-139">Bu klasör yoksa oluşturulması gerekir veya hiç izlemeleri üretilir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="e1e0f-140">Ardından, SetupETW.bat ETW İzleme oturumu başlatmak için istemci ve sunucu bilgisayarda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="e1e0f-141">SetupETW.bat dosya CS\Client klasörü altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4.  <span data-ttu-id="e1e0f-142">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1e0f-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="e1e0f-143">Örnek tamamlandığında ETWTracingSampleLog.etl dosya oluşturma işlemini tamamlamak için CleanupETW.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6.  <span data-ttu-id="e1e0f-144">Hizmet izleme görüntüleyicisini içinde ETWTracingSampleLog.etl dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="e1e0f-145">Biçimlendirilmiş bir ikili dosyası .svclog dosyası olarak kaydetmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7.  <span data-ttu-id="e1e0f-146">ETW ve ServiceModel izlemeleri görüntülemek için hizmet izleme görüntüleyicisini içinde yeni oluşturulan .svclog dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1e0f-147">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e1e0f-148">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e1e0f-149">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1e0f-150">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="e1e0f-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1e0f-151">See Also</span></span>  
 [<span data-ttu-id="e1e0f-152">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="e1e0f-152">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

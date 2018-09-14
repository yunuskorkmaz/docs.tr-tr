---
title: İleti İzleme ve Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 7f729e845fe552d523a46a1783404baf4e0bbfca
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569417"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="e6c56-102">İleti İzleme ve Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e6c56-102">Tracing and Message Logging</span></span>
<span data-ttu-id="e6c56-103">Bu örnek, izleme ve ileti günlüğe kaydetmeyi etkinleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6c56-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="e6c56-104">Sonuçta elde edilen izleme ve ileti günlüklerini kullanarak görüntülenen [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e6c56-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="e6c56-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e6c56-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6c56-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="e6c56-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="e6c56-107">İzleme</span><span class="sxs-lookup"><span data-stu-id="e6c56-107">Tracing</span></span>  
 <span data-ttu-id="e6c56-108">Windows Communication Foundation (WCF) kullanan tanımlanan izleme mekanizması <xref:System.Diagnostics> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e6c56-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="e6c56-109">Bu izleme modelinde, izleme verilerini, uygulamalarını uygulamak iz kaynakları tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e6c56-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="e6c56-110">Her kaynak bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e6c56-110">Each source is identified by a name.</span></span> <span data-ttu-id="e6c56-111">İzleme Tüketiciler, bilgi almak istediğiniz izleme kaynakları için izleme dinleyicilerine oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6c56-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="e6c56-112">İzleme verilerini almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6c56-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="e6c56-113">WCF'de, bu hizmet modeli iz ayarlayarak hizmet veya istemcinin yapılandırma dosyasına aşağıdaki kodu ekleyerek yapılabilir `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="e6c56-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="e6c56-114">İzleme kaynağı bölümünde izleme kaynakları hakkında daha fazla bilgi için bkz. [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konu.</span><span class="sxs-lookup"><span data-stu-id="e6c56-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="e6c56-115">Etkinlik izleme ve yayma</span><span class="sxs-lookup"><span data-stu-id="e6c56-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="e6c56-116">Sahip `ActivityTracing` etkin ve `propagateActivity` kümesine `true` içinde `system.ServiceModel` izleme kaynakları için hem istemci hem de hizmet uç noktaları (içindeki etkinlikleri arasında mantıksal birimler (etkinlik) işlem içinde izlemeleri bağıntısı sağlayın Etkinlik aktarımları için) üzerinden ve birden fazla uç noktası (aracılığıyla, etkinlik kimliği yayma) kapsayan etkinlikler arasında.</span><span class="sxs-lookup"><span data-stu-id="e6c56-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="e6c56-117">Bu üç mekanizmalar (etkinlikler, aktarımı ve yayma) daha hızlı bir şekilde hizmet izleme görüntüleyicisini aracını kullanarak bir hata kök nedenini bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6c56-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="e6c56-118">Daha fazla bilgi için [ilişkilendirilmiş izlemeleri görüntülemek ve sorun giderme için hizmet izleme görüntüleyicisini kullanarak](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="e6c56-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="e6c56-119">Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sağlanan izleme genişletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e6c56-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="e6c56-120">Kullanıcı tanımlı Etkinlik izleme için izleme etkinliklerin oluşturmasına olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="e6c56-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="e6c56-121">Grup izlemeleri içine mantıksal iş birimleri.</span><span class="sxs-lookup"><span data-stu-id="e6c56-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="e6c56-122">Etkinlikleri aktarımları ve yayma ile ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="e6c56-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="e6c56-123">WCF izleme (örneğin, bir günlük dosyası disk alanı maliyeti) performans maliyeti azalır.</span><span class="sxs-lookup"><span data-stu-id="e6c56-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="e6c56-124">Kullanıcı tanımlı Etkinlik izleme hakkında daha fazla bilgi için lütfen bkz [genişletme izleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e6c56-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="e6c56-125">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e6c56-125">Message Logging</span></span>  
 <span data-ttu-id="e6c56-126">Hem istemci hem de hizmet herhangi bir WCF uygulaması, ileti günlüğe kaydetme etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6c56-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="e6c56-127">İleti günlüğü etkinleştirmek için istemci veya hizmet için aşağıdaki kodu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="e6c56-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e6c56-128">Bir ileti kaydedildiği olup, istemci veya sunucu izlenen üzerinde izleme türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6c56-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="e6c56-129">Örneğin, aynı iletiyi hizmetine "TransportRead" kategorisi altında izlenen ise istemcide "TransportWrite" kategorisi altındaki bir istemciye gönderilen ileti bir "Ekle" izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="e6c56-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="e6c56-130">Aşağıdaki kodu ekleyerek İzleme dinleyicisi yapılandırma <xref:System.Diagnostics> istemcinin App.config dosyasının veya hizmetin Web.config dosyasının bölümü:</span><span class="sxs-lookup"><span data-stu-id="e6c56-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="e6c56-131">Yapılandırma dosyasında belirtilen hedef dizin XML biçiminde iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e6c56-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6c56-132">İzleme dosyaları, başlangıçta günlük dizini oluşturmadan oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e6c56-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="e6c56-133">Dinleyici Yapılandırması'nda bir alternatif günlük dizinini belirtin veya C:\logs\ dizinin var olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e6c56-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="e6c56-134">Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e6c56-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="e6c56-135">Günlüğe ileti kaydetme hakkında daha fazla bilgi için bkz: [iletileri günlüğe kaydetmeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konu.</span><span class="sxs-lookup"><span data-stu-id="e6c56-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6c56-136">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e6c56-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e6c56-137">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6c56-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e6c56-138">İzleme ve ileti günlüğe kaydetme örneği çalıştırmadan önce .svclog dosyalara yazmak için C:\logs\ hizmeti için dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6c56-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="e6c56-139">Bu dizinin adını, izleme ve günlüğe kaydedilecek ileti için yol olarak yapılandırma dosyasında tanımlanır ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e6c56-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="e6c56-140">Ağ hizmeti yazma erişimi kullanıcı logs dizininde verin.</span><span class="sxs-lookup"><span data-stu-id="e6c56-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="e6c56-141">Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6c56-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e6c56-142">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6c56-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6c56-143">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="e6c56-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e6c56-144">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e6c56-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e6c56-145">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e6c56-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6c56-146">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e6c56-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="e6c56-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6c56-147">See Also</span></span>  
 [<span data-ttu-id="e6c56-148">İzleme</span><span class="sxs-lookup"><span data-stu-id="e6c56-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e6c56-149">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="e6c56-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)

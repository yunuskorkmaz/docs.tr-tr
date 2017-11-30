---
title: "İleti İzleme ve Kaydetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: "53"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a73c6e544b7aae003a525c29743d68db18a54515
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="d64b2-102">İleti İzleme ve Kaydetme</span><span class="sxs-lookup"><span data-stu-id="d64b2-102">Tracing and Message Logging</span></span>
<span data-ttu-id="d64b2-103">Bu örnek, ileti izleme ve kaydetme etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d64b2-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="d64b2-104">Sonuçta elde edilen izlemeleri ve ileti günlüklerini kullanarak görüntülenen [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d64b2-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="d64b2-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d64b2-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d64b2-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d64b2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="d64b2-107">İzleme</span><span class="sxs-lookup"><span data-stu-id="d64b2-107">Tracing</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="d64b2-108">tanımlanan izleme mekanizması kullanır <xref:System.Diagnostics> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d64b2-108"> uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="d64b2-109">Bu izleme modelde izleme verilerini uygulamalarını uygulamak izleme kaynaklar tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d64b2-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="d64b2-110">Her kaynak adına göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d64b2-110">Each source is identified by a name.</span></span> <span data-ttu-id="d64b2-111">İzleme dinleyicileri bilgilerini almak istediği izleme kaynakları için izleme tüketicileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d64b2-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="d64b2-112">İzleme verilerini almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d64b2-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="d64b2-113">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu iki hizmetin için aşağıdaki kodu ekleyerek yapılabilir veya istemcinin yapılandırma dosyası hizmet modeli izleme kaynağı ayarlayarak `switchValue`:</span><span class="sxs-lookup"><span data-stu-id="d64b2-113">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="d64b2-114">İzleme kaynakları hakkında daha fazla bilgi için bkz: izleme kaynağı bölümünde [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d64b2-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="d64b2-115">Etkinlik izleme ve yayma</span><span class="sxs-lookup"><span data-stu-id="d64b2-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="d64b2-116">Sahip `ActivityTracing` etkin ve `propagateActivity` kümesine `true` içinde `system.ServiceModel` izleme kaynakları hem istemci hem de hizmet uç noktaları ('nda etkinlikler arasında bağıntı (aktiviteler) işleme mantıksal birimler içinde izlemeleri sağlayın Etkinlik aktarımları için) üzerinden ve birden fazla uç noktası (aracılığıyla, etkinlik kimliği yayma) kapsayıcı etkinlikler arasında.</span><span class="sxs-lookup"><span data-stu-id="d64b2-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="d64b2-117">Bu üç mekanizma (etkinlikleri, aktarımları ve yayma) daha hızlı bir şekilde hizmet izleme görüntüleyicisini aracını kullanarak bir hatasının kök nedenini bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d64b2-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="d64b2-118">Daha fazla bilgi için bkz: [bağıntılı izlemeleri görüntüleme ve sorun giderme için hizmet izleme görüntüleyicisini kullanma](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="d64b2-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="d64b2-119">Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sağlanan izleme genişletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d64b2-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="d64b2-120">Kullanıcı tanımlı Etkinlik izleme için izleme etkinliklerini oluşturmasına olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="d64b2-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="d64b2-121">Grup izlemeleri iş mantıksal birimler halinde.</span><span class="sxs-lookup"><span data-stu-id="d64b2-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="d64b2-122">Etkinlikler aktarımları ve yayma ile ilişkilendirilmesi.</span><span class="sxs-lookup"><span data-stu-id="d64b2-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="d64b2-123">Performans maliyetini azaltmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izleme (örneğin, disk alanı maliyeti bir günlük dosyası).</span><span class="sxs-lookup"><span data-stu-id="d64b2-123">Lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="d64b2-124">Kullanıcı tanımlı Etkinlik izleme hakkında daha fazla bilgi için lütfen bkz [genişletme izleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d64b2-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="d64b2-125">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="d64b2-125">Message Logging</span></span>  
 <span data-ttu-id="d64b2-126">İleti günlüğe kaydetme etkinleştirilebilir, hem istemci hem de hizmet herhangi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="d64b2-126">Message logging can be enabled both on the client and service of any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="d64b2-127">İleti günlüğe kaydetme etkinleştirmek için istemci veya hizmet için aşağıdaki kodu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="d64b2-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d64b2-128">Bir ileti kaydedildiğinde, izleme türü olup olmadığını, istemci veya sunucu izlenen üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d64b2-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="d64b2-129">Örneğin, aynı ileti konuşması "TransportRead" kategorisi altında izlenen ise istemcide "TransportWrite" kategorisi altında bir istemciye gönderilen bir "Ekle" iletisi izleneceğini.</span><span class="sxs-lookup"><span data-stu-id="d64b2-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="d64b2-130">Aşağıdaki kodu ekleyerek İzleme dinleyicisi yapılandırma <xref:System.Diagnostics> istemcinin App.config dosyası veya hizmetin Web.config dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="d64b2-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="d64b2-131">İletileri yapılandırma dosyasında belirtilen hedef dizinin XML biçiminde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d64b2-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d64b2-132">İzleme dosyaları başlangıçta günlük dizinini oluşturmadan oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="d64b2-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="d64b2-133">Dinleyici Yapılandırması'nda bir alternatif günlük dizinini belirtin veya C:\logs\ dizinin var olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d64b2-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="d64b2-134">Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="d64b2-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="d64b2-135">İleti günlüğe kaydetme hakkında daha fazla bilgi için bkz: [yapılandırma ileti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d64b2-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d64b2-136">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d64b2-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d64b2-137">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d64b2-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d64b2-138">İzleme ve ileti günlüğe kaydetme örneği çalıştırmadan önce .svclog dosyaları yazmak için C:\logs\ hizmeti için dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d64b2-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="d64b2-139">Bu dizinin adı yapılandırma dosyasında izlemeleri ve günlüğe kaydedilecek iletileri için yol olarak tanımlanır ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d64b2-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="d64b2-140">Günlükleri dizinine kullanıcı ağ hizmeti yazma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="d64b2-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="d64b2-141">C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d64b2-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="d64b2-142">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d64b2-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d64b2-143">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d64b2-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d64b2-144">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d64b2-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d64b2-145">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d64b2-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d64b2-146">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d64b2-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="d64b2-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d64b2-147">See Also</span></span>  
 [<span data-ttu-id="d64b2-148">İzleme</span><span class="sxs-lookup"><span data-stu-id="d64b2-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d64b2-149">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="d64b2-149">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

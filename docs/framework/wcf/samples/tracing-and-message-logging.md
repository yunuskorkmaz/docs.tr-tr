---
title: İleti İzleme ve Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: a58541b7d50d83d1e39d7c9dd9c58be4111ec494
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038735"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="3f87f-102">İleti İzleme ve Kaydetme</span><span class="sxs-lookup"><span data-stu-id="3f87f-102">Tracing and Message Logging</span></span>
<span data-ttu-id="3f87f-103">Bu örnek, izleme ve ileti günlüğe kaydetmenin nasıl etkinleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="3f87f-104">Ortaya çıkan izlemeler ve ileti günlükleri, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="3f87f-105">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="3f87f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f87f-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3f87f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="3f87f-107">İzleme</span><span class="sxs-lookup"><span data-stu-id="3f87f-107">Tracing</span></span>  
 <span data-ttu-id="3f87f-108">Windows Communication Foundation (WCF), <xref:System.Diagnostics> ad alanında tanımlanan izleme mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f87f-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="3f87f-109">Bu izleme modelinde, izleme verileri uygulamaların uygulayan izleme kaynakları tarafından üretilir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="3f87f-110">Her kaynak bir ad ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3f87f-110">Each source is identified by a name.</span></span> <span data-ttu-id="3f87f-111">İzleme tüketicileri, bilgi almak istedikleri izleme kaynakları için izleme dinleyicileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f87f-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="3f87f-112">İzleme verileri almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="3f87f-113">WCF 'de, hizmet modeli izleme kaynağı `switchValue`ayarlanarak hizmetin veya istemcinin yapılandırma dosyasına aşağıdaki kod eklenerek bu yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="3f87f-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="3f87f-114">İzleme kaynakları hakkında daha fazla bilgi için [Izlemeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konusunun Kaynak izleme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3f87f-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="3f87f-115">Etkinlik Izleme ve yayma</span><span class="sxs-lookup"><span data-stu-id="3f87f-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="3f87f-116">Hem `ActivityTracing` istemci hem `propagateActivity` de hizmet `true` için `system.ServiceModel` izleme kaynaklarında etkinleştirilmiş ve olarak ayarlanmış olması, uç noktalar içindeki etkinliklerde (etkinlikler) mantıksal işleme (etkinlik) içindeki izlemelerin bağıntısını sağlar ( etkinlik aktarımları aracılığıyla) ve birden çok uç noktayı kapsayan etkinlikler arasında (etkinlik KIMLIĞI yayma aracılığıyla).</span><span class="sxs-lookup"><span data-stu-id="3f87f-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="3f87f-117">Bu üç mekanizma (Etkinlikler, aktarımlar ve yayma), hizmet Izleme Görüntüleyicisi aracını kullanarak bir hatanın kök nedenini daha hızlı bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="3f87f-118">Daha fazla bilgi için bkz. [bağıntılı izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3f87f-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="3f87f-119">Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sunulan izlemeyi genişletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3f87f-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="3f87f-120">Kullanıcı tanımlı etkinlik izleme, kullanıcının şunları yapmak için izleme etkinlikleri oluşturmasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="3f87f-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="3f87f-121">İzlemeleri mantıksal iş birimlerine göre gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="3f87f-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="3f87f-122">Aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="3f87f-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="3f87f-123">WCF izlemenin (örneğin, bir günlük dosyasının disk alanı maliyeti) performans maliyetini azaltır.</span><span class="sxs-lookup"><span data-stu-id="3f87f-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="3f87f-124">Kullanıcı tanımlı etkinlik izleme hakkında daha fazla bilgi için lütfen [genişletme izleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="3f87f-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="3f87f-125">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="3f87f-125">Message Logging</span></span>  
 <span data-ttu-id="3f87f-126">İleti günlüğe kaydetme her ikisi de herhangi bir WCF uygulamasının istemcisinde ve hizmetinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="3f87f-127">İleti günlüğe kaydetmeyi etkinleştirmek için, istemci veya hizmete aşağıdaki kodu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="3f87f-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="3f87f-128">İleti kaydedildiğinde, izleme türü istemcide mi yoksa sunucuda mı izlenmekte olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f87f-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="3f87f-129">Örneğin, bir istemciye gönderilen "Ekle" iletisi, istemcideki "TransportWrite" kategorisinin altında izleniyorsa, hizmette "TransportRead" kategorisinin altında aynı ileti de izlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="3f87f-130">Aşağıdaki kodu <xref:System.Diagnostics> istemcinin App. config dosyasının veya hizmetin Web. config dosyasının bölümüne ekleyerek izleme dinleyicisini yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="3f87f-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="3f87f-131">İletiler, yapılandırma dosyasında belirtilen hedef dizinde XML biçiminde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f87f-132">İzleme dosyaları, başlangıçta günlük dizini oluşturulmadan oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="3f87f-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="3f87f-133">C:\logs\ dizininin var olduğundan emin olun veya dinleyici yapılandırmasında alternatif bir günlük dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="3f87f-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="3f87f-134">Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="3f87f-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="3f87f-135">İleti günlüğü hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="3f87f-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f87f-136">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3f87f-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3f87f-137">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3f87f-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3f87f-138">Izleme ve Ileti günlüğü örneğini çalıştırmadan önce, hizmet için C:\logs\ dizinini oluşturarak. svclog dosyalarını öğesine yazın.</span><span class="sxs-lookup"><span data-stu-id="3f87f-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="3f87f-139">Bu dizinin adı yapılandırma dosyasında günlüğe kaydedilecek izlemeler ve iletilerin yolu olarak tanımlanır ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="3f87f-140">Kullanıcı ağ hizmetine Günlükler dizinine yazma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="3f87f-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="3f87f-141">Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f87f-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3f87f-142">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3f87f-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3f87f-143">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f87f-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3f87f-144">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3f87f-144">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3f87f-145">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="3f87f-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f87f-146">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3f87f-146">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="3f87f-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f87f-147">See also</span></span>

- [<span data-ttu-id="3f87f-148">İzleme</span><span class="sxs-lookup"><span data-stu-id="3f87f-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="3f87f-149">AppFabric Izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="3f87f-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)

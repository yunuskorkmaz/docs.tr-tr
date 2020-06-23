---
title: İleti İzleme ve Kaydetme
description: Bu WFC örneğini kullanarak izlemeleri ve ileti günlüklerini görüntülemek için hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer.exe) nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: bb49334252c2415223b0f8f5559a6dc838d175e3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246031"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="a181d-103">İleti İzleme ve Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a181d-103">Tracing and Message Logging</span></span>
<span data-ttu-id="a181d-104">Bu örnek, izleme ve ileti günlüğe kaydetmenin nasıl etkinleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a181d-104">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="a181d-105">Ortaya çıkan izlemeler ve ileti günlükleri, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a181d-105">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="a181d-106">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="a181d-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a181d-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a181d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="a181d-108">İzleme</span><span class="sxs-lookup"><span data-stu-id="a181d-108">Tracing</span></span>  
 <span data-ttu-id="a181d-109">Windows Communication Foundation (WCF), ad alanında tanımlanan izleme mekanizmasını kullanır <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="a181d-109">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="a181d-110">Bu izleme modelinde, izleme verileri uygulamaların uygulayan izleme kaynakları tarafından üretilir.</span><span class="sxs-lookup"><span data-stu-id="a181d-110">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="a181d-111">Her kaynak bir ad ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a181d-111">Each source is identified by a name.</span></span> <span data-ttu-id="a181d-112">İzleme tüketicileri, bilgi almak istedikleri izleme kaynakları için izleme dinleyicileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a181d-112">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="a181d-113">İzleme verileri almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a181d-113">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="a181d-114">WCF 'de, hizmet modeli izleme kaynağı ayarlanarak hizmetin veya istemcinin yapılandırma dosyasına aşağıdaki kod eklenerek bu yapılabilir `switchValue` :</span><span class="sxs-lookup"><span data-stu-id="a181d-114">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="a181d-115">İzleme kaynakları hakkında daha fazla bilgi için [Izlemeyi yapılandırma](../diagnostics/tracing/configuring-tracing.md) konusunun Kaynak izleme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a181d-115">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="a181d-116">Etkinlik Izleme ve yayma</span><span class="sxs-lookup"><span data-stu-id="a181d-116">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="a181d-117">`ActivityTracing` `propagateActivity` `true` `system.ServiceModel` Hem istemci hem de hizmet için izleme kaynaklarında etkinleştirilmiş ve olarak ayarlanmış olması, mantıksal işlem (etkinlik) birimleri içinde, uç noktaların içindeki etkinliklerde (etkinlik aktarımları aracılığıyla) ve birden çok uç noktayı kapsayan etkinliklerde (etkinlik kimliği yayma aracılığıyla) izleme bağıntısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a181d-117">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="a181d-118">Bu üç mekanizma (Etkinlikler, aktarımlar ve yayma), hizmet Izleme Görüntüleyicisi aracını kullanarak bir hatanın kök nedenini daha hızlı bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a181d-118">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="a181d-119">Daha fazla bilgi için bkz. [bağıntılı izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="a181d-119">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="a181d-120">Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sunulan izlemeyi genişletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a181d-120">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="a181d-121">Kullanıcı tanımlı etkinlik izleme, kullanıcının şunları yapmak için izleme etkinlikleri oluşturmasına izin verir:</span><span class="sxs-lookup"><span data-stu-id="a181d-121">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="a181d-122">İzlemeleri mantıksal iş birimlerine göre gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="a181d-122">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="a181d-123">Aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="a181d-123">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="a181d-124">WCF izlemenin (örneğin, bir günlük dosyasının disk alanı maliyeti) performans maliyetini azaltır.</span><span class="sxs-lookup"><span data-stu-id="a181d-124">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="a181d-125">Kullanıcı tanımlı etkinlik izleme hakkında daha fazla bilgi için lütfen [genişletme izleme](extending-tracing.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="a181d-125">For more information about user-defined activity trace, please see the [Extending Tracing](extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="a181d-126">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a181d-126">Message Logging</span></span>  
 <span data-ttu-id="a181d-127">İleti günlüğe kaydetme her ikisi de herhangi bir WCF uygulamasının istemcisinde ve hizmetinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a181d-127">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="a181d-128">İleti günlüğe kaydetmeyi etkinleştirmek için, istemci veya hizmete aşağıdaki kodu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a181d-128">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="a181d-129">İleti kaydedildiğinde, izleme türü istemcide mi yoksa sunucuda mı izlenmekte olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a181d-129">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="a181d-130">Örneğin, bir istemciye gönderilen "Ekle" iletisi, istemcideki "TransportWrite" kategorisinin altında izleniyorsa, hizmette "TransportRead" kategorisinin altında aynı ileti de izlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a181d-130">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="a181d-131"><xref:System.Diagnostics>İstemci App.config dosyasının veya hizmetin Web.config dosyasının bölümüne aşağıdaki kodu ekleyerek izleme dinleyicisini yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="a181d-131">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="a181d-132">İletiler, yapılandırma dosyasında belirtilen hedef dizinde XML biçiminde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a181d-132">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a181d-133">İzleme dosyaları, başlangıçta günlük dizini oluşturulmadan oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="a181d-133">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="a181d-134">C:\logs\ dizininin var olduğundan emin olun veya dinleyici yapılandırmasında alternatif bir günlük dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a181d-134">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="a181d-135">Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a181d-135">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="a181d-136">İleti günlüğü hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../diagnostics/configuring-message-logging.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="a181d-136">For more information about message logging, see the [Configuring Message Logging](../diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a181d-137">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a181d-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a181d-138">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a181d-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a181d-139">Izleme ve Ileti günlüğü örneğini çalıştırmadan önce, hizmet için C:\logs\ dizinini oluşturarak. svclog dosyalarını öğesine yazın.</span><span class="sxs-lookup"><span data-stu-id="a181d-139">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="a181d-140">Bu dizinin adı yapılandırma dosyasında günlüğe kaydedilecek izlemeler ve iletilerin yolu olarak tanımlanır ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a181d-140">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="a181d-141">Kullanıcı ağ hizmetine Günlükler dizinine yazma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="a181d-141">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="a181d-142">Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a181d-142">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="a181d-143">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a181d-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a181d-144">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a181d-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a181d-145">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a181d-145">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a181d-146">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a181d-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a181d-147">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a181d-147">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="a181d-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a181d-148">See also</span></span>

- [<span data-ttu-id="a181d-149">İzleme</span><span class="sxs-lookup"><span data-stu-id="a181d-149">Tracing</span></span>](../diagnostics/tracing/index.md)
- <span data-ttu-id="a181d-150">[AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a181d-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

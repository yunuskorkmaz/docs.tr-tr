---
title: İleti İzleme ve Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143830"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="fc781-102">İleti İzleme ve Kaydetme</span><span class="sxs-lookup"><span data-stu-id="fc781-102">Tracing and Message Logging</span></span>
<span data-ttu-id="fc781-103">Bu örnek, izleme ve ileti günlüğe kaydetmeyi nasıl etkinleştireceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc781-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="fc781-104">Elde edilen izlemeler ve ileti günlükleri [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc781-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="fc781-105">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc781-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc781-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="fc781-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="fc781-107">İzleme</span><span class="sxs-lookup"><span data-stu-id="fc781-107">Tracing</span></span>  
 <span data-ttu-id="fc781-108">Windows Communication Foundation (WCF), ad alanında <xref:System.Diagnostics> tanımlanan izleme mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc781-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="fc781-109">Bu izleme modelinde, izleme verileri uygulamaların uyguladığı izleme kaynakları tarafından üretilir.</span><span class="sxs-lookup"><span data-stu-id="fc781-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="fc781-110">Her kaynak bir adla tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fc781-110">Each source is identified by a name.</span></span> <span data-ttu-id="fc781-111">İzleme tüketicileri, bilgi almak istedikleri izleme kaynakları için izleme dinleyicileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc781-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="fc781-112">İzleme verilerini almak için, izleme kaynağı için bir dinleyici oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc781-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="fc781-113">WCF'de bu işlem, Hizmet Modeli izleme kaynağını `switchValue`ayarlayarak hizmetin veya istemcinin yapılandırma dosyasına aşağıdaki kodu ekleyerek yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="fc781-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="fc781-114">İzleme kaynakları hakkında daha fazla bilgi için, [İzleme İzleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konusundaki İzleme Kaynağı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fc781-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="fc781-115">Aktivite Takibi ve Yayılması</span><span class="sxs-lookup"><span data-stu-id="fc781-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="fc781-116">Hem `ActivityTracing` istemci `propagateActivity` hem `true` de `system.ServiceModel` hizmet için izleme kaynaklarında etkinleştirilip ayarlanmış olması, mantıksal işleme birimleri (etkinlikler), uç noktalar içindeki etkinlikler (etkinlik aktarımları yoluyla) ve birden çok uç noktayı kapsayan etkinlikler arasında (etkinlik kimliği yayılımı yoluyla) izlemelerin korelasyonunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc781-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="fc781-117">Bu üç mekanizma (etkinlikler, aktarımlar ve yayılma) Service Trace Viewer aracını kullanarak bir hatanın temel nedenini daha hızlı bulmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc781-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="fc781-118">Daha fazla bilgi için, [İlişkili İzleri Görüntülemek ve Sorun Giderme için Hizmet İzleme Görüntüleyici'yi Kullanma'ya](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fc781-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="fc781-119">ServiceModel tarafından sağlanan izlemeyi, kullanıcı tanımlı etkinlik izlemeleri oluşturarak genişletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fc781-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="fc781-120">Kullanıcı tanımlı etkinlik izleme, kullanıcının aşağıdakilere yönelik izleme etkinlikleri oluşturmasına olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="fc781-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="fc781-121">Grup, mantıksal çalışma birimlerine izler.</span><span class="sxs-lookup"><span data-stu-id="fc781-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="fc781-122">Transferler ve yayılma yoluyla faaliyetleri ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="fc781-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="fc781-123">WCF izlemenin performans maliyetini (örneğin, günlük dosyasının disk alanı maliyeti) azledin.</span><span class="sxs-lookup"><span data-stu-id="fc781-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="fc781-124">Kullanıcı tanımlı etkinlik izleme hakkında daha fazla bilgi için lütfen [Genişletme İzleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="fc781-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="fc781-125">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="fc781-125">Message Logging</span></span>  
 <span data-ttu-id="fc781-126">İleti günlüğe kaydetme, herhangi bir WCF uygulamasının istemcisi ve hizmetinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fc781-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="fc781-127">İleti günlüğe kaydetmeyi etkinleştirmek için istemciye veya hizmete aşağıdaki kodu eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="fc781-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="fc781-128">İleti kaydedildiğinde, izleme türü istemcide mi yoksa sunucuda mı izlendigine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fc781-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="fc781-129">Örneğin, istemciye gönderilen bir "Ekle" iletisi istemcideki "TransportWrite" kategorisi altında izlenirken, aynı ileti hizmetteki "TransportRead" kategorisi altında izlenir.</span><span class="sxs-lookup"><span data-stu-id="fc781-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="fc781-130">İz dinleyicisini, istemcinin App.config <xref:System.Diagnostics> dosyasının veya hizmetin Web.config dosyasının bölümüne aşağıdaki kodu ekleyerek yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="fc781-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="fc781-131">İletiler yapılandırma dosyasında belirtilen hedef dizinde XML biçiminde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fc781-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc781-132">İzleme dosyaları başlangıçta günlük dizini oluşturmadan oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="fc781-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="fc781-133">C:\logs\ dizininin var olduğundan emin olun veya dinleyici yapılandırmasında alternatif bir günlük dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc781-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="fc781-134">Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="fc781-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="fc781-135">İleti günlüğe kaydetme hakkında daha fazla bilgi için, [İleti Günlüğe Kaydetme](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="fc781-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc781-136">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fc781-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fc781-137">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc781-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fc781-138">İzleme ve İleti Günlüğü örneğini çalıştırmadan önce, .svclog dosyalarını yazmak için hizmetin C:\logs\ dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc781-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="fc781-139">Bu dizinin adı yapılandırma dosyasında, günlüğe kaydedilecek ve değiştirilebilen izlemeler ve iletiler için yol olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fc781-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="fc781-140">Kullanıcı Ağ Hizmeti günlükleri dizinine erişim yazın.</span><span class="sxs-lookup"><span data-stu-id="fc781-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="fc781-141">Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc781-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="fc781-142">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc781-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc781-143">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc781-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fc781-144">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fc781-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fc781-145">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="fc781-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc781-146">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc781-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="fc781-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc781-147">See also</span></span>

- [<span data-ttu-id="fc781-148">İzleme</span><span class="sxs-lookup"><span data-stu-id="fc781-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- <span data-ttu-id="fc781-149">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fc781-149">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

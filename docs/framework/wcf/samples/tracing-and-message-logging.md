---
title: İleti İzleme ve Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 448eef6ea147b725600b774026155acc1fca6d36
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094871"
---
# <a name="tracing-and-message-logging"></a>İleti İzleme ve Kaydetme
Bu örnek, izleme ve ileti günlüğe kaydetmenin nasıl etkinleştirileceğini gösterir. Ortaya çıkan izlemeler ve ileti günlükleri, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenir. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="tracing"></a>İzleme  
 Windows Communication Foundation (WCF), <xref:System.Diagnostics> ad alanında tanımlanan izleme mekanizmasını kullanır. Bu izleme modelinde, izleme verileri uygulamaların uygulayan izleme kaynakları tarafından üretilir. Her kaynak bir ad ile tanımlanır. İzleme tüketicileri, bilgi almak istedikleri izleme kaynakları için izleme dinleyicileri oluşturur. İzleme verileri almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir. WCF 'de, bu, hizmet modeli izleme kaynağı `switchValue`ayarlanarak hizmetin veya istemcinin yapılandırma dosyasına aşağıdaki kodu ekleyerek yapılabilir:  
  
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
  
 İzleme kaynakları hakkında daha fazla bilgi için [Izlemeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konusunun Kaynak izleme bölümüne bakın.  
  
## <a name="activity-tracing-and-propagation"></a>Etkinlik Izleme ve yayma  
 `ActivityTracing` etkinleştirilmiş ve `propagateActivity`, hem istemci hem de hizmet için `system.ServiceModel` izleme kaynaklarında `true` olarak ayarlanmış olması, mantıksal işlem (etkinlik) birimlerindeki izlemelerin (etkinlik aktarımları aracılığıyla) ve birden çok uç noktayı kapsayan etkinliklerin (etkinlik KIMLIĞI yayması aracılığıyla) arasında bağıntı sağlamasına olanak sağlar.  
  
 Bu üç mekanizma (Etkinlikler, aktarımlar ve yayma), hizmet Izleme Görüntüleyicisi aracını kullanarak bir hatanın kök nedenini daha hızlı bulmanıza yardımcı olabilir. Daha fazla bilgi için bkz. [bağıntılı izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sunulan izlemeyi genişletmek mümkündür. Kullanıcı tanımlı etkinlik izleme, kullanıcının şunları yapmak için izleme etkinlikleri oluşturmasına izin verir:  
  
- İzlemeleri mantıksal iş birimlerine göre gruplandırın.  
  
- Aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirme.  
  
- WCF izlemenin (örneğin, bir günlük dosyasının disk alanı maliyeti) performans maliyetini azaltır.  
  
 Kullanıcı tanımlı etkinlik izleme hakkında daha fazla bilgi için lütfen [genişletme izleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örneğine bakın.  
  
## <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 İleti günlüğe kaydetme her ikisi de herhangi bir WCF uygulamasının istemcisinde ve hizmetinde etkinleştirilebilir. İleti günlüğe kaydetmeyi etkinleştirmek için, istemci veya hizmete aşağıdaki kodu eklemeniz gerekir:  
  
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
  
 İleti kaydedildiğinde, izleme türü istemcide mi yoksa sunucuda mı izlenmekte olduğuna bağlıdır. Örneğin, bir istemciye gönderilen "Ekle" iletisi, istemcideki "TransportWrite" kategorisinin altında izleniyorsa, hizmette "TransportRead" kategorisinin altında aynı ileti de izlenmektedir.  
  
 Aşağıdaki kodu istemcinin App. config dosyasının <xref:System.Diagnostics> bölümüne veya hizmetin Web. config dosyasına ekleyerek izleme dinleyicisini yapılandırın:  
  
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
  
 İletiler, yapılandırma dosyasında belirtilen hedef dizinde XML biçiminde günlüğe kaydedilir.  
  
> [!NOTE]
> İzleme dosyaları, başlangıçta günlük dizini oluşturulmadan oluşturulmaz. C:\logs\ dizininin var olduğundan emin olun veya dinleyici yapılandırmasında alternatif bir günlük dizini belirtin. Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.  
  
 İleti günlüğü hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konusuna bakın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Izleme ve Ileti günlüğü örneğini çalıştırmadan önce, hizmet için C:\logs\ dizinini oluşturarak. svclog dosyalarını öğesine yazın. Bu dizinin adı yapılandırma dosyasında günlüğe kaydedilecek izlemeler ve iletilerin yolu olarak tanımlanır ve değiştirilebilir. Kullanıcı ağ hizmetine Günlükler dizinine yazma erişimi verin.  
  
3. Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

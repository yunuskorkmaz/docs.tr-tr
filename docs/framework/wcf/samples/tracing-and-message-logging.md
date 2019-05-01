---
title: İleti İzleme ve Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 079decb76b45566f354418d671145f0c284628c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007740"
---
# <a name="tracing-and-message-logging"></a>İleti İzleme ve Kaydetme
Bu örnek, izleme ve ileti günlüğe kaydetmeyi etkinleştirme gösterir. Sonuçta elde edilen izleme ve ileti günlüklerini kullanarak görüntülenen [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="tracing"></a>İzleme  
 Windows Communication Foundation (WCF) kullanan tanımlanan izleme mekanizması <xref:System.Diagnostics> ad alanı. Bu izleme modelinde, izleme verilerini, uygulamalarını uygulamak iz kaynakları tarafından oluşturulur. Her kaynak bir ad tarafından tanımlanır. İzleme Tüketiciler, bilgi almak istediğiniz izleme kaynakları için izleme dinleyicilerine oluşturun. İzleme verilerini almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir. WCF'de, bu hizmet modeli iz ayarlayarak hizmet veya istemcinin yapılandırma dosyasına aşağıdaki kodu ekleyerek yapılabilir `switchValue`:  
  
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
  
 İzleme kaynağı bölümünde izleme kaynakları hakkında daha fazla bilgi için bkz. [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konu.  
  
## <a name="activity-tracing-and-propagation"></a>Etkinlik izleme ve yayma  
 Sahip `ActivityTracing` etkin ve `propagateActivity` kümesine `true` içinde `system.ServiceModel` izleme kaynakları için hem istemci hem de hizmet uç noktaları (içindeki etkinlikleri arasında mantıksal birimler (etkinlik) işlem içinde izlemeleri bağıntısı sağlayın Etkinlik aktarımları için) üzerinden ve birden fazla uç noktası (aracılığıyla, etkinlik kimliği yayma) kapsayan etkinlikler arasında.  
  
 Bu üç mekanizmalar (etkinlikler, aktarımı ve yayma) daha hızlı bir şekilde hizmet izleme görüntüleyicisini aracını kullanarak bir hata kök nedenini bulmanıza yardımcı olabilir. Daha fazla bilgi için [ilişkilendirilmiş izlemeleri görüntülemek ve sorun giderme için hizmet izleme görüntüleyicisini kullanarak](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sağlanan izleme genişletmek mümkündür. Kullanıcı tanımlı Etkinlik izleme için izleme etkinliklerin oluşturmasına olanak tanır:  
  
- Grup izlemeleri içine mantıksal iş birimleri.  
  
- Etkinlikleri aktarımları ve yayma ile ilişkilendirin.  
  
- WCF izleme (örneğin, bir günlük dosyası disk alanı maliyeti) performans maliyeti azalır.  
  
 Kullanıcı tanımlı Etkinlik izleme hakkında daha fazla bilgi için lütfen bkz [genişletme izleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örnek.  
  
## <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 Hem istemci hem de hizmet herhangi bir WCF uygulaması, ileti günlüğe kaydetme etkinleştirilebilir. İleti günlüğü etkinleştirmek için istemci veya hizmet için aşağıdaki kodu eklemeniz gerekir:  
  
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
  
 Bir ileti kaydedildiği olup, istemci veya sunucu izlenen üzerinde izleme türüne bağlıdır. Örneğin, aynı iletiyi hizmetine "TransportRead" kategorisi altında izlenen ise istemcide "TransportWrite" kategorisi altındaki bir istemciye gönderilen ileti bir "Ekle" izleneceğini.  
  
 Aşağıdaki kodu ekleyerek İzleme dinleyicisi yapılandırma <xref:System.Diagnostics> istemcinin App.config dosyasının veya hizmetin Web.config dosyasının bölümü:  
  
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
  
 Yapılandırma dosyasında belirtilen hedef dizin XML biçiminde iletileri günlüğe kaydedilir.  
  
> [!NOTE]
>  İzleme dosyaları, başlangıçta günlük dizini oluşturmadan oluşturulmaz. Dinleyici Yapılandırması'nda bir alternatif günlük dizinini belirtin veya C:\logs\ dizinin var olduğundan emin olun. Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.  
  
 Günlüğe ileti kaydetme hakkında daha fazla bilgi için bkz: [iletileri günlüğe kaydetmeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. İzleme ve ileti günlüğe kaydetme örneği çalıştırmadan önce .svclog dosyalara yazmak için C:\logs\ hizmeti için dizin oluşturun. Bu dizinin adını, izleme ve günlüğe kaydedilecek ileti için yol olarak yapılandırma dosyasında tanımlanır ve değiştirilebilir. Ağ hizmeti yazma erişimi kullanıcı logs dizininde verin.  
  
3. Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)

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
# <a name="tracing-and-message-logging"></a>İleti İzleme ve Kaydetme
Bu örnek, izleme ve ileti günlüğe kaydetmeyi nasıl etkinleştireceklerini gösterir. Elde edilen izlemeler ve ileti günlükleri [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="tracing"></a>İzleme  
 Windows Communication Foundation (WCF), ad alanında <xref:System.Diagnostics> tanımlanan izleme mekanizmasını kullanır. Bu izleme modelinde, izleme verileri uygulamaların uyguladığı izleme kaynakları tarafından üretilir. Her kaynak bir adla tanımlanır. İzleme tüketicileri, bilgi almak istedikleri izleme kaynakları için izleme dinleyicileri oluşturur. İzleme verilerini almak için, izleme kaynağı için bir dinleyici oluşturmanız gerekir. WCF'de bu işlem, Hizmet Modeli izleme kaynağını `switchValue`ayarlayarak hizmetin veya istemcinin yapılandırma dosyasına aşağıdaki kodu ekleyerek yapılabilir:  
  
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
  
 İzleme kaynakları hakkında daha fazla bilgi için, [İzleme İzleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konusundaki İzleme Kaynağı bölümüne bakın.  
  
## <a name="activity-tracing-and-propagation"></a>Aktivite Takibi ve Yayılması  
 Hem `ActivityTracing` istemci `propagateActivity` hem `true` de `system.ServiceModel` hizmet için izleme kaynaklarında etkinleştirilip ayarlanmış olması, mantıksal işleme birimleri (etkinlikler), uç noktalar içindeki etkinlikler (etkinlik aktarımları yoluyla) ve birden çok uç noktayı kapsayan etkinlikler arasında (etkinlik kimliği yayılımı yoluyla) izlemelerin korelasyonunu sağlar.  
  
 Bu üç mekanizma (etkinlikler, aktarımlar ve yayılma) Service Trace Viewer aracını kullanarak bir hatanın temel nedenini daha hızlı bulmanıza yardımcı olabilir. Daha fazla bilgi için, [İlişkili İzleri Görüntülemek ve Sorun Giderme için Hizmet İzleme Görüntüleyici'yi Kullanma'ya](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)bakın.  
  
 ServiceModel tarafından sağlanan izlemeyi, kullanıcı tanımlı etkinlik izlemeleri oluşturarak genişletmek mümkündür. Kullanıcı tanımlı etkinlik izleme, kullanıcının aşağıdakilere yönelik izleme etkinlikleri oluşturmasına olanak tanır:  
  
- Grup, mantıksal çalışma birimlerine izler.  
  
- Transferler ve yayılma yoluyla faaliyetleri ilişkilendirin.  
  
- WCF izlemenin performans maliyetini (örneğin, günlük dosyasının disk alanı maliyeti) azledin.  
  
 Kullanıcı tanımlı etkinlik izleme hakkında daha fazla bilgi için lütfen [Genişletme İzleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örneğine bakın.  
  
## <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 İleti günlüğe kaydetme, herhangi bir WCF uygulamasının istemcisi ve hizmetinde etkinleştirilebilir. İleti günlüğe kaydetmeyi etkinleştirmek için istemciye veya hizmete aşağıdaki kodu eklemeniz gerekir:  
  
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
  
 İleti kaydedildiğinde, izleme türü istemcide mi yoksa sunucuda mı izlendigine bağlıdır. Örneğin, istemciye gönderilen bir "Ekle" iletisi istemcideki "TransportWrite" kategorisi altında izlenirken, aynı ileti hizmetteki "TransportRead" kategorisi altında izlenir.  
  
 İz dinleyicisini, istemcinin App.config <xref:System.Diagnostics> dosyasının veya hizmetin Web.config dosyasının bölümüne aşağıdaki kodu ekleyerek yapılandırın:  
  
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
  
 İletiler yapılandırma dosyasında belirtilen hedef dizinde XML biçiminde günlüğe kaydedilir.  
  
> [!NOTE]
> İzleme dosyaları başlangıçta günlük dizini oluşturmadan oluşturulmaz. C:\logs\ dizininin var olduğundan emin olun veya dinleyici yapılandırmasında alternatif bir günlük dizini belirtin. Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.  
  
 İleti günlüğe kaydetme hakkında daha fazla bilgi için, [İleti Günlüğe Kaydetme](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konusuna bakın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. İzleme ve İleti Günlüğü örneğini çalıştırmadan önce, .svclog dosyalarını yazmak için hizmetin C:\logs\ dizinini oluşturun. Bu dizinin adı yapılandırma dosyasında, günlüğe kaydedilecek ve değiştirilebilen izlemeler ve iletiler için yol olarak tanımlanır. Kullanıcı Ağ Hizmeti günlükleri dizinine erişim yazın.  
  
3. Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

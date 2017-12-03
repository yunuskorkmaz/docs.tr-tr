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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d37e050933f0f94a74fcabe3afe007ad2333d58a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tracing-and-message-logging"></a>İleti İzleme ve Kaydetme
Bu örnek, ileti izleme ve kaydetme etkinleştirmek gösterilmiştir. Sonuçta elde edilen izlemeleri ve ileti günlüklerini kullanarak görüntülenen [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="tracing"></a>İzleme  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]tanımlanan izleme mekanizması kullanır <xref:System.Diagnostics> ad alanı. Bu izleme modelde izleme verilerini uygulamalarını uygulamak izleme kaynaklar tarafından oluşturulur. Her kaynak adına göre tanımlanır. İzleme dinleyicileri bilgilerini almak istediği izleme kaynakları için izleme tüketicileri oluşturun. İzleme verilerini almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu iki hizmetin için aşağıdaki kodu ekleyerek yapılabilir veya istemcinin yapılandırma dosyası hizmet modeli izleme kaynağı ayarlayarak `switchValue`:  
  
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
  
 İzleme kaynakları hakkında daha fazla bilgi için bkz: izleme kaynağı bölümünde [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konu.  
  
## <a name="activity-tracing-and-propagation"></a>Etkinlik izleme ve yayma  
 Sahip `ActivityTracing` etkin ve `propagateActivity` kümesine `true` içinde `system.ServiceModel` izleme kaynakları hem istemci hem de hizmet uç noktaları ('nda etkinlikler arasında bağıntı (aktiviteler) işleme mantıksal birimler içinde izlemeleri sağlayın Etkinlik aktarımları için) üzerinden ve birden fazla uç noktası (aracılığıyla, etkinlik kimliği yayma) kapsayıcı etkinlikler arasında.  
  
 Bu üç mekanizma (etkinlikleri, aktarımları ve yayma) daha hızlı bir şekilde hizmet izleme görüntüleyicisini aracını kullanarak bir hatasının kök nedenini bulmanıza yardımcı olabilir. Daha fazla bilgi için bkz: [bağıntılı izlemeleri görüntüleme ve sorun giderme için hizmet izleme görüntüleyicisini kullanma](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sağlanan izleme genişletmek mümkündür. Kullanıcı tanımlı Etkinlik izleme için izleme etkinliklerini oluşturmasına olanak tanır:  
  
-   Grup izlemeleri iş mantıksal birimler halinde.  
  
-   Etkinlikler aktarımları ve yayma ile ilişkilendirilmesi.  
  
-   Performans maliyetini azaltmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izleme (örneğin, disk alanı maliyeti bir günlük dosyası).  
  
 Kullanıcı tanımlı Etkinlik izleme hakkında daha fazla bilgi için lütfen bkz [genişletme izleme](../../../../docs/framework/wcf/samples/extending-tracing.md) örnek.  
  
## <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 İleti günlüğe kaydetme etkinleştirilebilir, hem istemci hem de hizmet herhangi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama. İleti günlüğe kaydetme etkinleştirmek için istemci veya hizmet için aşağıdaki kodu eklemeniz gerekir:  
  
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
  
 Bir ileti kaydedildiğinde, izleme türü olup olmadığını, istemci veya sunucu izlenen üzerinde bağlıdır. Örneğin, aynı ileti konuşması "TransportRead" kategorisi altında izlenen ise istemcide "TransportWrite" kategorisi altında bir istemciye gönderilen bir "Ekle" iletisi izleneceğini.  
  
 Aşağıdaki kodu ekleyerek İzleme dinleyicisi yapılandırma <xref:System.Diagnostics> istemcinin App.config dosyası veya hizmetin Web.config dosyası bölümünü:  
  
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
  
 İletileri yapılandırma dosyasında belirtilen hedef dizinin XML biçiminde günlüğe kaydedilir.  
  
> [!NOTE]
>  İzleme dosyaları başlangıçta günlük dizinini oluşturmadan oluşturulmaz. Dinleyici Yapılandırması'nda bir alternatif günlük dizinini belirtin veya C:\logs\ dizinin var olduğundan emin olun. Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.  
  
 İleti günlüğe kaydetme hakkında daha fazla bilgi için bkz: [yapılandırma ileti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) konu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  İzleme ve ileti günlüğe kaydetme örneği çalıştırmadan önce .svclog dosyaları yazmak için C:\logs\ hizmeti için dizin oluşturun. Bu dizinin adı yapılandırma dosyasında izlemeleri ve günlüğe kaydedilecek iletileri için yol olarak tanımlanır ve değiştirilebilir. Günlükleri dizinine kullanıcı ağ hizmeti yazma erişimi verin.  
  
3.  C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)

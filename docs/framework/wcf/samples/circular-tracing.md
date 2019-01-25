---
title: Döngüsel İzleme
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: eaecf2205e7618f02a66f8c35fc88ca5a59947b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646441"
---
# <a name="circular-tracing"></a>Döngüsel İzleme
Bu örnek, bir döngüsel arabellek İzleme dinleyicisi uygulamasını gösterir. Sık karşılaşılan bir senaryodur üretim Hizmetleri için uzun süreler için kullanılabilen hizmetler ve izleme günlüğü düşük bir düzeyde etkin ' dir. Bu hizmetler, çok fazla disk alanı kullanır. Bir hizmet sorunlarını giderirken, izleme günlüğü en son verileri sorununuzu çözmek için geçerlidir. Bu örnek yalnızca en son izlemeleri, yapılandırılabilir bir veri miktarına kadar diskte tutulur bir döngüsel arabellek İzleme dinleyicisi uygulanışı gösterilmektedir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve özel İzleme dinleyicisi içerir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek, aşina olduğunuzu varsayar [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek ve okuma için sağlanan belgeleri [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.  
  
## <a name="circular-buffer-trace-listener"></a>Döngüsel arabellek İzleme dinleyicisi  
 Döngüsel arabellek İzleme dinleyicisi uygulamasının arkasında kavramı her kadar ikiye toplam istenen izleme günlük verilerini depolayabilir iki dosya sağlamaktır. Dinleyici bir dosya oluşturur ve isteğe bağlı olarak, bu noktada ikinci bir dosyaya geçer veri boyutu, ilk yarısında, sınıra ulaşana kadar bu dosyaya yazar. Dinleyici ikinci dosya - sınırına ulaştığında yeni izlemeleri ilk dosyanın üzerine yazar.  
  
 Bu dinleyici türetildiği `XmlWriteTraceListener` ve günlükleri ile görüntülenmesine izin verir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Günlükleri görüntülemek çalışırken, iki günlük dosyaları kolayca günlük dosyalarının her ikisi de aynı anda hizmet izleme Görüntüleyicisi Aracı'nda açarak tasarlanabilen. Hizmet izleme Görüntüleyicisi aracı otomatik olarak doğru sırayla görünecekleri izlemeleri sıralama üstlenir.  
  
## <a name="configuration"></a>Yapılandırma  
 Bir hizmeti bir dinleyici ve kaynak öğeleri için aşağıdaki kodu ekleyerek döngüsel arabellek İzleme dinleyicisi kullanmak için yapılandırılabilir. En fazla dosya boyutunu ayarlayarak belirtilen `maxFileSizeKB` özniteliği döngüsel izleme dinleyicinin yapılandırması. Bu, aşağıdaki kodda gösterilmiştir.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)

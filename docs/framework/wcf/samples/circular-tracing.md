---
title: "Döngüsel İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b86867793424d6d0b42a18d6a2fbd6175bc1a47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="circular-tracing"></a>Döngüsel İzleme
Bu örnek uygulama döngüsel arabellek İzleme dinleyicisi ortaya koyar. Üretim Hizmetleri için yaygın bir senaryo Hizmetleri, uzun bir süre için kullanılabilir olmasını ve izleme günlüğü düşük bir düzeyde etkin değil. Bu hizmetler çok disk alanı kullanabilir. Bir hizmet sorunlarını giderirken, izleme günlüğü en son verileri bir sorunu çözmek için geçerlidir. Bu örnek yalnızca en son izlemeleri içinde yapılandırılabilir miktarda veri kadar diskte tutulur döngüsel arabellek İzleme dinleyicisi uygulaması gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve özel İzleme dinleyicisi içerir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek aşina olduğunuzu varsayar [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek ve için sağlanan belgeleri okuduğunuzu [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.  
  
## <a name="circular-buffer-trace-listener"></a>Döngüsel arabellek İzleme dinleyicisi  
 Döngüsel arabellek İzleme dinleyicisi uyarlamasını arkasında kavramı her kadar yarısı toplam istenen izleme günlük verilerini depolayabilir iki dosya olmalıdır. Dinleyici bir dosya oluşturur ve isteğe bağlı olarak, bu noktada ikinci bir dosyaya geçer veri boyutu yarısı sınırını ulaşana kadar bu dosyaya yazar. Dinleyici ikinci dosya - sınırına ulaştığında ile yeni izlemeler ilk dosyasının üzerine yazar.  
  
 Bu dinleyici türetilen `XmlWriteTraceListener` ve günlükleri ile görüntülenmesine izin verir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Günlükleri görüntülemek çalışırken, iki günlük dosyaları kolayca hizmet izleme Görüntüleyicisi aracı aynı anda hem de günlük dosyaları açarak tasarlanabilen. Hizmet izleme Görüntüleyicisi aracı otomatik olarak doğru sırada görünecekleri izlemeleri sıralama mvc'deki.  
  
## <a name="configuration"></a>Yapılandırma  
 Bir hizmet dinleyici ve kaynak öğeler için aşağıdaki kodu ekleyerek döngüsel arabellek İzleme dinleyicisi kullanacak şekilde yapılandırılabilir. Ayarlayarak belirtilen en büyük dosya boyutu `maxFileSizeKB` özniteliği döngüsel İzleme dinleyicisi'nın yapılandırması. Bu aşağıdaki kodda gösterilmiştir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)

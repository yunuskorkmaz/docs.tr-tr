---
title: Döngüsel İzleme
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1759db28cb024afc04d02c4b128f96d73aefdd87
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585447"
---
# <a name="circular-tracing"></a>Döngüsel İzleme

Bu örnek, döngüsel arabellek İzleme dinleyicisinin uygulanmasını gösterir. Üretim Hizmetleri için yaygın bir senaryo, uzun süreler için kullanılabilir olan ve düşük düzeyde izleme günlüğü etkin olan hizmetlerden oluşur. Bu hizmetler çok fazla disk alanı tüketir. Bir hizmette sorun giderirken, izleme günlüğündeki en son veriler bir sorunu çözmeye uygun olur. Bu örnek, yalnızca en son izlemelerin yapılandırılabilir bir veri miktarına kadar diskte tutulduğu döngüsel bir arabellek İzleme dinleyicisi uygulamasını gösterir. Bu örnek [Başlarken](getting-started-sample.md) ' i temel alır ve özel bir izleme dinleyicisi içerir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, [izleme ve Ileti günlüğe kaydetme](tracing-and-message-logging.md) örneği hakkında bilgi sahibi olduğunuzu ve [Izleme ve mesaj günlüğü](tracing-and-message-logging.md) örneği için sunulan belgeleri okuduğunuzu varsayar.

## <a name="circular-buffer-trace-listener"></a>Döngüsel arabellek Izleme dinleyicisi

Döngüsel arabellek Izleme dinleyicisi uygulamasının arkasındaki kavram, her bir depolama alanı için istenen toplam izleme günlüğü verilerinin yarısını oluşturan iki dosya vardır. Dinleyici bir dosya oluşturur ve veri boyutunun yarısını alıncaya kadar bu dosyaya yazar; bu noktada ikinci bir dosyaya geçiş yapar. Dinleyici ikinci dosya için sınıra ulaştığında, ilk dosyanın üzerine yeni izlemelerle yazar.

Bu dinleyici öğesinden türetilir `XmlWriteTraceListener` ve günlüklerin [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)ile görüntülenmesine izin verir. Günlükleri görüntülemeye çalışırken, iki günlük dosyası her iki günlük dosyası da hizmet Izleme Görüntüleyicisi aracında aynı anda açılarak kolayca yeniden birleştirilebilir. Hizmet Izleme Görüntüleyicisi Aracı, izlemeleri doğru sırada görünecek şekilde sıralamayı otomatik olarak gerçekleştirir.

## <a name="configuration"></a>Yapılandırma

Bir hizmet, bir dinleyici ve kaynak öğeleri için aşağıdaki kodu ekleyerek döngüsel arabellek Izleme dinleyicisini kullanacak şekilde yapılandırılabilir. En büyük dosya boyutu, `maxFileSizeKB` Döngüsel İzleme dinleyicisi yapılandırmasındaki özniteliği ayarlanarak belirtilir. Bu, aşağıdaki kodda gösterilmiştir.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: c56f886857e8d391a243e3af4a13353f14116247
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329719"
---
# <a name="extending-tracing"></a>İzlemeyi Genişletme
Bu örnek, kullanıcı tanımlı etkinlik izlemeleri istemci ve hizmet kodu yazarak Windows Communication Foundation (WCF) izleme özelliğini genişletme gösterir. Bu izleme etkinliklerin oluşturup izlemeleri çalışmanın mantıksal birimler halinde gruplandırmak kullanıcı sağlar. Aktarımları (içinde aynı uç noktası) ile etkinlikleri ve yayma (uç noktalar genelinde) ilişkilendirmek mümkündür. Bu örnekte, hem istemci hem de hizmet için izlemeyi etkinleştirilir. İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>İzleme ve Etkinlik yayma  
 Kullanıcı kendi iş mantıksal birimler Grup izlemeleri için izleme etkinliklerine oluşturma, etkinlikleri aktarımları ve yayma ile ilişkilendirin ve WCF izleme (örneğin, maliyet disk alanı performans maliyetini azaltmak kullanıcı tanımlı Etkinlik izleme sağlar bir günlük dosyası).  
  
### <a name="adding-custom-sources"></a>Özel kaynaklar ekleme  
 Kullanıcı tanımlı izlemeler, hizmet ve istemci kodu eklenebilir. Kaydedilir ve görüntülenen bu özel izlemeleri için izleme kaynakları istemci veya hizmet yapılandırma dosyalarına izin ekleme [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Aşağıdaki kod, adlı bir kullanıcı tanımlı izleme kaynağına ekleme işlemi açıklanır `ServerCalculatorTraceSource` yapılandırma dosyası.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Etkinlikleri ilişkilendirme  
 Doğrudan uç arasında etkinliklerini ilişkilendirmek için `propagateActivity` özniteliği ayarlanmalıdır `true` içinde `System.ServiceModel` izleme kaynağı. Ayrıca, WCF etkinliklerini olmadan izlemeleri yaymak için etkinlik ServiceModel izleme kapatılmalıdır. Bu aşağıdaki kod örneğinde görülebilir.  
  
> [!NOTE]
>  ServiceModel etkinliği izleme devre dışı kapatma değil çağrılarınızla izleme düzeyini sahip aynı `switchValue` Kapalı'özelliğini ayarlayın.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Lessening performans maliyeti  
 Ayarı `ActivityTracing` de kapalı olarak `System.ServiceModel` izleme kaynağı dahil ServiceModel Etkinlik izleme olmadan yalnızca kullanıcı tarafından tanımlanan etkinlik izlemeleri içeren bir izleme dosyası oluşturur. Bu, çok daha küçük boyutu bir günlük dosyasında sonuçlanır. Ancak, izlemeleri işleme WCF ilişkilendirmek için bir fırsat kaybolur.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)

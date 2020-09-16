---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: f2b9deb346077609193ec08c2c01b10a3ad9357b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556518"
---
# <a name="extend-tracing"></a>İzlemeyi Genişlet

Bu örnek, istemci ve hizmet kodunda Kullanıcı tanımlı etkinlik izlemeleri yazarak Windows Communication Foundation (WCF) izleme özelliğinin nasıl genişletileceğini gösterir. Kullanıcı tanımlı etkinlik izlemelerinin yazılması, kullanıcının mantıksal iş birimlerine izleme etkinlikleri ve grup izlemeleri oluşturmasına izin verir. Ayrıca, etkinlikleri aktarımlar (aynı uç nokta içinde) ve yayma (uç noktalar arasında) ile ilişkilendirmek mümkündür. Bu örnekte, izleme hem istemci hem de hizmet için etkinleştirilmiştir. İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [izleme ve mesaj günlüğü](tracing-and-message-logging.md).  
  
 Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>İzleme ve etkinlik yayma  
 Kullanıcı tanımlı etkinlik izleme, kullanıcının izlemeleri mantıksal iş birimlerine göre gruplamak, aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirmek ve WCF izlemenin (örneğin, bir günlük dosyasının disk alanı maliyeti) performans maliyetini azaltmak için kendi izleme etkinliklerini oluşturmalarına olanak tanır.  
  
### <a name="add-custom-sources"></a>Özel Kaynak Ekle  
 Kullanıcı tanımlı izlemeler, hem istemci hem de hizmet koduna eklenebilir. İstemci veya hizmet yapılandırma dosyalarına izleme kaynakları eklemek, bu özel izlemelerin [Service Trace Viewer aracında (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kaydedilip görüntülenmesini sağlar. Aşağıdaki kod, yapılandırma dosyasına adlı Kullanıcı tanımlı izleme kaynağının nasıl ekleneceğini gösterir `ServerCalculatorTraceSource` .  
  
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
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a>Etkinlikleri ilişkilendirme  
 Etkinlikleri doğrudan uç noktalar arasında ilişkilendirmek için, `propagateActivity` özniteliği izleme kaynağında olarak ayarlanmalıdır `true` `System.ServiceModel` . Ayrıca, WCF etkinliklerinde ilerlemeden izlemeleri yaymak için, ServiceModel etkinliği Izlemenin kapalı olması gerekir. Bu, aşağıdaki kod örneğinde görülebilir.  
  
> [!NOTE]
> ServiceModel etkinlik Izlemenin kapatılması, özelliği tarafından belirtilen izleme düzeyiyle aynı değildir ve `switchValue` kapalı olarak ayarlanır.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a>Performans maliyetini azaltır  
 `ActivityTracing` `System.ServiceModel` İzleme kaynağında kapalı ayarı, yalnızca Kullanıcı tanımlı etkinlik izlemelerini içeren bir izleme dosyası oluşturur ve bu da hiçbir ServiceModel etkinlik izlemeden dahil değildir. ServiceModel etkinliğinin dışlanması, daha küçük bir günlük dosyasına neden olur. Ancak, WCF işleme izlemelerinin ilişkilendirilmesi için fırsat kaybolur.  
  
## <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))

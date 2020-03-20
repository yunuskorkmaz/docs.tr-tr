---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183684"
---
# <a name="extending-tracing"></a>İzlemeyi Genişletme
Bu örnek, istemci ve hizmet koduna kullanıcı tanımlı etkinlik izlemeleri yazarak Windows Communication Foundation (WCF) izleme özelliğinin nasıl genişletilebildiğini göstermektedir. Bu, kullanıcının izleme etkinlikleri oluşturmasına ve izlemeleri mantıksal çalışma birimlerine gruplandırmasına olanak tanır. Faaliyetleri aktarımlar (aynı uç nokta içinde) ve yayılma (uç noktalar arasında) yoluyla ilişkilendirmek de mümkündür. Bu örnekte, izleme hem istemci hem de hizmet için etkinleştirilir. İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirilen hakkında daha fazla bilgi için [Bkz.](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)  
  
 Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>İzleme ve Aktivite Yayılımı  
 Kullanıcı tanımlı etkinlik izleme, kullanıcının izlemeleri mantıksal çalışma birimlerine gruplandırmak, aktarımlar ve yayılma yoluyla etkinlikleri ilişkilendirmek ve WCF izlemenin performans maliyetini (örneğin, disk alanı maliyeti) azaltması için kendi izleme etkinliklerini oluşturmasına olanak tanır bir günlük dosyasının).  
  
### <a name="adding-custom-sources"></a>Özel Kaynak Ekleme  
 Kullanıcı tanımlı izlemeler hem istemci hem de hizmet koduna eklenebilir. İstemci veya hizmet yapılandırma dosyalarına izleme kaynakları eklemek, bu özel izlemelerin [Service Trace Viewer Tool 'da (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kaydedilmesine ve görüntülenmesine olanak sağlar. Aşağıdaki kod, yapılandırma dosyasına kullanıcı `ServerCalculatorTraceSource` tanımlı bir izleme kaynağının nasıl ekleyeceğini gösterir.  
  
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
  
### <a name="correlating-activities"></a>Korelasyon Faaliyetleri  
 Etkinlikleri doğrudan uç noktalar arasında `propagateActivity` ilişkilendirmek için `true` öznitelik `System.ServiceModel` izleme kaynağına ayarlanmalıdır. Ayrıca, WCF etkinliklerinden geçmeden izlemeleri yaymak için ServiceModel Etkinlik İzleme solunmalıdır. Bu, aşağıdaki kod örneğinde görülebilir.  
  
> [!NOTE]
> ServiceModel Etkinlik İzleme'yi kapatmak, özellik tarafından gösterilen izleme düzeyine `switchValue` sahip olmakla aynı şey değildir.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Performans Maliyetini Azaltma  
 İzleme kaynağında kapalı `ActivityTracing` ayar, ServiceModel etkinlik izlerinin hiçbiri dahil edilmeden yalnızca kullanıcı tanımlı etkinlik izlemelerini içeren bir izleme dosyası oluşturur. `System.ServiceModel` Bu çok daha küçük boyutlu bir günlük dosyası ile sonuçlanır. Ancak, WCF işleme izlerini ilişkilendirme fırsatı kaybolur.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

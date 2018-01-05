---
title: "İzlemeyi Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c92aa17f25271173ca0bcbad1a8a180c9129abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-tracing"></a>İzlemeyi Genişletme
Bu örnek nasıl genişletileceğini gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanıcı tanımlı etkinlik izlemeleri istemci ve hizmet kodu yazarak izleme özelliği. Bu izleme etkinlikleri oluşturmak ve izlemeleri iş mantıksal birimler halinde gruplandırmak kullanıcının sağlar. Aktarımları (içinde aynı uç noktası) etkinlikleri ve yayma (uç noktalar arasında) ilişkilendirmek mümkündür. Bu örnekte, hem istemci hem de hizmet için izleme etkinleştirilir. İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz: [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>İzleme ve Etkinlik yayma  
 Kullanıcı tanımlı Etkinlik izleme sağlayan kendi aktarımları ve yayma ile çalışma, correlate etkinliklerin mantıksal birimler Grup izlemeleri için izleme etkinliklerine oluşturmak ve performans maliyetini azaltmak kullanıcı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izleme (örneğin, disk alanı maliyeti bir günlük dosyası).  
  
### <a name="adding-custom-sources"></a>Özel kaynakları ekleme  
 Kullanıcı tanımlı izlemeleri için hem istemci hem de hizmet kod eklenebilir. İzleme kaynakları istemci veya hizmet yapılandırması dosyalara izin kaydedilir ve görüntülenen bu özel izlemeleri için ekleme [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Aşağıdaki kod adlı bir kullanıcı tarafından tanımlanan izleme kaynağı eklemeyi gösterir `ServerCalculatorTraceSource` yapılandırma dosyasına.  
  
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
  
### <a name="correlating-activities"></a>Bağıntı etkinlikleri  
 Doğrudan uç noktalar arasında etkinliklerini ilişkilendirmek için `propagateActivity` özniteliği ayarlanmalıdır `true` içinde `System.ServiceModel` izleme kaynağı. Ayrıca, oluşturulmak olmadan izlemeleri yayılmasına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] etkinliklerini, etkinlik ServiceModel izleme kapalı olmalıdır. Bu, aşağıdaki kod örneğinde görülebilir.  
  
> [!NOTE]
>  ServiceModel etkinliği izleme devre dışı kapatma değil tarafından belirtilen izleme düzeyi sahip aynı `switchValue` özelliği ayarlamak kapalı.  
  
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
 Ayarı `ActivityTracing` içinde kapalı `System.ServiceModel` izleme kaynağı yalnızca kullanıcı tanımlı Etkinlik izleme, herhangi bir dahil ServiceModel etkinlik izlemeleri içeren bir izleme dosyası oluşturur. Bu, çok daha küçük boyutu bir günlük dosyasında sonuçlanır. Ancak, ilişkilendirmek için Fırsat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izlemeler işlenirken kaybolur.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)

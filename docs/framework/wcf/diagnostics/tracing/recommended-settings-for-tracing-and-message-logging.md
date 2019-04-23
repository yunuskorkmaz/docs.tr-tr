---
title: İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: fa6dc74a26f6a76591a15c549a892f31a65c521e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132372"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
Bu konu, önerilen izleme ve farklı işletim ortamlarının için ileti günlüğe kaydetme ayarlarını açıklar.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Bir üretim ortamı için önerilen ayarlar  
 WCF izleme kaynakları kullanıyorsanız, bir üretim ortamı için ayarlanmış `switchValue` uyarı. WCF kullanıyorsanız `System.ServiceModel` izleme kaynağı, Ayarla `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini `true`. Bir kullanıcı tanımlı izleme kaynağı kullanıyorsanız `switchValue` özniteliğini `Warning, ActivityTracing`. Bu kullanarak el ile yapılabilir [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). İsabet performans düşünmüyoruz, ayarlayabileceğiniz `switchValue` özniteliğini `Information` tüm daha önce de belirtildiği durumlarda, izleme verilerinin oldukça büyük bir miktarını oluşturduğu. Aşağıdaki örnek, bu önerilen ayarları gösterir.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Dağıtım veya hata ayıklama için önerilen ayarlar  
 Dağıtım veya hata ayıklama ortamı seçin `Information` veya `Verbose`, birlikte `ActivityTracing` ya da kullanıcı tanımlı bir için veya `System.ServiceModel` izleme kaynağı. Hata ayıklamayı iyileştirme için de bir ek izleme kaynağı eklemeniz gerekir (`System.ServiceModel.MessageLogging`) ileti günlüğe kaydetmeyi etkinleştirmek için yapılandırma. Dikkat `switchValue` özniteliği bu iz herhangi bir etkisi vardır.  
  
 Aşağıdaki örnek, önerilen ayarları kullanan bir paylaşılan dinleyici kullanarak gösterir `XmlWriterTraceListener`.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a>Ayarları değiştirmek için WMI'yı kullanarak  
 WMI zamanında yapılandırma ayarlarını değiştirmek için kullanabileceğiniz (etkinleştirerek `wmiProviderEnabled` gösterildiği şekilde yapılandırmada özniteliği daha önce yapılandırma örneği). Örneğin, WMI CIM Studio'dan izleme kaynak düzeylerini uyarıyı bilgi çalışma zamanında değiştirmek için kullanabilirsiniz. Bu şekilde Canlı hata ayıklama performans maliyeti çok yüksek olduğunu bilmeniz gerekir. WMI kullanma hakkında daha fazla bilgi için bkz. [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) konu.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>ASP.NET izleme, bağıntılı olaylar etkinleştir  
 ASP.NET olay izleme etkinleştirilmemişse, ASP.NET olayları bağıntı Kimliğini (ActivityID) ayarlamayın. ASP.NET olaylarına açmak zorunda bağıntılı olaylar düzgün şekilde görmek için komut konsolunda aşağıdaki komutu kullanarak izleme, hangi çağrılacak giderek **Başlat**, **çalıştırma** ve türü **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 ASP.NET olaylarını izlemeyi devre dışı bırakmak için aşağıdaki komutu kullanın,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama için Windows Yönetim Araçlarını Kullanma](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

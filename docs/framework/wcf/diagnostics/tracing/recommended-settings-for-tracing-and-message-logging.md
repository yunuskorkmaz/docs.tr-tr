---
title: İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 44cdf90572cc52d5daf95368a644759be0ad1ee0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
Bu konu, önerilen izleme ve farklı işletim ortamlar için ileti günlüğe kaydetme ayarlarını açıklar.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Bir üretim ortamı için önerilen ayarları  
 WCF izleme kaynakları kullanıyorsanız, bir üretim ortamı için ayarlanmış `switchValue` uyarı. WCF kullanıyorsanız `System.ServiceModel` izleme kaynağı, Ayarla `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini `true`. Kullanıcı tanımlı izleme kaynağı kullanıyorsanız, ayarlamak `switchValue` özniteliğini `Warning, ActivityTracing`. Bu kullanarak el ile yapılabilir [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). İsabet performans düşündüğünüz değil, ayarlayabileceğiniz `switchValue` özniteliğini `Information` tüm yukarıda açıklanan durumlarda, hangi oluşturur, izleme verilerinin oldukça büyük bir miktarını. Aşağıdaki örnek, bu önerilen ayarları gösterir.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Dağıtım veya hata ayıklama için önerilen ayarları  
 Dağıtım veya hata ayıklama ortamı için seçin `Information` veya `Verbose`, birlikte `ActivityTracing` ya da bir kullanıcı tarafından tanımlanan için veya `System.ServiceModel` izleme kaynağı. Hata ayıklama geliştirmek için de bir ek izleme kaynağı eklemeniz gerekir (`System.ServiceModel.MessageLogging`) ileti günlüğe kaydetmeyi etkinleştirmek için yapılandırma. Dikkat `switchValue` özniteliği bu izleme kaynağı üzerinde hiçbir etkisi vardır.  
  
 Önerilen ayarları kullanan paylaşılan bir dinleyici kullanarak, aşağıdaki örnekte gösterilmiştir `XmlWriterTraceListener`.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Ayarları değiştirmek için WMI kullanma  
 Çalışma zamanında yapılandırma ayarlarını değiştirmek için WMI kullanabilirsiniz (etkinleştirerek `wmiProviderEnabled` şekilde yapılandırmasında özniteliği daha önce yapılandırma örneği). Örneğin, WMI CIM Studio içinde izleme kaynağı düzeyleri uyarıdan bilgileri çalışma zamanında değiştirmek için kullanabilirsiniz. Bu şekilde dinamik hata ayıklama performans maliyeti oldukça yüksek olabilir bilmeniz gerekir. WMI kullanma hakkında daha fazla bilgi için bkz: [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) konu.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>ASP.NET izleme, bağıntılı olaylar etkinleştir  
 ASP.NET olay izleme etkinleştirilmemişse ASP.NET olayları bağıntı kimliği (ActivityID) ayarlamayın. ASP.NET olaylarına açmak zorunda bağıntılı olaylar düzgün şekilde görmek için komut konsolunda şu komutu kullanarak izleme, hangi çağrılabilir giderek **Başlat**, **çalıştırmak** ve türü **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 ASP.NET olayları izlemeyi devre dışı bırakmak için aşağıdaki komutu kullanın,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama için Windows Yönetim Araçlarını Kullanma](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

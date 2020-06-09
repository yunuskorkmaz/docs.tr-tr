---
title: İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 9d2586570a3f590735c2a8e1ca176580886c8d92
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578922"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
Bu konuda, farklı işletim ortamları için önerilen izleme ve ileti günlüğü ayarları açıklanmaktadır.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Üretim ortamı için önerilen ayarlar  
 Bir üretim ortamında, WCF izleme kaynaklarını kullanıyorsanız, `switchValue` uyarı olarak ayarlayın. WCF `System.ServiceModel` izleme kaynağını kullanıyorsanız, `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini olarak ayarlayın `true` . Kullanıcı tanımlı bir izleme kaynağı kullanıyorsanız, `switchValue` özniteliğini olarak ayarlayın `Warning, ActivityTracing` . Bu işlem, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak el ile yapılabilir. Performans için bir isabet tahmin ediyorsanız, `switchValue` özniteliğini `Information` daha önce bahsedilen tüm durumlarda olarak ayarlayabilirsiniz. Bu, çok büyük miktarda izleme verisi üretir. Aşağıdaki örnek, önerilen bu ayarları gösterir.  
  
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
 Dağıtım veya hata ayıklama ortamında, `Information` `Verbose` `ActivityTracing` Kullanıcı tanımlı ya da izleme kaynağı için ile birlikte veya seçin `System.ServiceModel` . Hata ayıklamayı geliştirmek için, Ayrıca, `System.ServiceModel.MessageLogging` ileti günlüğe kaydetmeyi etkinleştirmek üzere yapılandırmaya ek bir izleme kaynağı () eklemeniz gerekir. `switchValue`Özniteliğin bu izleme kaynağını üzerinde hiçbir etkisi olmadığına dikkat edin.  
  
 Aşağıdaki örnek, tarafından kullanılan paylaşılan bir dinleyiciyi kullanarak önerilen ayarları gösterir `XmlWriterTraceListener` .  
  
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
 WMI 'yi, çalışma zamanındaki yapılandırma ayarlarını değiştirmek için kullanabilirsiniz ( `wmiProviderEnabled` daha önce yapılandırma örneğinde gösterildiği gibi, yapılandırmadaki özniteliğini etkinleştirerek). Örneğin, Trace kaynak düzeylerini, çalışma zamanında bilgi olarak uyarı olarak değiştirmek için CıM Studio içinde WMI kullanabilirsiniz. Bu şekilde, canlı hata ayıklama performans maliyetinin çok yüksek olduğunu bilmelisiniz. WMI kullanma hakkında daha fazla bilgi için [Tanılama için Windows Yönetim araçları kullanma](../wmi/index.md) konusuna bakın.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>ASP.NET Izlemede bağıntılı olayları etkinleştirme  
 ASP.NET olayları, ASP.NET olay izleme açık değilse bağıntı KIMLIĞINI (ActivityId) ayarlamayın. Bağıntılı olayları doğru şekilde görmek için, komut konsolunda aşağıdaki komutu kullanarak ASP.NET olayları izlemeyi açmanız gerekir. Bu, **Başlat**, **Çalıştır** **ve yaz komutları**kullanılarak çağrılabilir.  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 ASP.NET olaylarının izlenmesini devre dışı bırakmak için aşağıdaki komutu kullanın,  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama için Windows Yönetim Araçları kullanma](../wmi/index.md)

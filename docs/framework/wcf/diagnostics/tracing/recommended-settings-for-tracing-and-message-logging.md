---
title: İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 6e671762edb2d1ca71ce14cb6ef66c64e02bc297
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856087"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
Bu konuda, farklı işletim ortamları için önerilen izleme ve ileti günlüğü ayarları açıklanmaktadır.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Üretim ortamı için önerilen ayarlar  
 Bir üretim ortamında, WCF izleme kaynaklarını kullanıyorsanız, uyarı `switchValue` olarak ayarlayın. WCF `System.ServiceModel` izleme kaynağını kullanıyorsanız, `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini olarak `true`ayarlayın. Kullanıcı tanımlı bir izleme kaynağı kullanıyorsanız, `switchValue` özniteliğini olarak `Warning, ActivityTracing`ayarlayın. Bu işlem, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak el ile yapılabilir. Performans için bir isabet tahmin ediyorsanız, `switchValue` özniteliğini daha önce bahsedilen tüm durumlarda olarak `Information` ayarlayabilirsiniz. Bu, çok büyük miktarda izleme verisi üretir. Aşağıdaki örnek, önerilen bu ayarları gösterir.  
  
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
 Dağıtım veya hata ayıklama ortamında, Kullanıcı `Information` tanımlı `Verbose`ya `System.ServiceModel` da izleme `ActivityTracing` kaynağı için ile birlikte veya seçin. Hata ayıklamayı geliştirmek için, Ayrıca, ileti günlüğe kaydetmeyi etkinleştirmek üzere yapılandırmaya`System.ServiceModel.MessageLogging`ek bir izleme kaynağı () eklemeniz gerekir. `switchValue` Özniteliğin bu izleme kaynağını üzerinde hiçbir etkisi olmadığına dikkat edin.  
  
 Aşağıdaki örnek, `XmlWriterTraceListener`tarafından kullanılan paylaşılan bir dinleyiciyi kullanarak önerilen ayarları gösterir.  
  
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
 WMI 'yi, çalışma zamanındaki yapılandırma ayarlarını değiştirmek için kullanabilirsiniz (daha önce yapılandırma `wmiProviderEnabled` örneğinde gösterildiği gibi, yapılandırmadaki özniteliğini etkinleştirerek). Örneğin, Trace kaynak düzeylerini, çalışma zamanında bilgi olarak uyarı olarak değiştirmek için CıM Studio içinde WMI kullanabilirsiniz. Bu şekilde, canlı hata ayıklama performans maliyetinin çok yüksek olduğunu bilmelisiniz. WMI kullanma hakkında daha fazla bilgi için [Tanılama için Windows Yönetim araçları kullanma](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) konusuna bakın.  
  
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

- [Tanılama için Windows Yönetim Araçlarını Kullanma](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

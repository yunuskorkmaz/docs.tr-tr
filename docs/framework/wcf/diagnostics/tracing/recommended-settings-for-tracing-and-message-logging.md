---
title: İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 604aae2c0a0c5390428e7f1a2c99e17e90ee76a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185724"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar
Bu konu, farklı çalışma ortamları için önerilen izleme ve ileti günlüğe kaydetme ayarlarını açıklar.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Üretim Ortamı Için Önerilen Ayarlar  
 Bir üretim ortamı için, WCF izleme kaynakları `switchValue` kullanıyorsanız, Uyarı'yı ayarlayın. WCF `System.ServiceModel` izleme kaynağını `switchValue` kullanıyorsanız, özniteliği `Warning` ve `propagateActivity` özniteliği ' `true`ye ayarlayın. Kullanıcı tanımlı bir izleme kaynağı kullanıyorsanız, `switchValue` özniteliği . `Warning, ActivityTracing` Bu Configuration Editor Aracı [(SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak el ile yapılabilir. Performansta bir isabet beklemiyorsanız, özniteliği `switchValue` `Information` daha önce bahsedilen tüm durumlarda ayarlayabilirsiniz ve bu da oldukça büyük miktarda izleme verisi oluşturur. Aşağıdaki örnek, önerilen bu ayarları gösterir.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Dağıtım veya Hata Ayıklama için Önerilen Ayarlar  
 Dağıtım veya hata ayıklama ortamı `Information` `Verbose`için, `ActivityTracing` kullanıcı tarafından tanımlanan veya `System.ServiceModel` izleme kaynağı için seçin veya birlikte. Hata ayıklamayı geliştirmek için, ileti günlüğe`System.ServiceModel.MessageLogging`kaydetmeyi etkinleştirmek için yapılandırmaya ek bir izleme kaynağı () eklemeniz gerekir. Özniteliğin `switchValue` bu izleme kaynağı üzerinde hiçbir etkisi olmadığına dikkat edin.  
  
 Aşağıdaki örnekte, paylaşılan bir dinleyici kullanılarak önerilen ayarları `XmlWriterTraceListener`gösterir.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Ayarları Değiştirmek için WMI kullanma  
 Çalışma zamanında yapılandırma ayarlarını değiştirmek için WMI'yi `wmiProviderEnabled` kullanabilirsiniz (daha önceki yapılandırma örneğinde gösterildiği gibi yapılandırmadaki özniteliği etkinleştirerek). Örneğin, çalışma zamanında Izleme kaynağı düzeylerini Uyarı'dan Bilgiye değiştirmek için CIM Studio içindeki WMI'yi kullanabilirsiniz. Bu şekilde canlı hata ayıklama performans maliyeti çok yüksek olabilir farkında olmalıdır. WMI kullanma hakkında daha fazla bilgi için [Tanılama için Windows Yönetim Aracını Kullanma konusuna](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) bakın.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>ASP.NET İzlemede İlişkili Olayları Etkinleştirme  
 ASP.NET olaylar, ASP.NET olay izleme açık olmadığı sürece korelasyon kimliğini (ActivityID) ayarlamaz. Korelasyonlu olayları düzgün görmek için, komut konsolundaki aşağıdaki komutu kullanarak ASP.NET olayları takip ederek açmanız gerekir, bu komut konsoluna giderek çağrılabilir **,** **Çalıştır** ve **cmd**yazın ,  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 ASP.NET olaylarının izini kapatmak için aşağıdaki komutu kullanın,  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama için Windows Yönetim İzlemesini Kullanma](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

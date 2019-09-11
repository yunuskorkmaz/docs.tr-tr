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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="45767-102">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="45767-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="45767-103">Bu konuda, farklı işletim ortamları için önerilen izleme ve ileti günlüğü ayarları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45767-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="45767-104">Üretim ortamı için önerilen ayarlar</span><span class="sxs-lookup"><span data-stu-id="45767-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="45767-105">Bir üretim ortamında, WCF izleme kaynaklarını kullanıyorsanız, uyarı `switchValue` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="45767-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="45767-106">WCF `System.ServiceModel` izleme kaynağını kullanıyorsanız, `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="45767-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="45767-107">Kullanıcı tanımlı bir izleme kaynağı kullanıyorsanız, `switchValue` özniteliğini olarak `Warning, ActivityTracing`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="45767-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="45767-108">Bu işlem, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak el ile yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="45767-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="45767-109">Performans için bir isabet tahmin ediyorsanız, `switchValue` özniteliğini daha önce bahsedilen tüm durumlarda olarak `Information` ayarlayabilirsiniz. Bu, çok büyük miktarda izleme verisi üretir.</span><span class="sxs-lookup"><span data-stu-id="45767-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="45767-110">Aşağıdaki örnek, önerilen bu ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="45767-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="45767-111">Dağıtım veya hata ayıklama için önerilen ayarlar</span><span class="sxs-lookup"><span data-stu-id="45767-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="45767-112">Dağıtım veya hata ayıklama ortamında, Kullanıcı `Information` tanımlı `Verbose`ya `System.ServiceModel` da izleme `ActivityTracing` kaynağı için ile birlikte veya seçin.</span><span class="sxs-lookup"><span data-stu-id="45767-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="45767-113">Hata ayıklamayı geliştirmek için, Ayrıca, ileti günlüğe kaydetmeyi etkinleştirmek üzere yapılandırmaya`System.ServiceModel.MessageLogging`ek bir izleme kaynağı () eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="45767-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="45767-114">`switchValue` Özniteliğin bu izleme kaynağını üzerinde hiçbir etkisi olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="45767-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="45767-115">Aşağıdaki örnek, `XmlWriterTraceListener`tarafından kullanılan paylaşılan bir dinleyiciyi kullanarak önerilen ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="45767-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="45767-116">Ayarları değiştirmek için WMI kullanma</span><span class="sxs-lookup"><span data-stu-id="45767-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="45767-117">WMI 'yi, çalışma zamanındaki yapılandırma ayarlarını değiştirmek için kullanabilirsiniz (daha önce yapılandırma `wmiProviderEnabled` örneğinde gösterildiği gibi, yapılandırmadaki özniteliğini etkinleştirerek).</span><span class="sxs-lookup"><span data-stu-id="45767-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="45767-118">Örneğin, Trace kaynak düzeylerini, çalışma zamanında bilgi olarak uyarı olarak değiştirmek için CıM Studio içinde WMI kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45767-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="45767-119">Bu şekilde, canlı hata ayıklama performans maliyetinin çok yüksek olduğunu bilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="45767-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="45767-120">WMI kullanma hakkında daha fazla bilgi için [Tanılama için Windows Yönetim araçları kullanma](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="45767-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="45767-121">ASP.NET Izlemede bağıntılı olayları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="45767-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="45767-122">ASP.NET olayları, ASP.NET olay izleme açık değilse bağıntı KIMLIĞINI (ActivityId) ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="45767-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="45767-123">Bağıntılı olayları doğru şekilde görmek için, komut konsolunda aşağıdaki komutu kullanarak ASP.NET olayları izlemeyi açmanız gerekir. Bu, **Başlat**, **Çalıştır** **ve yaz komutları**kullanılarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="45767-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="45767-124">ASP.NET olaylarının izlenmesini devre dışı bırakmak için aşağıdaki komutu kullanın,</span><span class="sxs-lookup"><span data-stu-id="45767-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="45767-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45767-125">See also</span></span>

- [<span data-ttu-id="45767-126">Tanılama için Windows Yönetim Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="45767-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="ec084-102">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="ec084-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="ec084-103">Bu konuda, farklı işletim ortamları için önerilen izleme ve ileti günlüğü ayarları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec084-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="ec084-104">Üretim ortamı için önerilen ayarlar</span><span class="sxs-lookup"><span data-stu-id="ec084-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="ec084-105">Bir üretim ortamında, WCF izleme kaynaklarını kullanıyorsanız, `switchValue` uyarı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec084-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="ec084-106">WCF `System.ServiceModel` izleme kaynağını kullanıyorsanız, `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="ec084-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="ec084-107">Kullanıcı tanımlı bir izleme kaynağı kullanıyorsanız, `switchValue` özniteliğini olarak ayarlayın `Warning, ActivityTracing` .</span><span class="sxs-lookup"><span data-stu-id="ec084-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="ec084-108">Bu işlem, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak el ile yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec084-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="ec084-109">Performans için bir isabet tahmin ediyorsanız, `switchValue` özniteliğini `Information` daha önce bahsedilen tüm durumlarda olarak ayarlayabilirsiniz. Bu, çok büyük miktarda izleme verisi üretir.</span><span class="sxs-lookup"><span data-stu-id="ec084-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="ec084-110">Aşağıdaki örnek, önerilen bu ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec084-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="ec084-111">Dağıtım veya hata ayıklama için önerilen ayarlar</span><span class="sxs-lookup"><span data-stu-id="ec084-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="ec084-112">Dağıtım veya hata ayıklama ortamında, `Information` `Verbose` `ActivityTracing` Kullanıcı tanımlı ya da izleme kaynağı için ile birlikte veya seçin `System.ServiceModel` .</span><span class="sxs-lookup"><span data-stu-id="ec084-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="ec084-113">Hata ayıklamayı geliştirmek için, Ayrıca, `System.ServiceModel.MessageLogging` ileti günlüğe kaydetmeyi etkinleştirmek üzere yapılandırmaya ek bir izleme kaynağı () eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec084-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="ec084-114">`switchValue`Özniteliğin bu izleme kaynağını üzerinde hiçbir etkisi olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ec084-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="ec084-115">Aşağıdaki örnek, tarafından kullanılan paylaşılan bir dinleyiciyi kullanarak önerilen ayarları gösterir `XmlWriterTraceListener` .</span><span class="sxs-lookup"><span data-stu-id="ec084-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="ec084-116">Ayarları değiştirmek için WMI kullanma</span><span class="sxs-lookup"><span data-stu-id="ec084-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="ec084-117">WMI 'yi, çalışma zamanındaki yapılandırma ayarlarını değiştirmek için kullanabilirsiniz ( `wmiProviderEnabled` daha önce yapılandırma örneğinde gösterildiği gibi, yapılandırmadaki özniteliğini etkinleştirerek).</span><span class="sxs-lookup"><span data-stu-id="ec084-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="ec084-118">Örneğin, Trace kaynak düzeylerini, çalışma zamanında bilgi olarak uyarı olarak değiştirmek için CıM Studio içinde WMI kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec084-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="ec084-119">Bu şekilde, canlı hata ayıklama performans maliyetinin çok yüksek olduğunu bilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ec084-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="ec084-120">WMI kullanma hakkında daha fazla bilgi için [Tanılama için Windows Yönetim araçları kullanma](../wmi/index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="ec084-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="ec084-121">ASP.NET Izlemede bağıntılı olayları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ec084-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="ec084-122">ASP.NET olayları, ASP.NET olay izleme açık değilse bağıntı KIMLIĞINI (ActivityId) ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="ec084-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="ec084-123">Bağıntılı olayları doğru şekilde görmek için, komut konsolunda aşağıdaki komutu kullanarak ASP.NET olayları izlemeyi açmanız gerekir. Bu, **Başlat**, **Çalıştır** **ve yaz komutları**kullanılarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec084-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="ec084-124">ASP.NET olaylarının izlenmesini devre dışı bırakmak için aşağıdaki komutu kullanın,</span><span class="sxs-lookup"><span data-stu-id="ec084-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec084-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec084-125">See also</span></span>

- [<span data-ttu-id="ec084-126">Tanılama için Windows Yönetim Araçları kullanma</span><span class="sxs-lookup"><span data-stu-id="ec084-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)

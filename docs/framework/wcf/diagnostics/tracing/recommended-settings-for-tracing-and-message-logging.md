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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="0ba64-102">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="0ba64-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="0ba64-103">Bu konu, farklı çalışma ortamları için önerilen izleme ve ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ba64-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="0ba64-104">Üretim Ortamı Için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="0ba64-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="0ba64-105">Bir üretim ortamı için, WCF izleme kaynakları `switchValue` kullanıyorsanız, Uyarı'yı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ba64-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="0ba64-106">WCF `System.ServiceModel` izleme kaynağını `switchValue` kullanıyorsanız, özniteliği `Warning` ve `propagateActivity` özniteliği ' `true`ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ba64-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="0ba64-107">Kullanıcı tanımlı bir izleme kaynağı kullanıyorsanız, `switchValue` özniteliği . `Warning, ActivityTracing`</span><span class="sxs-lookup"><span data-stu-id="0ba64-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="0ba64-108">Bu Configuration Editor Aracı [(SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak el ile yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba64-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="0ba64-109">Performansta bir isabet beklemiyorsanız, özniteliği `switchValue` `Information` daha önce bahsedilen tüm durumlarda ayarlayabilirsiniz ve bu da oldukça büyük miktarda izleme verisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ba64-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="0ba64-110">Aşağıdaki örnek, önerilen bu ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ba64-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="0ba64-111">Dağıtım veya Hata Ayıklama için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="0ba64-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="0ba64-112">Dağıtım veya hata ayıklama ortamı `Information` `Verbose`için, `ActivityTracing` kullanıcı tarafından tanımlanan veya `System.ServiceModel` izleme kaynağı için seçin veya birlikte.</span><span class="sxs-lookup"><span data-stu-id="0ba64-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="0ba64-113">Hata ayıklamayı geliştirmek için, ileti günlüğe`System.ServiceModel.MessageLogging`kaydetmeyi etkinleştirmek için yapılandırmaya ek bir izleme kaynağı () eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ba64-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="0ba64-114">Özniteliğin `switchValue` bu izleme kaynağı üzerinde hiçbir etkisi olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0ba64-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="0ba64-115">Aşağıdaki örnekte, paylaşılan bir dinleyici kullanılarak önerilen ayarları `XmlWriterTraceListener`gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ba64-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="0ba64-116">Ayarları Değiştirmek için WMI kullanma</span><span class="sxs-lookup"><span data-stu-id="0ba64-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="0ba64-117">Çalışma zamanında yapılandırma ayarlarını değiştirmek için WMI'yi `wmiProviderEnabled` kullanabilirsiniz (daha önceki yapılandırma örneğinde gösterildiği gibi yapılandırmadaki özniteliği etkinleştirerek).</span><span class="sxs-lookup"><span data-stu-id="0ba64-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="0ba64-118">Örneğin, çalışma zamanında Izleme kaynağı düzeylerini Uyarı'dan Bilgiye değiştirmek için CIM Studio içindeki WMI'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ba64-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="0ba64-119">Bu şekilde canlı hata ayıklama performans maliyeti çok yüksek olabilir farkında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ba64-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="0ba64-120">WMI kullanma hakkında daha fazla bilgi için [Tanılama için Windows Yönetim Aracını Kullanma konusuna](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ba64-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="0ba64-121">ASP.NET İzlemede İlişkili Olayları Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0ba64-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="0ba64-122">ASP.NET olaylar, ASP.NET olay izleme açık olmadığı sürece korelasyon kimliğini (ActivityID) ayarlamaz.</span><span class="sxs-lookup"><span data-stu-id="0ba64-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="0ba64-123">Korelasyonlu olayları düzgün görmek için, komut konsolundaki aşağıdaki komutu kullanarak ASP.NET olayları takip ederek açmanız gerekir, bu komut konsoluna giderek çağrılabilir **,** **Çalıştır** ve **cmd**yazın ,</span><span class="sxs-lookup"><span data-stu-id="0ba64-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="0ba64-124">ASP.NET olaylarının izini kapatmak için aşağıdaki komutu kullanın,</span><span class="sxs-lookup"><span data-stu-id="0ba64-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ba64-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba64-125">See also</span></span>

- [<span data-ttu-id="0ba64-126">Tanılama için Windows Yönetim İzlemesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="0ba64-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

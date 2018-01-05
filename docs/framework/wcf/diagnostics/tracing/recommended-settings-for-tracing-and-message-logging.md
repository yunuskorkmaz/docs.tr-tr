---
title: "İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bca09510a73a74b039ec18934c0be39629c4ce39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="ddaa9-102">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="ddaa9-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="ddaa9-103">Bu konu, önerilen izleme ve farklı işletim ortamlar için ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="ddaa9-104">Bir üretim ortamı için önerilen ayarları</span><span class="sxs-lookup"><span data-stu-id="ddaa9-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="ddaa9-105">WCF izleme kaynakları kullanıyorsanız, bir üretim ortamı için ayarlanmış `switchValue` uyarı.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="ddaa9-106">WCF kullanıyorsanız `System.ServiceModel` izleme kaynağı, Ayarla `switchValue` özniteliğini `Warning` ve `propagateActivity` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="ddaa9-107">Kullanıcı tanımlı izleme kaynağı kullanıyorsanız, ayarlamak `switchValue` özniteliğini `Warning, ActivityTracing`.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="ddaa9-108">Bu kullanarak el ile yapılabilir [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ddaa9-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="ddaa9-109">İsabet performans düşündüğünüz değil, ayarlayabileceğiniz `switchValue` özniteliğini `Information` tüm yukarıda açıklanan durumlarda, hangi oluşturur, izleme verilerinin oldukça büyük bir miktarını.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="ddaa9-110">Aşağıdaki örnek, bu önerilen ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="ddaa9-111">Dağıtım veya hata ayıklama için önerilen ayarları</span><span class="sxs-lookup"><span data-stu-id="ddaa9-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="ddaa9-112">Dağıtım veya hata ayıklama ortamı için seçin `Information` veya `Verbose`, birlikte `ActivityTracing` ya da bir kullanıcı tarafından tanımlanan için veya `System.ServiceModel` izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="ddaa9-113">Hata ayıklama geliştirmek için de bir ek izleme kaynağı eklemeniz gerekir (`System.ServiceModel.MessageLogging`) ileti günlüğe kaydetmeyi etkinleştirmek için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="ddaa9-114">Dikkat `switchValue` özniteliği bu izleme kaynağı üzerinde hiçbir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="ddaa9-115">Önerilen ayarları kullanan paylaşılan bir dinleyici kullanarak, aşağıdaki örnekte gösterilmiştir `XmlWriterTraceListener`.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="ddaa9-116">Ayarları değiştirmek için WMI kullanma</span><span class="sxs-lookup"><span data-stu-id="ddaa9-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="ddaa9-117">Çalışma zamanında yapılandırma ayarlarını değiştirmek için WMI kullanabilirsiniz (etkinleştirerek `wmiProviderEnabled` şekilde yapılandırmasında özniteliği daha önce yapılandırma örneği).</span><span class="sxs-lookup"><span data-stu-id="ddaa9-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="ddaa9-118">Örneğin, WMI CIM Studio içinde izleme kaynağı düzeyleri uyarıdan bilgileri çalışma zamanında değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="ddaa9-119">Bu şekilde dinamik hata ayıklama performans maliyeti oldukça yüksek olabilir bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="ddaa9-120">WMI kullanma hakkında daha fazla bilgi için bkz: [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="ddaa9-121">ASP.NET izleme, bağıntılı olaylar etkinleştir</span><span class="sxs-lookup"><span data-stu-id="ddaa9-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="ddaa9-122">ASP.NET olay izleme etkinleştirilmemişse ASP.NET olayları bağıntı kimliği (ActivityID) ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="ddaa9-123">ASP.NET olaylarına açmak zorunda bağıntılı olaylar düzgün şekilde görmek için komut konsolunda şu komutu kullanarak izleme, hangi çağrılabilir giderek **Başlat**, **çalıştırmak** ve türü **cmd** ,</span><span class="sxs-lookup"><span data-stu-id="ddaa9-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="ddaa9-124">ASP.NET olayları izlemeyi devre dışı bırakmak için aşağıdaki komutu kullanın,</span><span class="sxs-lookup"><span data-stu-id="ddaa9-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddaa9-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ddaa9-125">See Also</span></span>  
 [<span data-ttu-id="ddaa9-126">Tanılama için Windows Yönetim Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ddaa9-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

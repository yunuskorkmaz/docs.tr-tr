---
title: İş Akışı İzleme
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 972520aae7a2af950ed1ba079769861173784148
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837512"
---
# <a name="workflow-tracing"></a><span data-ttu-id="edde0-102">İş Akışı İzleme</span><span class="sxs-lookup"><span data-stu-id="edde0-102">Workflow Tracing</span></span>
<span data-ttu-id="edde0-103">İş akışı izleme .NET Framework İzleme dinleyicilerini kullanarak tanılama bilgilerini yakalamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="edde0-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="edde0-104">Uygulama ile ilgili bir sorun algılanırsa izleme etkinleştirilebilir ve sorun çözümlendikten sonra yeniden devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="edde0-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="edde0-105">İş akışları için hata ayıklama izlemeyi etkinleştirmenin iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="edde0-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="edde0-106">Bunu olay Izleme görüntüleyicisini kullanarak yapılandırabilir veya izleme olaylarını bir dosyaya göndermek için <xref:System.Diagnostics> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edde0-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="edde0-107">ETW 'de hata ayıklama Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="edde0-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="edde0-108">ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi hata ayıklama kanalını etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="edde0-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="edde0-109">Olay Görüntüleyicisi 'de analitik ve hata ayıklama günlükleri düğümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="edde0-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="edde0-110">Olay Görüntüleyicisi 'daki ağaç görünümünde, **Olay Görüntüleyicisi > uygulamalar ve hizmet günlükleri-> Microsoft-> Windows-> uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="edde0-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="edde0-111">**Uygulama sunucusu-uygulamalar** ' a sağ tıklayın ve **Görünüm-> analitik ve hata ayıklama günlüklerini göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="edde0-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="edde0-112">**Hata Ayıkla** ' ya sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="edde0-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="edde0-113">Bir iş akışı, hata ayıklamayı çalıştırdığında ve izlemeler ETW hata ayıklama kanalına yayıldıklarında, Olay Görüntüleyicisi görüntülenebilirler.</span><span class="sxs-lookup"><span data-stu-id="edde0-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="edde0-114">**Olay Görüntüleyicisi > uygulamalar ve hizmet günlükleri-> Microsoft-> Windows-> uygulama sunucusu-uygulamalar '** a gidin.</span><span class="sxs-lookup"><span data-stu-id="edde0-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="edde0-115">**Hata Ayıkla** ' ya sağ tıklayın ve **Yenile**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="edde0-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="edde0-116">Varsayılan analitik izleme arabelleği boyutu yalnızca 4 kilobayttır (KB); boyutu 32 KB olarak artırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="edde0-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="edde0-117">Bunu yapmak için aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="edde0-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="edde0-118">Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="edde0-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="edde0-119">Windows. ApplicationServer. Applications. Man dosyasındaki \<bufferSize > değerini 32 olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="edde0-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="edde0-120">Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="edde0-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edde0-121">.NET Framework 4 Istemci profilini kullanıyorsanız, önce .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak ETW bildirimini kaydetmeniz gerekir: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="edde0-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="edde0-122">System. Diagnostics kullanarak hata ayıklama Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="edde0-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="edde0-123">Bu dinleyiciler iş akışı uygulamasının App. config dosyasında veya bir iş akışı hizmeti için Web. config ' de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="edde0-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="edde0-124">Bu örnekte, izleme bilgilerini geçerli dizindeki MyTraceLog. txt dosyasına kaydetmek için bir <xref:System.Diagnostics.TextWriterTraceListener> yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="edde0-124">In this example, a <xref:System.Diagnostics.TextWriterTraceListener> is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edde0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edde0-125">See also</span></span>

- <span data-ttu-id="edde0-126">[Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="edde0-126">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="edde0-127">[App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="edde0-127">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>

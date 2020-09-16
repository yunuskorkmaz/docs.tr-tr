---
title: İş Akışı İzleme
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: fc27be295cbf0a83b65ff03e36f2aeffeda12db9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557508"
---
# <a name="workflow-tracing"></a><span data-ttu-id="e4302-102">İş Akışı İzleme</span><span class="sxs-lookup"><span data-stu-id="e4302-102">Workflow Tracing</span></span>
<span data-ttu-id="e4302-103">İş akışı izleme .NET Framework İzleme dinleyicilerini kullanarak tanılama bilgilerini yakalamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="e4302-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="e4302-104">Uygulama ile ilgili bir sorun algılanırsa izleme etkinleştirilebilir ve sorun çözümlendikten sonra yeniden devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4302-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="e4302-105">İş akışları için hata ayıklama izlemeyi etkinleştirmenin iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e4302-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="e4302-106">Bunu olay Izleme görüntüleyicisini kullanarak yapılandırabilir veya <xref:System.Diagnostics> izleme olaylarını bir dosyaya göndermek için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4302-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="e4302-107">ETW 'de hata ayıklama Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e4302-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="e4302-108">ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi hata ayıklama kanalını etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="e4302-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="e4302-109">Olay Görüntüleyicisi 'de analitik ve hata ayıklama günlükleri düğümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="e4302-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="e4302-110">Olay Görüntüleyicisi 'daki ağaç görünümünde, **Olay Görüntüleyicisi >uygulamalar ve hizmet günlükleri->Microsoft->Windows->uygulama sunucusu-uygulamalar**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="e4302-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="e4302-111">**Uygulama sunucusu-uygulamalar** ' a sağ tıklayın ve **Görünüm->analitik ve hata ayıklama günlüklerini göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e4302-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="e4302-112">**Hata Ayıkla** ' ya sağ tıklayın ve **günlüğü etkinleştir**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e4302-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="e4302-113">Bir iş akışı, hata ayıklamayı çalıştırdığında ve izlemeler ETW hata ayıklama kanalına yayıldıklarında, Olay Görüntüleyicisi görüntülenebilirler.</span><span class="sxs-lookup"><span data-stu-id="e4302-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="e4302-114">**Olay Görüntüleyicisi >uygulamalar ve hizmet günlükleri->Microsoft->Windows->uygulama sunucusu-uygulamalar '** a gidin.</span><span class="sxs-lookup"><span data-stu-id="e4302-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="e4302-115">**Hata Ayıkla** ' ya sağ tıklayın ve **Yenile**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e4302-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="e4302-116">Varsayılan analitik izleme arabelleği boyutu yalnızca 4 kilobayttır (KB); boyutu 32 KB olarak artırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="e4302-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="e4302-117">Bunu yapmak için aşağıdaki adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e4302-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="e4302-118">Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="e4302-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="e4302-119">\<bufferSize>Windows. ApplicationServer. Applications. Man dosyasındaki değeri 32 olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e4302-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="e4302-120">Şu komutu geçerli çerçeve dizininde yürütün (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="e4302-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4302-121">.NET Framework 4 Istemci profilini kullanıyorsanız, önce .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak ETW bildirimini kaydetmeniz gerekir: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="e4302-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="e4302-122">System. Diagnostics kullanarak hata ayıklama Izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e4302-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="e4302-123">Bu dinleyiciler, iş akışı uygulamasının App.config dosyasında veya bir iş akışı hizmeti için Web.config yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4302-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="e4302-124">Bu örnekte, <xref:System.Diagnostics.TextWriterTraceListener> izleme bilgilerini geçerli dizindeki MyTraceLog.txt dosyasına kaydedecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e4302-124">In this example, a <xref:System.Diagnostics.TextWriterTraceListener> is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4302-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4302-125">See also</span></span>

- <span data-ttu-id="e4302-126">[Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e4302-126">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="e4302-127">[App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e4302-127">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>

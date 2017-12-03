---
title: "İş akışı izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cc400c2925d1a4a1810780528bad6da3ad492eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-tracing"></a><span data-ttu-id="47c47-102">İş akışı izleme</span><span class="sxs-lookup"><span data-stu-id="47c47-102">Workflow Tracing</span></span>
<span data-ttu-id="47c47-103">İş akışı izleme .NET Framework izleme dinleyicilerini kullanarak tanılama bilgileri yakalamak için bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="47c47-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="47c47-104">İzleme uygulama ile ilgili bir sorun algılandığında, etkin ve sorun çözüldükten sonra yeniden devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="47c47-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="47c47-105">İş akışları için hata ayıklama izlemeyi etkinleştirebilir iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="47c47-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="47c47-106">Olay İzleme Görüntüleyicisi'ni kullanarak yapılandırabilirsiniz ya da kullanabilirsiniz <xref:System.Diagnostics> izleme olayları bir dosya göndermek için.</span><span class="sxs-lookup"><span data-stu-id="47c47-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="47c47-107">ETW İzleme hata ayıklama etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="47c47-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="47c47-108">ETW kullanarak izlemeyi etkinleştirmek için Olay Görüntüleyicisi'ndeki Debug kanal etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="47c47-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1.  <span data-ttu-id="47c47-109">Çok analitik gidin ve günlükleri düğümü Olay Görüntüleyicisi'ndeki debug.</span><span class="sxs-lookup"><span data-stu-id="47c47-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2.  <span data-ttu-id="47c47-110">Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="47c47-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="47c47-111">Sağ **uygulama uygulamalarının** seçip **View'a Analitik ve hata ayıklama günlüklerini göster**.</span><span class="sxs-lookup"><span data-stu-id="47c47-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="47c47-112">Sağ **hata ayıklama** seçip **günlüğü etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="47c47-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3.  <span data-ttu-id="47c47-113">Bir iş akışı debug çalıştırdığında ve izlemeleri ETW hata ayıklama kanala gösterilen Olay Görüntüleyicisi'nde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="47c47-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="47c47-114">Gidin **Olay Görüntüleyicisi -> uygulamalar ve hizmet günlükleri -> Microsoft -> Windows -> Uygulama uygulamalarının**.</span><span class="sxs-lookup"><span data-stu-id="47c47-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="47c47-115">Sağ **hata ayıklama** seçip **yenileme**.</span><span class="sxs-lookup"><span data-stu-id="47c47-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4.  <span data-ttu-id="47c47-116">Yalnızca 4 kilobayt (KB); varsayılan çözümleme izleme arabellek boyutu değil 32 KB boyutunu artırmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="47c47-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="47c47-117">Bunu yapmak için aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="47c47-117">To do this, perform the following steps.</span></span>  
  
    1.  <span data-ttu-id="47c47-118">Geçerli framework dizinde (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203) şu komutu çalıştırın:`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="47c47-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2.  <span data-ttu-id="47c47-119">Değişiklik \<bufferSize > 32 Windows.ApplicationServer.Applications.man dosyasındaki değeri.</span><span class="sxs-lookup"><span data-stu-id="47c47-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  <span data-ttu-id="47c47-120">Geçerli framework dizinde (örneğin, C:\Windows\Microsoft.NET\Framework\v4.0.21203) şu komutu çalıştırın:`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="47c47-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47c47-121">.NET Framework 4 istemci profili kullanıyorsanız, önce ETW bildirimi .NET Framework 4 dizininden aşağıdaki komutu çalıştırarak kaydetmeniz gerekir:`ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="47c47-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="47c47-122">Hata ayıklama System.Diagnostics kullanarak izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="47c47-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="47c47-123">Bu dinleyicileri bir iş akışı hizmeti için iş akışı uygulamanın Web.config veya App.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="47c47-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="47c47-124">Bu örnekte, bir [olmalıdır](http://go.microsoft.com/fwlink/?LinkId=165424) MyTraceLog.txt dosyası geçerli dizinde izleme bilgilerini kaydetmek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="47c47-124">In this example, a [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47c47-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47c47-125">See Also</span></span>  
 [<span data-ttu-id="47c47-126">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="47c47-126">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="47c47-127">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="47c47-127">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)

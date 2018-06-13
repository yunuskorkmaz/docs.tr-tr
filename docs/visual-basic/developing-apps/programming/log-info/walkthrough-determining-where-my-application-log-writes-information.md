---
title: My.Application.Log bilgileri (Visual Basic) nereye yazdığını belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: fa177fa1f07c52d900f57e5bf61c967f06203c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590939"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="d45f0-102">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d45f0-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="d45f0-103">`My.Application.Log` Nesne için birden fazla günlük dinleyicileri bilgileri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d45f0-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="d45f0-104">Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyasına göre geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="d45f0-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="d45f0-105">Bu konu varsayılan ayarları ve uygulamanızın ayarlarını belirleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="d45f0-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="d45f0-106">Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz: [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="d45f0-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="d45f0-107">My.Application.Log dinleyicileri belirlemek için</span><span class="sxs-lookup"><span data-stu-id="d45f0-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="d45f0-108">Derlemenin yapılandırma dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="d45f0-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="d45f0-109">Derleme geliştiriyorsanız, app.config dosyasında Visual Studio'dan erişebilirsiniz **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="d45f0-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="d45f0-110">Aksi durumda yapılandırma dosyasının adını ".config" ile eklenen derlemenin adıdır ve derleme aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d45f0-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d45f0-111">Her derlemesi bir yapılandırma dosyası içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d45f0-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="d45f0-112">Yapılandırma dosyasını bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d45f0-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="d45f0-113">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d45f0-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="d45f0-114">`<sources>` Bölüm bulunduğu `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d45f0-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="d45f0-115">Bu bölümler mevcut sonra bilgisayarın yapılandırma dosyasını yapılandırabilir `My.Application.Log` günlük dinleyicileri.</span><span class="sxs-lookup"><span data-stu-id="d45f0-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="d45f0-116">Aşağıdaki adımlar, hangi bilgisayar yapılandırma dosyası tanımlar belirlemek açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="d45f0-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="d45f0-117">Bilgisayarın machine.config dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="d45f0-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="d45f0-118">Genellikle, bulunur *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizin, burada `SystemRoot` işletim sistemi dizindir ve `frameworkVersion` sürümü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d45f0-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="d45f0-119">Machine.config ayarlarında, bir uygulamanın yapılandırma dosyasına göre geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="d45f0-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="d45f0-120">Aşağıda listelenen isteğe bağlı öğeleri yoksa, bunları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d45f0-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="d45f0-121">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d45f0-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="d45f0-122">Bu bölümler yoksa sonra `My.Application.Log` yalnızca varsayılan günlük dinleyicileri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d45f0-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="d45f0-123">Bulun <`add>` öğelerinde <`listeners>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d45f0-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="d45f0-124">Bu öğeler için adlandırılmış günlük dinleyicileri eklemek `My.Application.Log` kaynak.</span><span class="sxs-lookup"><span data-stu-id="d45f0-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="d45f0-125">Bulun `<add>` öğeleri günlük dinleyicileri adlarıyla `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d45f0-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="d45f0-126">Paylaşılan dinleyiciler birçok türleri için dinleyici'nın başlatma verileri nerede verileri dinleyicisi yönlendirir açıklaması şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d45f0-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="d45f0-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyicisi giriş açıklandığı gibi bir dosyayı günlüğe yazar.</span><span class="sxs-lookup"><span data-stu-id="d45f0-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="d45f0-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyicisi tarafından belirtilen bilgisayarda olay günlüğü için bilgi Yazar `initializeData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d45f0-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="d45f0-129">Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="d45f0-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="d45f0-130">Daha fazla bilgi için bkz: [.NET Framework'te ETW olayları](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="d45f0-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
    -   <span data-ttu-id="d45f0-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyicileri yazma belirtilen dosyaya `initializeData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d45f0-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="d45f0-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyicisi komut satırı konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="d45f0-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="d45f0-133">Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu tür belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="d45f0-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45f0-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d45f0-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [<span data-ttu-id="d45f0-135">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="d45f0-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="d45f0-136">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="d45f0-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="d45f0-137">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="d45f0-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="d45f0-138">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d45f0-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="d45f0-139">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="d45f0-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)  
 [<span data-ttu-id="d45f0-140">Sorun Giderme: Günlük Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="d45f0-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

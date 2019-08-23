---
title: My. Application. log bilgisinin nereden yazabileceğini belirleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 305c29e33f6cd421f39004e09d27c75b02ba8354
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912551"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="9215c-102">İzlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9215c-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="9215c-103">Nesnesi `My.Application.Log` , çeşitli günlük dinleyicilerine bilgi yazabilir.</span><span class="sxs-lookup"><span data-stu-id="9215c-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="9215c-104">Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="9215c-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="9215c-105">Bu konu, varsayılan ayarları ve uygulamanızın ayarlarının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9215c-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="9215c-106">Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="9215c-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="9215c-107">My. Application. log için dinleyicileri belirleme</span><span class="sxs-lookup"><span data-stu-id="9215c-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="9215c-108">Derlemenin yapılandırma dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="9215c-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="9215c-109">Derlemeyi geliştiriyorsanız, **Çözüm Gezgini**Visual Studio 'da App. config dosyasına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9215c-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="9215c-110">Aksi takdirde, yapılandırma dosya adı ". config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9215c-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9215c-111">Her derlemenin bir yapılandırma dosyası yoktur.</span><span class="sxs-lookup"><span data-stu-id="9215c-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="9215c-112">Yapılandırma dosyası bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="9215c-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="9215c-113">Bölümünde yer `name` alan "DefaultSource"özniteliğinesahipbölümündebölümünübulun`<sources>`. `<listeners>` `<source>`</span><span class="sxs-lookup"><span data-stu-id="9215c-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="9215c-114">Bölümü, bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bulunur. `<sources>`</span><span class="sxs-lookup"><span data-stu-id="9215c-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="9215c-115">Bu bölümler yoksa, bilgisayarın yapılandırma dosyası `My.Application.Log` günlük dinleyicilerini yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="9215c-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="9215c-116">Aşağıdaki adımlarda, bilgisayar yapılandırma dosyasının neyi tanımladığı nasıl belirleneceği açıklanır:</span><span class="sxs-lookup"><span data-stu-id="9215c-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="9215c-117">Bilgisayarın Machine. config dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="9215c-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="9215c-118">Genellikle, *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, burada `SystemRoot` işletim sistemi dizinidir ve `frameworkVersion` .NET Framework sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="9215c-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="9215c-119">Machine. config dosyasındaki ayarlar bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="9215c-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="9215c-120">Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9215c-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="9215c-121">`<listeners>` Bölümündeki`name`bölümünde bulunan bölümündeki " `<configuration>` DefaultSource `<sources>` " özniteliği, bölümündeki en üst düzey bölümünde bulunan bölümü bulun. `<system.diagnostics>` `<source>`</span><span class="sxs-lookup"><span data-stu-id="9215c-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="9215c-122">Bu bölümler yoksa, `My.Application.Log` yalnızca varsayılan günlük dinleyicilerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9215c-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="9215c-123">`add>` <`listeners>` Bölümünde < öğelerini bulun.</span><span class="sxs-lookup"><span data-stu-id="9215c-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="9215c-124">Bu öğeler, kaynak için `My.Application.Log` adlandırılmış günlük dinleyicileri ekler.</span><span class="sxs-lookup"><span data-stu-id="9215c-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="9215c-125">Bölümünde, üst düzey `<system.diagnostics>` `<sharedListeners>` bölümündekibölümünde`<configuration>` bulunan günlük dinleyicilerinin adlarını içeren `<add>` öğeleri bulun.</span><span class="sxs-lookup"><span data-stu-id="9215c-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="9215c-126">Birçok türdeki paylaşılan dinleyici için, dinleyicinin başlatma verileri, dinleyicinin verileri nerede yönlendirdiği hakkında bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="9215c-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="9215c-127">Bir <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, giriş bölümünde açıklandığı gibi bir dosya günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="9215c-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="9215c-128">Bir <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyici, `initializeData` parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="9215c-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="9215c-129">Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9215c-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="9215c-130">Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9215c-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="9215c-131">`initializeData` Ve <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> dinleyicileri,parametresinde<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="9215c-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="9215c-132">Bir <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyici, komut satırı konsoluna yazar.</span><span class="sxs-lookup"><span data-stu-id="9215c-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="9215c-133">Diğer günlük dinleyicisi türlerinin yazma bilgileri hakkında daha fazla bilgi için, bu türün belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="9215c-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="9215c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9215c-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="9215c-135">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="9215c-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="9215c-136">Nasıl yapılır: Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="9215c-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="9215c-137">Nasıl yapılır: Yazma günlüğü Iletileri</span><span class="sxs-lookup"><span data-stu-id="9215c-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="9215c-138">İzlenecek yol: My. Application. log dosyası yazma bilgilerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="9215c-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="9215c-139">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="9215c-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="9215c-140">Sorun giderme: Günlük dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="9215c-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

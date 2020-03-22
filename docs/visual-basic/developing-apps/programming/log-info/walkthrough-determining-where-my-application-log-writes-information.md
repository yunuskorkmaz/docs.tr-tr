---
title: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353600"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="3c076-102">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c076-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="3c076-103">Nesne `My.Application.Log` birkaç günlük dinleyiciye bilgi yazabilir.</span><span class="sxs-lookup"><span data-stu-id="3c076-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="3c076-104">Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="3c076-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="3c076-105">Bu konu varsayılan ayarları ve uygulamanızın ayarlarını nasıl belirleyirinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="3c076-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="3c076-106">Varsayılan çıktı konumları hakkında daha fazla bilgi için Bkz. [Uygulama Günlükleri ile Çalışma.](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)</span><span class="sxs-lookup"><span data-stu-id="3c076-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="3c076-107">My.Application.Log için dinleyici belirlemek için</span><span class="sxs-lookup"><span data-stu-id="3c076-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="3c076-108">Derlemenin yapılandırma dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="3c076-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="3c076-109">Montajı geliştiriyorsanız, Visual Studio'daki app.config'e **Solution Explorer'dan**erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c076-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="3c076-110">Aksi takdirde, yapılandırma dosya adı ".config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3c076-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3c076-111">Her derlemenin bir yapılandırma dosyası yok.</span><span class="sxs-lookup"><span data-stu-id="3c076-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="3c076-112">Yapılandırma dosyası bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3c076-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="3c076-113">Bölümde bulunan "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümdeki bölümü bulun. `<listeners>` `<sources>`</span><span class="sxs-lookup"><span data-stu-id="3c076-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="3c076-114">Bölüm, `<sources>` üst düzey `<system.diagnostics>` `<configuration>` bölümde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c076-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="3c076-115">Bu bölümler yoksa, bilgisayarın yapılandırma dosyası günlük dinleyicilerini `My.Application.Log` yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="3c076-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="3c076-116">Aşağıdaki adımlar, bilgisayar yapılandırma dosyasının tanımladığı nı nasıl belirleyeceklerini açıklar:</span><span class="sxs-lookup"><span data-stu-id="3c076-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="3c076-117">Bilgisayarın makinesinin bulunduğu config dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="3c076-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="3c076-118">Genellikle *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, işletim sistemi `SystemRoot` dizininin bulunduğu yerdir ve `frameworkVersion` .NET Framework'ün sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="3c076-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="3c076-119">machine.config'deki ayarlar, bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="3c076-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="3c076-120">Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c076-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="3c076-121">`<listeners>` "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümdeki bölümü, `<sources>` `<system.diagnostics>` bölümdeki, üst düzey `<configuration>` bölümdeki bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="3c076-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="3c076-122">Bu bölümler yoksa, yalnızca `My.Application.Log` varsayılan günlük dinleyicileri vardır.</span><span class="sxs-lookup"><span data-stu-id="3c076-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="3c076-123"><`add>` `listeners>` bölümündeki <öğeleri bulun.</span><span class="sxs-lookup"><span data-stu-id="3c076-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="3c076-124">Bu öğeler, adı geçen `My.Application.Log` günlük dinleyicilerini kaynağa ekler.</span><span class="sxs-lookup"><span data-stu-id="3c076-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="3c076-125">Bölümdeki, `<system.diagnostics>` üst düzey `<configuration>` bölümde, günlük dinleyicilerinin adlarını içeren `<add>` öğeleri bulun. `<sharedListeners>`</span><span class="sxs-lookup"><span data-stu-id="3c076-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="3c076-126">Birçok paylaşılan dinleyici türü için dinleyicinin başlangıç verileri, dinleyicinin verileri nereye yönlendirdiğinin açıklamasını içerir:</span><span class="sxs-lookup"><span data-stu-id="3c076-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="3c076-127">Bir <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, girişte açıklandığı gibi bir dosya günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="3c076-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="3c076-128">Dinleyici, <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> `initializeData` parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="3c076-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="3c076-129">Bir olay günlüğünü görüntülemek için **Server Explorer** veya Windows **Event Viewer'ı**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c076-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="3c076-130">Daha fazla bilgi için [.NET Framework'deki ETW Olayları'na](../../../../framework/performance/etw-events.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3c076-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="3c076-131">Ve <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyiciler parametrede belirtilen `initializeData` dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="3c076-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="3c076-132">Dinleyici <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> komut satırı konsoluna yazar.</span><span class="sxs-lookup"><span data-stu-id="3c076-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="3c076-133">Diğer günlük dinleyici türlerinin nerede bilgi yazdıkları hakkında bilgi için, bu türbelgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="3c076-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c076-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c076-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="3c076-135">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="3c076-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="3c076-136">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="3c076-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="3c076-137">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="3c076-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="3c076-138">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3c076-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="3c076-139">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="3c076-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="3c076-140">Sorun Giderme: Günlük Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="3c076-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

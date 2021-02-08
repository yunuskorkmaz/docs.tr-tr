---
description: 'Daha fazla bilgi edinin: Izlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme (Visual Basic)'
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
ms.openlocfilehash: 4ddb5777bcbdde07069efd2fd3a66f0c220ee135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792290"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="73245-103">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73245-103">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="73245-104">`My.Application.Log`Nesnesi, çeşitli günlük dinleyicilerine bilgi yazabilir.</span><span class="sxs-lookup"><span data-stu-id="73245-104">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="73245-105">Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="73245-105">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="73245-106">Bu konu, varsayılan ayarları ve uygulamanızın ayarlarının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73245-106">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="73245-107">Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="73245-107">For more information about the default output locations, see [Working with Application Logs](working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="73245-108">My. Application. log için dinleyicileri belirleme</span><span class="sxs-lookup"><span data-stu-id="73245-108">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="73245-109">Derlemenin yapılandırma dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="73245-109">Locate the assembly's configuration file.</span></span> <span data-ttu-id="73245-110">Derlemeyi geliştiriyorsanız, **Çözüm Gezgini** Visual Studio 'daki app.config erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73245-110">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="73245-111">Aksi takdirde, yapılandırma dosya adı ". config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="73245-111">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="73245-112">Her derlemenin bir yapılandırma dosyası yoktur.</span><span class="sxs-lookup"><span data-stu-id="73245-112">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="73245-113">Yapılandırma dosyası bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="73245-113">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="73245-114">Bölümünde `<listeners>` `<source>` `name` yer alan "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="73245-114">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="73245-115">Bölümü, bölümünde `<sources>` `<system.diagnostics>` , üst düzey `<configuration>` bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="73245-115">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="73245-116">Bu bölümler yoksa, bilgisayarın yapılandırma dosyası `My.Application.Log` günlük dinleyicilerini yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="73245-116">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="73245-117">Aşağıdaki adımlarda, bilgisayar yapılandırma dosyasının neyi tanımladığı nasıl belirleneceği açıklanır:</span><span class="sxs-lookup"><span data-stu-id="73245-117">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="73245-118">Bilgisayarın machine.config dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="73245-118">Locate the computer's machine.config file.</span></span> <span data-ttu-id="73245-119">Genellikle, *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, burada `SystemRoot` işletim sistemi dizinidir ve `frameworkVersion` .NET Framework sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="73245-119">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="73245-120">machine.config ayarları, bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="73245-120">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="73245-121">Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73245-121">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="73245-122">Bölümündeki bölümünde bulunan bölümündeki `<listeners>` `<source>` `name` "DefaultSource" özniteliği, bölümündeki `<sources>` `<system.diagnostics>` en üst düzey `<configuration>` bölümünde bulunan bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="73245-122">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="73245-123">Bu bölümler yoksa, `My.Application.Log` yalnızca varsayılan günlük dinleyicilerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73245-123">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="73245-124">`add>`<bölümünde <öğelerini bulun `listeners>` .</span><span class="sxs-lookup"><span data-stu-id="73245-124">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="73245-125">Bu öğeler, kaynak için adlandırılmış günlük dinleyicileri ekler `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="73245-125">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="73245-126">Bölümünde, `<add>` `<sharedListeners>` `<system.diagnostics>` üst düzey bölümündeki bölümünde bulunan günlük dinleyicilerinin adlarını içeren öğeleri bulun `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="73245-126">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="73245-127">Birçok türdeki paylaşılan dinleyici için, dinleyicinin başlatma verileri, dinleyicinin verileri nerede yönlendirdiği hakkında bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="73245-127">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="73245-128">Bir <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, giriş bölümünde açıklandığı gibi bir dosya günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="73245-128">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="73245-129">Bir <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyici, parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi Yazar `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="73245-129">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="73245-130">Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73245-130">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="73245-131">Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="73245-131">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="73245-132"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyicileri, parametresinde belirtilen dosyaya yazar `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="73245-132">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="73245-133">Bir <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyici, komut satırı konsoluna yazar.</span><span class="sxs-lookup"><span data-stu-id="73245-133">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="73245-134">Diğer günlük dinleyicisi türlerinin yazma bilgileri hakkında daha fazla bilgi için, bu türün belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="73245-134">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="73245-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73245-135">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="73245-136">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="73245-136">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="73245-137">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="73245-137">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="73245-138">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="73245-138">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="73245-139">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="73245-139">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="73245-140">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="73245-140">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="73245-141">Sorun Giderme: Günlük Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="73245-141">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)

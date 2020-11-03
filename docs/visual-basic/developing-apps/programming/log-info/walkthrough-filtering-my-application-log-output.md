---
title: My.Application.Log Çıktısını Filtreleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: e77a56b2be33555bc02157c8e643ac655b083bc3
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282209"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="b275f-102">İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b275f-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="b275f-103">Bu izlenecek yol, nesneden `My.Application.Log` dinleyicilerine hangi bilgilerin geçtiğini `Log` ve hangi bilgilerin dinleyiciler tarafından yazıldığını denetlemek için nesnenin varsayılan günlük filtrelemesinin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b275f-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="b275f-104">Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığından, uygulamayı oluşturduktan sonra bile günlüğe kaydetme davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b275f-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="b275f-105">Başlarken</span><span class="sxs-lookup"><span data-stu-id="b275f-105">Getting Started</span></span>

<span data-ttu-id="b275f-106">Yazan her ileti `My.Application.Log` , bir ilişkili önem düzeyine sahiptir ve bu da filtreleme mekanizmalarının günlük çıkışını denetlemek için kullandığı bir önem düzeyi vardır</span><span class="sxs-lookup"><span data-stu-id="b275f-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="b275f-107">Bu örnek uygulama `My.Application.Log` , farklı önem düzeylerindeki çeşitli günlük iletilerini yazmak için yöntemler kullanır.</span><span class="sxs-lookup"><span data-stu-id="b275f-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="b275f-108">Örnek uygulamayı derlemek için</span><span class="sxs-lookup"><span data-stu-id="b275f-108">To build the sample application</span></span>

1. <span data-ttu-id="b275f-109">Yeni bir Visual Basic Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="b275f-109">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="b275f-110">Form1 adına button1 adlı bir düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b275f-110">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="b275f-111"><xref:System.Windows.Forms.Control.Click>Button1 için olay işleyicisinde aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b275f-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="b275f-112">Uygulamayı hata ayıklayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b275f-112">Run the application in the debugger.</span></span>

5. <span data-ttu-id="b275f-113">**Button1** 'e basın.</span><span class="sxs-lookup"><span data-stu-id="b275f-113">Press **Button1**.</span></span>

     <span data-ttu-id="b275f-114">Uygulama, uygulamanın hata ayıklama çıktısına ve günlük dosyasına aşağıdaki bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="b275f-114">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="b275f-115">Uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="b275f-115">Close the application.</span></span>

     <span data-ttu-id="b275f-116">Uygulamanın hata ayıklama çıkış penceresini görüntüleme hakkında daha fazla bilgi için bkz. [Çıkış penceresi](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="b275f-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="b275f-117">Uygulamanın günlük dosyasının konumu hakkında daha fazla bilgi için bkz [. Walkthrough: My. Application. log bilgisinin nereden yazabileceğini belirleme](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="b275f-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b275f-118">Varsayılan olarak uygulama kapandığında günlük dosyası çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="b275f-118">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="b275f-119">Yukarıdaki örnekte, yöntemine yapılan ikinci çağrı ve yöntemine yapılan <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> çağrı <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> günlük çıktısını üretir, ancak yöntemin ilk ve son çağrıları `WriteEntry` değildir.</span><span class="sxs-lookup"><span data-stu-id="b275f-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="b275f-120">Bunun nedeni, önem seviyelerinin `WriteEntry` `WriteException` "bilgi" ve "hata" olmasına ve her ikisinin de `My.Application.Log` nesnenin varsayılan günlük filtrelemesine izin verdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b275f-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="b275f-121">Bununla birlikte, "Başlat" ve "Durdur" önem derecesindeki olaylar günlük çıktısı üretmesinin engellenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b275f-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="b275f-122">Tüm My. Application. log dinleyicileri için filtreleme</span><span class="sxs-lookup"><span data-stu-id="b275f-122">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="b275f-123">`My.Application.Log`Nesnesi <xref:System.Diagnostics.SourceSwitch> `DefaultSwitch` , `WriteEntry` ve yöntemlerinden hangi iletilerin günlük dinleyicilerine geçireceğini denetlemek için adlandırılmış bir kullanır `WriteException` .</span><span class="sxs-lookup"><span data-stu-id="b275f-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="b275f-124">`DefaultSwitch`Değerini sabit listesi değerlerinden birine ayarlayarak uygulamanın yapılandırma dosyasında yapılandırabilirsiniz <xref:System.Diagnostics.SourceLevels> .</span><span class="sxs-lookup"><span data-stu-id="b275f-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="b275f-125">Varsayılan olarak, değeri "bilgi" ' dir.</span><span class="sxs-lookup"><span data-stu-id="b275f-125">By default, its value is "Information".</span></span>

<span data-ttu-id="b275f-126">Bu tablo, belirli bir ayar için, günlüğe kaydedilecek bir ileti yazmak için gereken önem derecesini gösterir `DefaultSwitch` .</span><span class="sxs-lookup"><span data-stu-id="b275f-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="b275f-127">DefaultSwitch değeri</span><span class="sxs-lookup"><span data-stu-id="b275f-127">DefaultSwitch Value</span></span>|<span data-ttu-id="b275f-128">Çıkış için gereken ileti önem derecesi</span><span class="sxs-lookup"><span data-stu-id="b275f-128">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="b275f-129">`Critical` veya `Error`</span><span class="sxs-lookup"><span data-stu-id="b275f-129">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="b275f-130">`Critical`, `Error` , veya `Warning`</span><span class="sxs-lookup"><span data-stu-id="b275f-130">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="b275f-131">`Critical`, `Error` , `Warning` veya `Information`</span><span class="sxs-lookup"><span data-stu-id="b275f-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="b275f-132">`Critical`,,, `Error` `Warning` `Information` veya `Verbose`</span><span class="sxs-lookup"><span data-stu-id="b275f-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="b275f-133">`Start`,,, `Stop` `Suspend` `Resume` veya `Transfer`</span><span class="sxs-lookup"><span data-stu-id="b275f-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="b275f-134">Tüm iletilere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="b275f-134">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="b275f-135">Tüm iletiler engellenir.</span><span class="sxs-lookup"><span data-stu-id="b275f-135">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="b275f-136">`WriteEntry`Ve `WriteException` yöntemlerinin her biri önem düzeyi belirtmeyen bir aşırı yüklemeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b275f-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="b275f-137">Aşırı yükleme için örtülü önem düzeyi `WriteEntry` "bilgi" ve aşırı yükleme için örtülü önem düzeyi `WriteException` "hata" dır.</span><span class="sxs-lookup"><span data-stu-id="b275f-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="b275f-138">Bu tabloda, önceki örnekte gösterilen günlük çıktısı açıklanmaktadır: varsayılan `DefaultSwitch` "bilgi" ayarıyla, yönteme yalnızca ikinci çağrı `WriteEntry` ve yönteme yapılan çağrı `WriteException` günlük çıkışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b275f-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="b275f-139">Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="b275f-139">To log only activity tracing events</span></span>

1. <span data-ttu-id="b275f-140">**Çözüm Gezgini** app.config sağ tıklayın ve **Aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="b275f-141">-veya-</span><span class="sxs-lookup"><span data-stu-id="b275f-141">-or-</span></span>

     <span data-ttu-id="b275f-142">app.config dosya yoksa:</span><span class="sxs-lookup"><span data-stu-id="b275f-142">If there is no app.config file:</span></span>

    1. <span data-ttu-id="b275f-143">**Proje** menüsünde **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-143">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="b275f-144">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="b275f-145">**Ekle** 'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b275f-145">Click **Add**.</span></span>

2. <span data-ttu-id="b275f-146">`<switches>`Üst düzey bölümde bulunan bölümünde olan bölümünü bulun `<system.diagnostics>` `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="b275f-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="b275f-147">Anahtarlar koleksiyonuna ekleyen öğeyi bulun `DefaultSwitch` .</span><span class="sxs-lookup"><span data-stu-id="b275f-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="b275f-148">Bu öğe şuna benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="b275f-148">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="b275f-149">`value`Özniteliğin değerini "ActivityTracing" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b275f-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="b275f-150">app.config dosyasının içeriği aşağıdaki XML 'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b275f-150">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. <span data-ttu-id="b275f-151">Uygulamayı hata ayıklayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b275f-151">Run the application in the debugger.</span></span>

7. <span data-ttu-id="b275f-152">**Button1** 'e basın.</span><span class="sxs-lookup"><span data-stu-id="b275f-152">Press **Button1**.</span></span>

     <span data-ttu-id="b275f-153">Uygulama aşağıdaki bilgileri uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazar:</span><span class="sxs-lookup"><span data-stu-id="b275f-153">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="b275f-154">Uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="b275f-154">Close the application.</span></span>

9. <span data-ttu-id="b275f-155">`value`Özniteliğin değerini "Information" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b275f-155">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="b275f-156">`DefaultSwitch`Yalnızca anahtar ayarı denetimleri `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b275f-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="b275f-157">.NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfların nasıl davranacağını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="b275f-157">It does not change how the .NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="b275f-158">My. Application. log dinleyicileri Için bireysel filtreleme</span><span class="sxs-lookup"><span data-stu-id="b275f-158">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="b275f-159">Önceki örnekte, tüm çıktılar için filtrelemenin nasıl değiştirileceği gösterilmektedir `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b275f-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="b275f-160">Bu örnek, tek bir günlük dinleyicisinin nasıl filtreleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b275f-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="b275f-161">Varsayılan olarak, uygulamanın, uygulamanın hata ayıklama çıktısına ve günlük dosyasına yazan iki dinleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="b275f-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="b275f-162">Yapılandırma dosyası, her birinin bir filtreye benzer bir filtreye sahip olmasını sağlayarak günlük dinleyicilerinin davranışını denetler `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b275f-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="b275f-163">Günlük dinleyicisi yalnızca, iletinin önem derecesine yalnızca günlüğün `DefaultSwitch` ve günlük dinleyicinin filtresi tarafından izin veriliyorsa bir ileti çıktı.</span><span class="sxs-lookup"><span data-stu-id="b275f-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="b275f-164">Bu örnek, yeni bir hata ayıklama dinleyicisi için filtrelemenin nasıl yapılandırılacağını ve nesneye nasıl ekleneceğini gösterir `Log` .</span><span class="sxs-lookup"><span data-stu-id="b275f-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="b275f-165">Varsayılan hata ayıklama dinleyicisi `Log` nesnesinden kaldırılmalıdır, bu nedenle hata ayıklama iletilerinin yeni hata ayıklama dinleyicisinden geldiği temizlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b275f-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="b275f-166">Yalnızca etkinlik izleme olaylarını günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="b275f-166">To log only activity-tracing events</span></span>

1. <span data-ttu-id="b275f-167">**Çözüm Gezgini** app.config sağ tıklayın ve **Aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="b275f-168">\-veya</span><span class="sxs-lookup"><span data-stu-id="b275f-168">\-or-</span></span>

     <span data-ttu-id="b275f-169">app.config dosya yoksa:</span><span class="sxs-lookup"><span data-stu-id="b275f-169">If there is no app.config file:</span></span>

    1. <span data-ttu-id="b275f-170">**Proje** menüsünde **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-170">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="b275f-171">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="b275f-172">**Ekle** 'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b275f-172">Click **Add**.</span></span>

2. <span data-ttu-id="b275f-173">**Çözüm Gezgini** app.config sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b275f-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="b275f-174">**Aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b275f-174">Choose **Open**.</span></span>

3. <span data-ttu-id="b275f-175">Bölümünün `<listeners>` `<source>` altında bulunan `name` "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="b275f-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="b275f-176">`<sources>`Bölümü, `<system.diagnostics>` bölümünün üst düzey bölümünde yer aldığı bölümdür `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="b275f-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="b275f-177">Bu öğeyi `<listeners>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b275f-177">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="b275f-178">Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="b275f-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="b275f-179">Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="b275f-179">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     <span data-ttu-id="b275f-180"><xref:System.Diagnostics.EventTypeFilter>Filtre, <xref:System.Diagnostics.SourceLevels> sabit listesi değerlerinden birini özniteliği olarak alır `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="b275f-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="b275f-181">app.config dosyasının içeriği aşağıdaki XML 'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b275f-181">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. <span data-ttu-id="b275f-182">Uygulamayı hata ayıklayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b275f-182">Run the application in the debugger.</span></span>

9. <span data-ttu-id="b275f-183">**Button1** 'e basın.</span><span class="sxs-lookup"><span data-stu-id="b275f-183">Press **Button1**.</span></span>

     <span data-ttu-id="b275f-184">Uygulama, uygulamanın günlük dosyasına aşağıdaki bilgileri yazar:</span><span class="sxs-lookup"><span data-stu-id="b275f-184">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="b275f-185">Uygulama daha kısıtlayıcı filtreleme nedeniyle uygulamanın hata ayıklama çıktısına daha az bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="b275f-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="b275f-186">Uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="b275f-186">Close the application.</span></span>

<span data-ttu-id="b275f-187">Dağıtımdan sonra günlük ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="b275f-187">For more information about changing log settings after deployment, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b275f-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b275f-188">See also</span></span>

- [<span data-ttu-id="b275f-189">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="b275f-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="b275f-190">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b275f-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="b275f-191">İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b275f-191">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="b275f-192">Nasıl yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="b275f-192">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="b275f-193">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="b275f-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="b275f-194">Uygulamadan Günlüğe Bilgi Kaydetme</span><span class="sxs-lookup"><span data-stu-id="b275f-194">Logging Information from the Application</span></span>](index.md)

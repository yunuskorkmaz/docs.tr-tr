---
title: "Filtreleme My.Application.Log çıktısını (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fd445227e0c8290ad63fccf807d6d7bdf43ccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="02514-102">İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02514-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="02514-103">Bu anlatımda için filtreleme varsayılan günlük değiştirmek nasıl gösterilir `My.Application.Log` hangi bilgilerin gelen geçirilen denetlemek için nesne `Log` nesne dinleyicileri ve hangi bilgilerin dinleyicileri tarafından yazılır.</span><span class="sxs-lookup"><span data-stu-id="02514-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="02514-104">Yapılandırma bilgileri uygulamanın yapılandırma dosyasında depolandığı için bile uygulama oluşturduktan sonra günlüğe kaydetme davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02514-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="02514-105">Başlarken</span><span class="sxs-lookup"><span data-stu-id="02514-105">Getting Started</span></span>  
 <span data-ttu-id="02514-106">Her ileti `My.Application.Log` yazma hangi filtreleme mekanizması kullanıyor günlük çıktısı denetlemek için bir ilişkili önem düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="02514-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="02514-107">Bu örnek uygulama kullanır `My.Application.Log` birkaç yazma yöntemleri farklı önem düzeyleri ile iletileri günlüğe.</span><span class="sxs-lookup"><span data-stu-id="02514-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="02514-108">Örnek uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="02514-108">To build the sample application</span></span>  
  
1.  <span data-ttu-id="02514-109">Yeni bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows uygulama projesi.</span><span class="sxs-lookup"><span data-stu-id="02514-109">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="02514-110">Form1 button1 adlı bir düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02514-110">Add a button named Button1 to Form1.</span></span>  
  
3.  <span data-ttu-id="02514-111">İçinde <xref:System.Windows.Forms.Control.Click> Button1, olay işleyicisi aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="02514-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  <span data-ttu-id="02514-112">Hata ayıklayıcıda uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02514-112">Run the application in the debugger.</span></span>  
  
5.  <span data-ttu-id="02514-113">Tuşuna **Button1**.</span><span class="sxs-lookup"><span data-stu-id="02514-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="02514-114">Uygulama, aşağıdaki bilgileri uygulamanın hata ayıklama çıktı ve günlük dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="02514-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  <span data-ttu-id="02514-115">Uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="02514-115">Close the application.</span></span>  
  
     <span data-ttu-id="02514-116">Uygulamanın hata ayıklama çıktı penceresini görüntüleme hakkında daha fazla bilgi için bkz: [çıktı penceresi](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="02514-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="02514-117">Uygulamanın günlük dosyasının konumunu hakkında daha fazla bilgi için bkz: [izlenecek yol: belirleme nerede My.Application.Log Yazar bilgisini](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="02514-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02514-118">Uygulama kapandığında varsayılan olarak, günlük dosyası çıkış uygulama aktarır.</span><span class="sxs-lookup"><span data-stu-id="02514-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="02514-119">İkinci çağrısı yukarıdaki örnekte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> yöntemi ve çağrısı <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> yöntem ilk ve son çağrı sırasında günlük çıkışı üretir `WriteEntry` yöntemi yoktur.</span><span class="sxs-lookup"><span data-stu-id="02514-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="02514-120">Bunun nedeni, önem derecesi düzeyleri `WriteEntry` ve `WriteException` "Bilgi" ve "Error" her ikisi de izin `My.Application.Log` nesnenin günlük filtreleme varsayılan.</span><span class="sxs-lookup"><span data-stu-id="02514-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="02514-121">Ancak, "Başlat" ve "Durdur" önem düzeyleri ile olayları günlük çıkış üretmeyi engellenir.</span><span class="sxs-lookup"><span data-stu-id="02514-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="02514-122">Tüm My.Application.Log dinleyicileri için filtreleme</span><span class="sxs-lookup"><span data-stu-id="02514-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="02514-123">`My.Application.Log` Nesne kullanan bir <xref:System.Diagnostics.SourceSwitch> adlı `DefaultSwitch` hangi geçişleri gelen iletileri denetlemek `WriteEntry` ve `WriteException` günlük dinleyicileri yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="02514-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="02514-124">Yapılandırabileceğiniz `DefaultSwitch` değerini biri olarak ayarlayarak uygulamanın yapılandırma dosyasında <xref:System.Diagnostics.SourceLevels> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="02514-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="02514-125">Varsayılan olarak, "Bilgi" değeri olduğu.</span><span class="sxs-lookup"><span data-stu-id="02514-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="02514-126">Bu tablo için belirli bir verilen dinleyicileri için bir ileti yazmak günlüğü gerekli önem derecesini gösterir `DefaultSwitch` ayarı.</span><span class="sxs-lookup"><span data-stu-id="02514-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="02514-127">DefaultSwitch değeri</span><span class="sxs-lookup"><span data-stu-id="02514-127">DefaultSwitch Value</span></span>|<span data-ttu-id="02514-128">Çıktı için gereken ileti önem derecesi</span><span class="sxs-lookup"><span data-stu-id="02514-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="02514-129">`Critical`veya`Error`</span><span class="sxs-lookup"><span data-stu-id="02514-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="02514-130">`Critical`, `Error`, veya`Warning`</span><span class="sxs-lookup"><span data-stu-id="02514-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="02514-131">`Critical`, `Error`, `Warning`, veya`Information`</span><span class="sxs-lookup"><span data-stu-id="02514-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="02514-132">`Critical`, `Error`, `Warning`, `Information`, veya`Verbose`</span><span class="sxs-lookup"><span data-stu-id="02514-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="02514-133">`Start`, `Stop`, `Suspend`, `Resume`, veya`Transfer`</span><span class="sxs-lookup"><span data-stu-id="02514-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="02514-134">Tüm iletileri izin verilir.</span><span class="sxs-lookup"><span data-stu-id="02514-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="02514-135">Tüm iletileri engellenir.</span><span class="sxs-lookup"><span data-stu-id="02514-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="02514-136">`WriteEntry` Ve `WriteException` yöntemlerinin her bir önem düzeyi belirtmeyen bir aşırı yüklü.</span><span class="sxs-lookup"><span data-stu-id="02514-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="02514-137">Örtük önem derecesini `WriteEntry` aşırı yüklemesi, "Bilgi" ve örtük önem derecesini `WriteException` aşırı yüklemesi, "Error".</span><span class="sxs-lookup"><span data-stu-id="02514-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="02514-138">Bu tabloda, önceki örnekte gösterilen günlük çıktısı açıklanmaktadır: varsayılan `DefaultSwitch` "Bilgi" ayarı, yalnızca ikinci çağrısı `WriteEntry` yöntemi ve çağrısı `WriteException` yöntemi ürettiği günlük çıktısı.</span><span class="sxs-lookup"><span data-stu-id="02514-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="02514-139">Yalnızca etkinlik izleme olayları günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="02514-139">To log only activity tracing events</span></span>  
  
1.  <span data-ttu-id="02514-140">App.config dosyasında sağ **Çözüm Gezgini** seçip **açık**.</span><span class="sxs-lookup"><span data-stu-id="02514-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="02514-141">veya</span><span class="sxs-lookup"><span data-stu-id="02514-141">-or-</span></span>  
  
     <span data-ttu-id="02514-142">Herhangi bir app.config dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="02514-142">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="02514-143">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="02514-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="02514-144">Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="02514-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="02514-145">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="02514-145">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="02514-146">Bulun `<switches>` bulunduğu bölüm `<system.diagnostics>` üst düzey olan bölüm `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="02514-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="02514-147">Ekler öğesi bulunamıyor `DefaultSwitch` anahtarları koleksiyonuna.</span><span class="sxs-lookup"><span data-stu-id="02514-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="02514-148">Bu öğeye benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="02514-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  <span data-ttu-id="02514-149">Değerini değiştirme `value` özniteliği "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="02514-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5.  <span data-ttu-id="02514-150">App.config dosyasının içeriğini aşağıdaki XML'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="02514-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
6.  <span data-ttu-id="02514-151">Hata ayıklayıcıda uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02514-151">Run the application in the debugger.</span></span>  
  
7.  <span data-ttu-id="02514-152">Tuşuna **Button1**.</span><span class="sxs-lookup"><span data-stu-id="02514-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="02514-153">Uygulama, aşağıdaki bilgileri uygulamanın hata ayıklama çıktı ve günlük dosyasına yazar:</span><span class="sxs-lookup"><span data-stu-id="02514-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  <span data-ttu-id="02514-154">Uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="02514-154">Close the application.</span></span>  
  
9. <span data-ttu-id="02514-155">Değerini değiştirme `value` özniteliğini geri "bilgileri için".</span><span class="sxs-lookup"><span data-stu-id="02514-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02514-156">`DefaultSwitch` Anahtar yalnızca ayarı denetimlerini `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="02514-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="02514-157">Değiştirme nasıl [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfları davranır.</span><span class="sxs-lookup"><span data-stu-id="02514-157">It does not change how the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="02514-158">Tek tek My.Application.Log dinleyicileri için filtreleme</span><span class="sxs-lookup"><span data-stu-id="02514-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="02514-159">Önceki örnekte tüm filtreleme değiştirileceği gösterilmektedir `My.Application.Log` çıktı.</span><span class="sxs-lookup"><span data-stu-id="02514-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="02514-160">Bu örnek, bir tek tek günlük dinleyicisi filtre gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="02514-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="02514-161">Varsayılan olarak, bir uygulama, yazma uygulamanın hata ayıklama çıktısı ve günlük dosyası için iki dinleyicileri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="02514-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="02514-162">Yapılandırma dosyası her biri bir anahtar için benzer bir filtre olmasını sağlayarak günlük dinleyicileri davranışını denetleyen `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="02514-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="02514-163">Yalnızca ileti önem derecesi hem günlüğün tarafından izin verilip verilmediğini günlük dinleyici bir çıktı mesajı göndereceğiz `DefaultSwitch` ve günlük dinleyicisi'nın Filtresi.</span><span class="sxs-lookup"><span data-stu-id="02514-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="02514-164">Bu örnek için yeni bir hata ayıklama dinleyici filtreleme yapılandırmak ve eklemek gösterilmiştir `Log` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="02514-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="02514-165">Varsayılan hata ayıklama dinleyicisi kaldırılmalı `Log` hata ayıklama iletileri yeni hata ayıklama dinleyicisi geldiğini açık olacak şekilde, nesne.</span><span class="sxs-lookup"><span data-stu-id="02514-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="02514-166">Yalnızca etkinlik izleme olaylarını günlüğe kaydedecek şekilde</span><span class="sxs-lookup"><span data-stu-id="02514-166">To log only activity-tracing events</span></span>  
  
1.  <span data-ttu-id="02514-167">App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.</span><span class="sxs-lookup"><span data-stu-id="02514-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="02514-168">veya</span><span class="sxs-lookup"><span data-stu-id="02514-168">-or-</span></span>  
  
     <span data-ttu-id="02514-169">Herhangi bir app.config dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="02514-169">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="02514-170">Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="02514-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="02514-171">Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.</span><span class="sxs-lookup"><span data-stu-id="02514-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="02514-172">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="02514-172">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="02514-173">App.config dosyasında sağ **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="02514-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="02514-174">Seçin **açık**.</span><span class="sxs-lookup"><span data-stu-id="02514-174">Choose **Open**.</span></span>  
  
3.  <span data-ttu-id="02514-175">Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` altındaki "DefaultSource" özniteliği `<sources>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="02514-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="02514-176">`<sources>` Bölümdür altında `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="02514-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4.  <span data-ttu-id="02514-177">Bu öğeye ekleyin `<listeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="02514-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  <span data-ttu-id="02514-178">Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="02514-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="02514-179">Bu öğe için eklemek `<sharedListeners>` bölümü:</span><span class="sxs-lookup"><span data-stu-id="02514-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
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
  
     <span data-ttu-id="02514-180"><xref:System.Diagnostics.EventTypeFilter> Filtresi birini gerçekleştirir <xref:System.Diagnostics.SourceLevels> numaralandırma değerleri olarak kendi `initializeData` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="02514-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7.  <span data-ttu-id="02514-181">App.config dosyasının içeriğini aşağıdaki XML'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="02514-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
8.  <span data-ttu-id="02514-182">Hata ayıklayıcıda uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02514-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="02514-183">Tuşuna **Button1**.</span><span class="sxs-lookup"><span data-stu-id="02514-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="02514-184">Uygulama, aşağıdaki bilgileri uygulamanın günlük dosyasına yazar:</span><span class="sxs-lookup"><span data-stu-id="02514-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="02514-185">Uygulama daha kısıtlayıcı filtreleme nedeniyle daha az bilgi için uygulamanın hata ayıklama çıktısı yazar.</span><span class="sxs-lookup"><span data-stu-id="02514-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="02514-186">Uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="02514-186">Close the application.</span></span>  
  
 <span data-ttu-id="02514-187">Dağıtımdan sonra günlük ayarları değiştirme hakkında daha fazla bilgi için bkz: [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="02514-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02514-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02514-188">See Also</span></span>  
 [<span data-ttu-id="02514-189">İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme</span><span class="sxs-lookup"><span data-stu-id="02514-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="02514-190">İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="02514-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="02514-191">İzlenecek yol: Özel günlük dinleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="02514-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [<span data-ttu-id="02514-192">Nasıl yapılır: günlük iletileri yazma</span><span class="sxs-lookup"><span data-stu-id="02514-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="02514-193">İzleme anahtarları</span><span class="sxs-lookup"><span data-stu-id="02514-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="02514-194">Uygulama içinden bilgileri günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="02514-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)

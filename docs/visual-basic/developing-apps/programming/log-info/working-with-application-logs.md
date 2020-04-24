---
title: Uygulama Günlükleriyle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345894"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="f1cd0-102">Visual Basic'te Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="f1cd0-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="f1cd0-103">`My.Application.Log` Ve `My.Log` nesneleri günlüğe kaydetme ve izleme bilgilerini günlüklere yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="f1cd0-104">Iletiler günlüğe nasıl kaydedilir?</span><span class="sxs-lookup"><span data-stu-id="f1cd0-104">How Messages are Logged</span></span>

<span data-ttu-id="f1cd0-105">İlk olarak, iletinin önem derecesi günlüğün <xref:System.Diagnostics.TraceSource.Switch%2A> <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> özelliğinin özelliği ile denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="f1cd0-106">Varsayılan olarak, günlük `TraceListener` koleksiyonunda belirtilen izleme dinleyicilerine yalnızca önem derecesi "bilgi" ve üzeri iletiler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="f1cd0-107">Ardından, her dinleyici iletinin önem derecesini dinleyicinin <xref:System.Diagnostics.TraceSource.Switch%2A> özelliği ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="f1cd0-108">İletinin önem derecesi yeterince yüksekse, dinleyici iletiyi yazar.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="f1cd0-109">Aşağıdaki diyagramda, `WriteEntry` yönteme yazılan bir iletinin günlüğün izleme dinleyicilerinin `WriteLine` yöntemlerine nasıl geçirildiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f1cd0-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Günlük çağrımı gösteren diyagram.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="f1cd0-111">Uygulamanın yapılandırma dosyasını değiştirerek günlük ve izleme dinleyicilerinin davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="f1cd0-112">Aşağıdaki diyagramda, günlüğün bölümleri ile yapılandırma dosyası arasındaki yazışma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Günlük yapılandırmanızın gösterildiği diyagram.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="f1cd0-114">Iletiler günlüğe kaydedilir</span><span class="sxs-lookup"><span data-stu-id="f1cd0-114">Where Messages are Logged</span></span>

<span data-ttu-id="f1cd0-115">Derlemenin yapılandırma dosyası yoksa, `My.Application.Log` ve `My.Log` nesneleri uygulamanın hata ayıklama çıktısına ( <xref:System.Diagnostics.DefaultTraceListener> sınıfı aracılığıyla) yazar.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="f1cd0-116">Ayrıca, `My.Application.Log` nesnesi derlemenin günlük dosyasına ( <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sınıfı aracılığıyla) yazar, `My.Log` nesne ASP.NET Web sayfasının çıktısına ( <xref:System.Web.WebPageTraceListener> sınıfı aracılığıyla) yazar.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="f1cd0-117">Hata ayıklama çıktısı, uygulamanızı hata ayıklama modunda çalıştırırken Visual Studio **çıktı** penceresinde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="f1cd0-118">**Çıkış** penceresini açmak Için, **Hata Ayıkla** menü öğesine tıklayın, **Windows**' ın üzerine gelin ve ardından **Çıkış**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="f1cd0-119">**Çıkış** penceresinde, **çıktıyı göster** kutusundan **Hata Ayıkla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="f1cd0-120">Varsayılan olarak, `My.Application.Log` günlük dosyasını kullanıcının uygulama verileri yoluna yazar.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="f1cd0-121"><xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> Nesnenin <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> özelliğinden yolunu alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="f1cd0-122">Yolun biçimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f1cd0-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="f1cd0-123">İçin `BasePath` tipik bir değer aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="f1cd0-124">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="f1cd0-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="f1cd0-125">`CompanyName`, `ProductName`Ve `ProductVersion` değerleri uygulamanın derleme bilgileriyle gelir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="f1cd0-126">Günlük dosyası adının biçimi *AssemblyName*. log biçimindedir, burada *AssemblyName* uzantısı olmayan derlemenin dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="f1cd0-127">Birden çok günlük dosyası gerekiyorsa (örneğin, uygulama günlüğe yazmaya çalıştığında özgün günlüğün kullanılamadığı durumlar gibi), günlük dosyası adı için form *AssemblyName*-*yineleme*. log ' dur ve burada `iteration` pozitif `Integer`olur.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="f1cd0-128">Bilgisayar ve uygulamanın yapılandırma dosyalarını ekleyerek veya değiştirerek varsayılan davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="f1cd0-129">Daha fazla bilgi için bkz [. Izlenecek yol: My. Application. log bilgisinin nereden yazabileceğini değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="f1cd0-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="f1cd0-130">Günlük ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1cd0-130">Configuring Log Settings</span></span>

<span data-ttu-id="f1cd0-131">`Log` Nesnesi, uygulama yapılandırma dosyası, App. config olmadan çalışacak varsayılan bir uygulamaya sahiptir. Varsayılanları değiştirmek için yeni ayarlara sahip bir yapılandırma dosyası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="f1cd0-132">Daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="f1cd0-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="f1cd0-133">Günlük yapılandırma bölümleri, App. config dosyasının `<system.diagnostics>` ana `<configuration>` düğümündeki düğümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="f1cd0-134">Günlük bilgileri çeşitli düğümlerde tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="f1cd0-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="f1cd0-135">`Log` Nesnenin dinleyicileri DefaultSource adlı `<sources>` düğümde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="f1cd0-136">`Log` Nesnesi için önem derecesi, DefaultSwitch adlı `<switches>` düğümde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="f1cd0-137">Günlük dinleyicileri, `<sharedListeners>` düğümde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="f1cd0-138">Aşağıdaki kodda `<sources>`, `<switches>`, ve `<sharedListeners>` düğümleri örnekleri gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1cd0-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="f1cd0-139">Dağıtımdan sonra günlük ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="f1cd0-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="f1cd0-140">Bir uygulama geliştirirken, yapılandırma ayarları Yukarıdaki örneklerde gösterildiği gibi App. config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="f1cd0-141">Uygulamanızı dağıttıktan sonra yapılandırma dosyasını düzenleyerek günlüğü yapılandırmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="f1cd0-142">Windows tabanlı bir uygulamada, bu dosyanın adı *ApplicationName*. exe. config olur ve yürütülebilir dosyayla aynı klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="f1cd0-143">Bir Web uygulaması için, bu, projeyle ilişkili Web. config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="f1cd0-144">Uygulamanız bir sınıfın bir örneğini ilk kez oluşturan kodu yürüttüğünde, nesne hakkında bilgi için yapılandırma dosyasını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="f1cd0-145">`Log` Nesnesi için, bu `Log` nesne ilk kez erişildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="f1cd0-146">Sistem, yapılandırma dosyasını belirli bir nesne için yalnızca bir kez inceler — uygulamanız nesneyi ilk kez oluşturduğunda.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="f1cd0-147">Bu nedenle, değişikliklerin etkili olması için uygulamayı yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="f1cd0-148">Dağıtılan bir uygulamada, uygulama başlamadan önce geçiş nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="f1cd0-149">Genellikle bu, anahtar nesnelerinin açık ve kapalı olduğunu ya da izleme düzeylerini değiştirerek ve sonra uygulamanızı yeniden başlatarak içerir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="f1cd0-150">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="f1cd0-150">Security Considerations</span></span>

<span data-ttu-id="f1cd0-151">Günlüğe veri yazarken aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f1cd0-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="f1cd0-152">**Kullanıcı bilgilerinin sızmasını önleyin.**</span><span class="sxs-lookup"><span data-stu-id="f1cd0-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="f1cd0-153">Uygulamanızın günlüğe yalnızca onaylanan bilgileri yazdığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="f1cd0-154">Örneğin, uygulama günlüğü Kullanıcı adlarını içermesi, ancak kullanıcı parolalarını içermemesi için kabul edilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="f1cd0-155">**Günlük konumlarını güvenli hale getirin.**</span><span class="sxs-lookup"><span data-stu-id="f1cd0-155">**Make log locations secure.**</span></span> <span data-ttu-id="f1cd0-156">Potansiyel olarak hassas bilgiler içeren herhangi bir günlüğün güvenli bir konumda depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="f1cd0-157">**Yanıltıcı bilgilerden kaçının.**</span><span class="sxs-lookup"><span data-stu-id="f1cd0-157">**Avoid misleading information.**</span></span> <span data-ttu-id="f1cd0-158">Genel olarak, uygulamanız bu verileri kullanmadan önce bir kullanıcı tarafından girilen tüm verileri doğrulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="f1cd0-159">Bu, uygulama günlüğüne veri yazılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="f1cd0-160">**Hizmet reddine engel olmaz.**</span><span class="sxs-lookup"><span data-stu-id="f1cd0-160">**Avoid denial of service.**</span></span> <span data-ttu-id="f1cd0-161">Uygulamanız günlüğe çok fazla bilgi yazdığında, günlüğü doldurabilir veya önemli bilgileri bulmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1cd0-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1cd0-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="f1cd0-163">Uygulamadan Günlüğe Bilgi Kaydetme</span><span class="sxs-lookup"><span data-stu-id="f1cd0-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)

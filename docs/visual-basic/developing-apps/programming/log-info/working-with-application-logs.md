---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic uygulama günlükleriyle çalışma'
title: Uygulama Günlükleriyle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 0c05bd63cfbae668c58a87aa39651b6c3ef166ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792277"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="29d87-103">Visual Basic'te Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="29d87-103">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="29d87-104">`My.Application.Log`Ve `My.Log` nesneleri günlüğe kaydetme ve izleme bilgilerini günlüklere yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="29d87-104">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="29d87-105">Iletiler günlüğe nasıl kaydedilir?</span><span class="sxs-lookup"><span data-stu-id="29d87-105">How Messages are Logged</span></span>

<span data-ttu-id="29d87-106">İlk olarak, iletinin önem derecesi <xref:System.Diagnostics.TraceSource.Switch%2A> Günlüğün özelliğinin özelliği ile denetlenir <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="29d87-106">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="29d87-107">Varsayılan olarak, günlük koleksiyonunda belirtilen izleme dinleyicilerine yalnızca önem derecesi "bilgi" ve üzeri iletiler geçirilir `TraceListener` .</span><span class="sxs-lookup"><span data-stu-id="29d87-107">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="29d87-108">Ardından, her dinleyici iletinin önem derecesini dinleyicinin özelliği ile karşılaştırır <xref:System.Diagnostics.TraceSource.Switch%2A> .</span><span class="sxs-lookup"><span data-stu-id="29d87-108">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="29d87-109">İletinin önem derecesi yeterince yüksekse, dinleyici iletiyi yazar.</span><span class="sxs-lookup"><span data-stu-id="29d87-109">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="29d87-110">Aşağıdaki diyagramda, yönteme yazılan bir iletinin `WriteEntry` `WriteLine` Günlüğün izleme dinleyicilerinin yöntemlerine nasıl geçirildiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="29d87-110">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Günlük çağrımı gösteren diyagram.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="29d87-112">Uygulamanın yapılandırma dosyasını değiştirerek günlük ve izleme dinleyicilerinin davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29d87-112">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="29d87-113">Aşağıdaki diyagramda, günlüğün bölümleri ile yapılandırma dosyası arasındaki yazışma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29d87-113">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Günlük yapılandırmanızın gösterildiği diyagram.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="29d87-115">Iletiler günlüğe kaydedilir</span><span class="sxs-lookup"><span data-stu-id="29d87-115">Where Messages are Logged</span></span>

<span data-ttu-id="29d87-116">Derlemenin yapılandırma dosyası yoksa, `My.Application.Log` ve `My.Log` nesneleri uygulamanın hata ayıklama çıktısına ( <xref:System.Diagnostics.DefaultTraceListener> sınıfı aracılığıyla) yazar.</span><span class="sxs-lookup"><span data-stu-id="29d87-116">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="29d87-117">Ayrıca, nesnesi `My.Application.Log` derlemenin günlük dosyasına ( <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> sınıfı aracılığıyla) yazar, `My.Log` nesne ASP.NET Web sayfasının çıktısına ( <xref:System.Web.WebPageTraceListener> sınıfı aracılığıyla) yazar.</span><span class="sxs-lookup"><span data-stu-id="29d87-117">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="29d87-118">Hata ayıklama çıktısı, uygulamanızı hata ayıklama modunda çalıştırırken Visual Studio **çıktı** penceresinde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="29d87-118">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="29d87-119">**Çıkış** penceresini açmak Için, **Hata Ayıkla** menü öğesine tıklayın, **Windows**' ın üzerine gelin ve ardından **Çıkış**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="29d87-119">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="29d87-120">**Çıkış** penceresinde, **çıktıyı göster** kutusundan **Hata Ayıkla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="29d87-120">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="29d87-121">Varsayılan olarak, `My.Application.Log` günlük dosyasını kullanıcının uygulama verileri yoluna yazar.</span><span class="sxs-lookup"><span data-stu-id="29d87-121">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="29d87-122"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A>Nesnenin özelliğinden yolunu alabilirsiniz <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> .</span><span class="sxs-lookup"><span data-stu-id="29d87-122">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="29d87-123">Yolun biçimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="29d87-123">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="29d87-124">İçin tipik bir değer `BasePath` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="29d87-124">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="29d87-125">C:\Documents and Settings \\ `username` \Application Data</span><span class="sxs-lookup"><span data-stu-id="29d87-125">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="29d87-126">`CompanyName`, `ProductName` Ve değerleri `ProductVersion` uygulamanın derleme bilgileriyle gelir.</span><span class="sxs-lookup"><span data-stu-id="29d87-126">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="29d87-127">Günlük dosyası adının biçimi *AssemblyName*. log biçimindedir, burada *AssemblyName* uzantısı olmayan derlemenin dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="29d87-127">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="29d87-128">Birden çok günlük dosyası gerekiyorsa (örneğin, uygulama günlüğe yazmaya çalıştığında özgün günlüğün kullanılamadığı durumlar gibi), günlük dosyası adı için form *AssemblyName* - *yineleme*. log ' dur ve burada `iteration` pozitif olur `Integer` .</span><span class="sxs-lookup"><span data-stu-id="29d87-128">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="29d87-129">Bilgisayar ve uygulamanın yapılandırma dosyalarını ekleyerek veya değiştirerek varsayılan davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29d87-129">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="29d87-130">Daha fazla bilgi için bkz [. Izlenecek yol: My. Application. log bilgisinin nereden yazabileceğini değiştirme](walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="29d87-130">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="29d87-131">Günlük ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29d87-131">Configuring Log Settings</span></span>

<span data-ttu-id="29d87-132">`Log`Nesnesi, bir uygulama yapılandırma dosyası olmadan çalışacak varsayılan bir uygulamaya sahiptir app.config. Varsayılanları değiştirmek için yeni ayarlara sahip bir yapılandırma dosyası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="29d87-132">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="29d87-133">Daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log çıktısını filtreleme](walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="29d87-133">For more information, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="29d87-134">Günlük yapılandırma bölümleri, `<system.diagnostics>` `<configuration>` app.config dosyasının ana düğümündeki düğümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="29d87-134">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="29d87-135">Günlük bilgileri çeşitli düğümlerde tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="29d87-135">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="29d87-136">`Log`Nesnenin dinleyicileri `<sources>` DefaultSource adlı düğümde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="29d87-136">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="29d87-137">Nesnesi için önem derecesi, `Log` `<switches>` DefaultSwitch adlı düğümde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="29d87-137">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="29d87-138">Günlük dinleyicileri, `<sharedListeners>` düğümde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="29d87-138">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="29d87-139">`<sources>` `<switches>` Aşağıdaki kodda,, ve `<sharedListeners>` düğümleri örnekleri gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29d87-139">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

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

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="29d87-140">Dağıtımdan sonra günlük ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="29d87-140">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="29d87-141">Bir uygulama geliştirirken, Yukarıdaki örneklerde gösterildiği gibi, yapılandırma ayarları app.config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="29d87-141">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="29d87-142">Uygulamanızı dağıttıktan sonra yapılandırma dosyasını düzenleyerek günlüğü yapılandırmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29d87-142">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="29d87-143">Windows tabanlı bir uygulamada, bu dosyanın adı *applicationName*.exe.config ve yürütülebilir dosyayla aynı klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29d87-143">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="29d87-144">Bir Web uygulaması için bu, projeyle ilişkili Web.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="29d87-144">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="29d87-145">Uygulamanız bir sınıfın bir örneğini ilk kez oluşturan kodu yürüttüğünde, nesne hakkında bilgi için yapılandırma dosyasını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="29d87-145">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="29d87-146">Nesnesi için `Log` , bu nesne ilk kez `Log` erişildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="29d87-146">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="29d87-147">Sistem, yapılandırma dosyasını belirli bir nesne için yalnızca bir kez inceler — uygulamanız nesneyi ilk kez oluşturduğunda.</span><span class="sxs-lookup"><span data-stu-id="29d87-147">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="29d87-148">Bu nedenle, değişikliklerin etkili olması için uygulamayı yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="29d87-148">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="29d87-149">Dağıtılan bir uygulamada, uygulama başlamadan önce geçiş nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="29d87-149">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="29d87-150">Genellikle bu, anahtar nesnelerinin açık ve kapalı olduğunu ya da izleme düzeylerini değiştirerek ve sonra uygulamanızı yeniden başlatarak içerir.</span><span class="sxs-lookup"><span data-stu-id="29d87-150">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="29d87-151">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="29d87-151">Security Considerations</span></span>

<span data-ttu-id="29d87-152">Günlüğe veri yazarken aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="29d87-152">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="29d87-153">**Kullanıcı bilgilerinin sızmasını önleyin.**</span><span class="sxs-lookup"><span data-stu-id="29d87-153">**Avoid leaking user information.**</span></span> <span data-ttu-id="29d87-154">Uygulamanızın günlüğe yalnızca onaylanan bilgileri yazdığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="29d87-154">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="29d87-155">Örneğin, uygulama günlüğü Kullanıcı adlarını içermesi, ancak kullanıcı parolalarını içermemesi için kabul edilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="29d87-155">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="29d87-156">**Günlük konumlarını güvenli hale getirin.**</span><span class="sxs-lookup"><span data-stu-id="29d87-156">**Make log locations secure.**</span></span> <span data-ttu-id="29d87-157">Potansiyel olarak hassas bilgiler içeren herhangi bir günlüğün güvenli bir konumda depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29d87-157">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="29d87-158">**Yanıltıcı bilgilerden kaçının.**</span><span class="sxs-lookup"><span data-stu-id="29d87-158">**Avoid misleading information.**</span></span> <span data-ttu-id="29d87-159">Genel olarak, uygulamanız bu verileri kullanmadan önce bir kullanıcı tarafından girilen tüm verileri doğrulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="29d87-159">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="29d87-160">Bu, uygulama günlüğüne veri yazılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="29d87-160">This includes writing data to the application log.</span></span>

- <span data-ttu-id="29d87-161">**Hizmet reddine engel olmaz.**</span><span class="sxs-lookup"><span data-stu-id="29d87-161">**Avoid denial of service.**</span></span> <span data-ttu-id="29d87-162">Uygulamanız günlüğe çok fazla bilgi yazdığında, günlüğü doldurabilir veya önemli bilgileri bulmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="29d87-162">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="29d87-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29d87-163">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="29d87-164">Uygulamadan Günlüğe Bilgi Kaydetme</span><span class="sxs-lookup"><span data-stu-id="29d87-164">Logging Information from the Application</span></span>](index.md)

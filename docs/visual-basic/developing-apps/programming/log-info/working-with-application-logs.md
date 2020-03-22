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
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="07681-102">Visual Basic'te Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="07681-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="07681-103">Ve `My.Application.Log` `My.Log` nesneler günlüklere günlük ve izleme bilgilerini yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="07681-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="07681-104">İletiler Nasıl Günlüğe Kaydedilir?</span><span class="sxs-lookup"><span data-stu-id="07681-104">How Messages are Logged</span></span>

<span data-ttu-id="07681-105">İlk olarak, iletinin önem derecesi günlüğün <xref:System.Diagnostics.TraceSource.Switch%2A> <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> özelliğiyle denetlenir.</span><span class="sxs-lookup"><span data-stu-id="07681-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="07681-106">Varsayılan olarak, yalnızca önem "Bilgi" ve daha yüksek iletileri, log'un `TraceListener` koleksiyonunda belirtilen izleme dinleyicilerine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="07681-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="07681-107">Daha sonra, her dinleyici iletinin önem derecesini dinleyicinin <xref:System.Diagnostics.TraceSource.Switch%2A> özelliğiyle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="07681-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="07681-108">İletinin önem derecesi yeterince yüksekse, dinleyici iletiyi yazar.</span><span class="sxs-lookup"><span data-stu-id="07681-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="07681-109">Aşağıdaki diyagram, yönteme yazılan `WriteEntry` bir iletinin `WriteLine` log'un izleme dinleyicilerinin yöntemlerine nasıl iletildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="07681-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Günlük aramamı gösteren diyagram.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="07681-111">Uygulamanın yapılandırma dosyasını değiştirerek günlüğün ve izleme dinleyicilerinin davranışını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07681-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="07681-112">Aşağıdaki diyagram, günlük parçaları ve yapılandırma dosyası arasındaki yazışmaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="07681-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Günlük yapılandırmamı gösteren diyagram.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="07681-114">İletilerin Günlüğe Kaydedildiği Yerler</span><span class="sxs-lookup"><span data-stu-id="07681-114">Where Messages are Logged</span></span>

<span data-ttu-id="07681-115">Derlemede yapılandırma dosyası yoksa, `My.Application.Log` `My.Log` ve nesneler uygulamanın hata ayıklama çıktısına <xref:System.Diagnostics.DefaultTraceListener> (sınıf aracılığıyla) yazar.</span><span class="sxs-lookup"><span data-stu-id="07681-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="07681-116">Buna ek `My.Application.Log` olarak, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> `My.Log` nesne derlemenin günlük dosyasına (sınıf aracılığıyla) yazarken, nesne ASP.NET Web <xref:System.Web.WebPageTraceListener> sayfasının çıktısına (sınıf aracılığıyla) yazar.</span><span class="sxs-lookup"><span data-stu-id="07681-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="07681-117">Hata ayıklama çıkışı, uygulamanızı hata ayıklama modunda çalıştırırken Visual Studio **Çıktı** penceresinde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="07681-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="07681-118">**Çıktı** penceresini açmak için **Hata Ayıklama** menü öğesini tıklatın, **Windows'u**işaret edin ve sonra **Çıktı'yı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="07681-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="07681-119">**Çıktı** penceresinde, **kutudan çıktıyı göster'den** **Hata Ayıklama'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="07681-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="07681-120">Varsayılan olarak, `My.Application.Log` kullanıcının uygulama verileri için yola günlük dosyası yazar.</span><span class="sxs-lookup"><span data-stu-id="07681-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="07681-121">Yolu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> nesnenin özelliğinden alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07681-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="07681-122">Bu yolun biçimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="07681-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="07681-123">Için tipik `BasePath` bir değer aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="07681-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="07681-124">C:\Belgeler ve\\`username`Ayarlar \Uygulama Verileri</span><span class="sxs-lookup"><span data-stu-id="07681-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="07681-125">`CompanyName`, ve `ProductName` `ProductVersion` uygulamanın derleme bilgi gelen değerleri.</span><span class="sxs-lookup"><span data-stu-id="07681-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="07681-126">Günlük dosya adının biçimi *AssemblyName*.log'dur, *AssemblyName* uzantısı olmadan derlemenin dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="07681-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="07681-127">Başvuru nun günlüğe yazmaya çalıştığı zaman orijinal günlük kullanılamadığı nda birden fazla günlük dosyası gerekiyorsa, günlük dosyası adı için form *AssemblyName*-*yineleme*.log, pozitif `iteration` `Integer`olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="07681-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="07681-128">Bilgisayarın ve uygulamanın yapılandırma dosyalarını ekleyerek veya değiştirerek varsayılan davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07681-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="07681-129">Daha fazla bilgi için [Bkz. Walkthrough: My.Application.Log Yazma Bilgileri Nerede Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="07681-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="07681-130">Günlük Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="07681-130">Configuring Log Settings</span></span>

<span data-ttu-id="07681-131">Nesne, `Log` uygulama yapılandırma dosyası, app.config olmadan çalışan varsayılan bir uygulama vardır. Varsayılanları değiştirmek için, yeni ayarlarla birlikte bir yapılandırma dosyası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07681-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="07681-132">Daha fazla bilgi için [bkz: Walkthrough: Filtreleme My.Application.Log Çıktı](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="07681-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="07681-133">Günlük yapılandırma bölümleri app.config dosyasının `<system.diagnostics>` `<configuration>` ana düğümünde düğüm bulunur.</span><span class="sxs-lookup"><span data-stu-id="07681-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="07681-134">Günlük bilgileri birkaç düğümde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="07681-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="07681-135">Nesnenin `Log` dinleyicileri VarsayılanKaynak adlı `<sources>` düğümde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07681-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="07681-136">Nesnenin `Log` önem derecesi filtresi Varsayılan `<switches>` Anahtar adlı düğümde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07681-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="07681-137">Günlük dinleyiciler `<sharedListeners>` düğümde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07681-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="07681-138">`<sources>`, , `<switches>`ve `<sharedListeners>` düğümörnekleri aşağıdaki kodda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="07681-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

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

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="07681-139">Dağıtımdan Sonra Günlük Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="07681-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="07681-140">Bir uygulama geliştirdiğinizde, yapılandırma ayarları yukarıdaki örneklerde gösterildiği gibi app.config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="07681-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="07681-141">Uygulamanızı dağıttıktan sonra, yapılandırma dosyasını düzenleyerek günlüğü yapılandırmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07681-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="07681-142">Windows tabanlı bir uygulamada, bu dosyanın adı *applicationName*.exe.config'dir ve yürütülebilir dosyayla aynı klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07681-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="07681-143">Bir Web uygulaması için bu, projeyle ilişkili Web.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="07681-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="07681-144">Uygulamanız ilk kez bir sınıfın örneğini oluşturan kodu çalıştırdığında, nesne hakkında bilgi için yapılandırma dosyasını denetler.</span><span class="sxs-lookup"><span data-stu-id="07681-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="07681-145">Nesne `Log` için bu, nesneye `Log` ilk kez erişici olduğunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="07681-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="07681-146">Sistem yapılandırma dosyasını belirli bir nesne için yalnızca bir kez inceler ve uygulamanız nesneyi ilk kez oluşturduğunda.</span><span class="sxs-lookup"><span data-stu-id="07681-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="07681-147">Bu nedenle, değişikliklerin etkili olması için uygulamayı yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="07681-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="07681-148">Dağıtılan bir uygulamada, uygulamanız başlamadan önce anahtar nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="07681-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="07681-149">Genellikle, bu, anahtar nesnelerini açıp kapatmayı veya izleme düzeylerini değiştirerek ve ardından uygulamanızı yeniden başlatmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="07681-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="07681-150">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="07681-150">Security Considerations</span></span>

<span data-ttu-id="07681-151">Günlüğe veri yazarken aşağıdakileri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="07681-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="07681-152">**Kullanıcı bilgilerini sızdırmaktan kaçının.**</span><span class="sxs-lookup"><span data-stu-id="07681-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="07681-153">Uygulamanızın yalnızca onaylanmış bilgileri günlüğüne yazdığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="07681-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="07681-154">Örneğin, uygulama günlüğünün kullanıcı adları içermesi kabul edilebilir, ancak kullanıcı parolaları içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="07681-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="07681-155">**Günlük konumlarını güvenli hale getirin.**</span><span class="sxs-lookup"><span data-stu-id="07681-155">**Make log locations secure.**</span></span> <span data-ttu-id="07681-156">Hassas olabilecek bilgiler içeren tüm günlükler güvenli bir konumda depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07681-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="07681-157">**Yanıltıcı bilgilerden kaçının.**</span><span class="sxs-lookup"><span data-stu-id="07681-157">**Avoid misleading information.**</span></span> <span data-ttu-id="07681-158">Genel olarak, uygulamanız bu verileri kullanmadan önce bir kullanıcı tarafından girilen tüm verileri doğrulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="07681-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="07681-159">Bu, uygulama günlüğüne veri yazmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="07681-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="07681-160">**Hizmet reddi kaçının.**</span><span class="sxs-lookup"><span data-stu-id="07681-160">**Avoid denial of service.**</span></span> <span data-ttu-id="07681-161">Uygulamanız günlüğe çok fazla bilgi yazıyorsa, günlüğü doldurabilir veya önemli bilgileri bulmayı zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="07681-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="07681-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07681-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="07681-163">Uygulamadan Günlüğe Bilgi Kaydetme</span><span class="sxs-lookup"><span data-stu-id="07681-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)

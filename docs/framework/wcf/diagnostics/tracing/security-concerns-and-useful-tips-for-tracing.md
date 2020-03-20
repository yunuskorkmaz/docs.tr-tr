---
title: İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185715"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="a0159-102">İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları</span><span class="sxs-lookup"><span data-stu-id="a0159-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="a0159-103">Bu konu, WebHost kullanırken hassas bilgilerin maruz kalmalarını nasıl koruyabileceğinizi ve yararlı ipuçlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0159-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="a0159-104">WebHost ile Özel İzleme Dinleyicisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0159-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="a0159-105">Kendi izleme dinleyicinizi yazıyorsanız, Web tarafından barındırılan bir hizmet durumunda izlemelerin kaybolabileceği olasılığının farkında olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a0159-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="a0159-106">WebHost yeniden dönüştürdüğünde, yinelenen bir işlem devralırken canlı işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="a0159-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="a0159-107">Ancak, iki işlem yine de dinleyici türüne bağlı bir süre için aynı kaynağa erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0159-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="a0159-108">Bu durumda, `XmlWriterTraceListener` ikinci işlem için yeni bir izleme dosyası oluşturur; Windows olay izleme aynı oturum içinde birden çok işlemi yönetir ve aynı dosyaya erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0159-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="a0159-109">Kendi dinleyiciniz benzer işlevler sağlamazsa, dosya iki işlem tarafından kilitlendiğinde izlemeler kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="a0159-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="a0159-110">Özel izleme dinleyicisinin, örneğin kablodaki izlemeleri ve iletileri uzak bir veritabanına gönderebileceğini de unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a0159-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="a0159-111">Bir uygulama dağıtıcısı olarak, uygun erişim denetimi ile özel dinleyici yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0159-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="a0159-112">Ayrıca, uzak konumda açığa çıkabilen herhangi bir kişisel bilgi üzerinde güvenlik kontrolü uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a0159-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="a0159-113">Hassas Bilgileri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a0159-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="a0159-114">İleti kapsam dayken izlemeler ileti üstbilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a0159-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="a0159-115">İzleme etkinleştirildiğinde, bir sorgu dizesi gibi uygulamaya özgü üstbilgilerdeki kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="a0159-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="a0159-116">Uygulama dağıtıcı, yapılandırma ve izleme dosyaları üzerinde erişim denetimini zorlamakiçin sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a0159-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="a0159-117">Bu tür bilgilerin görünür olmasını istemiyorsanız, izleme günlüğünü paylaşmak istiyorsanız izlemeyi devre dışı bırakmanız veya verilerin bir kısmını filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0159-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="a0159-118">Aşağıdaki ipuçları, izleme dosyasının içeriğinin istemeden açığa çıkarOlmasını önlemenize yardımcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="a0159-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="a0159-119">Günlük dosyalarının hem WebHost'ta hem de kendi barındırma senaryolarında Access Control Lists (ACL) tarafından korunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a0159-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="a0159-120">Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="a0159-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="a0159-121">Örneğin, .xml dosya uzantısı güvenli bir seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="a0159-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="a0159-122">Servis edilebilen uzantıların listesini görmek için IIS yönetim kılavuzunu kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0159-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="a0159-123">Web tarayıcısı kullanan harici bir taraf tarafından erişmesini önlemek için WebHost vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0159-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="a0159-124">Varsayılan olarak, kullanıcı adı ve parola gibi anahtarlar ve kişisel olarak tanımlanabilir bilgiler (PII) izlemelerde ve günlüğe kaydedilmiş iletilerde günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="a0159-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="a0159-125">Ancak bir makine yöneticisi, `enableLoggingKnownPII` Machine.config `machineSettings` dosyasının öğesindeki özniteliği kullanarak makinede çalışan uygulamaların bilinen kişisel olarak tanımlanabilir bilgileri (PII) aşağıdaki gibi günlüğe kaydetmesini sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="a0159-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="a0159-126">Bir uygulama dağıtıcısı `logKnownPii` daha sonra aşağıdaki gibi KIŞISEL günlüğe kaydetmeyi etkinleştirmek için App.config veya Web.config dosyasındaki özniteliği kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="a0159-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="a0159-127">Yalnızca her iki `true` ayar da KIŞISEL olarak günlüğe kaydetme etkin olduğunda.</span><span class="sxs-lookup"><span data-stu-id="a0159-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="a0159-128">İki anahtarın birleşimi, her uygulama için bilinen KIŞISEL Bilgiler'i günlüğe kaydetme esnekliğisağlar.</span><span class="sxs-lookup"><span data-stu-id="a0159-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="a0159-129">Bir yapılandırma dosyasında iki veya daha fazla özel kaynak belirtirseniz, yalnızca ilk kaynağın özniteliklerinin okunduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a0159-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="a0159-130">Diğerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a0159-130">The others are ignored.</span></span> <span data-ttu-id="a0159-131">Bu, aşağıdaki App.config, dosya için, kişisel bilgiler ikinci kaynak için açıkça etkin olsa bile, her iki kaynak için de günlüğe kaydedilmez anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a0159-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="a0159-132">`<machineSettings enableLoggingKnownPii="Boolean"/>` Öğe Machine.config dosyasının dışında varsa, sistem <xref:System.Configuration.ConfigurationErrorsException>bir .</span><span class="sxs-lookup"><span data-stu-id="a0159-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="a0159-133">Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında etkili dir.</span><span class="sxs-lookup"><span data-stu-id="a0159-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="a0159-134">Her iki öznitelik de `true`'' de ayarlandığında, bir olay başlangıçta günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a0159-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="a0159-135">Bir olay, ayarlanmış `logKnownPii` `true` ancak `enableLoggingKnownPii` . `false`</span><span class="sxs-lookup"><span data-stu-id="a0159-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="a0159-136">KIŞISEL bilgiler hakkında daha fazla bilgi [için, KIŞISEL Güvenlik Kilitleme](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="a0159-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="a0159-137">Makine yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0159-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="a0159-138">Kişisel günlük etkinse, güvenlik anahtarları ve KIŞISEL bilgiler günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a0159-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="a0159-139">Devre dışı bırakılmışsa, duyarlı ve uygulamaya özgü veriler ileti üstbilgileri ve gövdelerinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a0159-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="a0159-140">Gizlilik ve kişisel bilgilerin açığa çıkarılmaktan korunması konusunda daha kapsamlı bir tartışma için [Bkz.](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="a0159-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="a0159-141">Ayrıca, ileti gönderenin IP adresi bağlantı yönelimli taşımalar için bağlantı başına bir kez ve aksi takdirde gönderilen ileti başına bir kez günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a0159-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="a0159-142">Bu gönderenin rızası olmadan yapılır.</span><span class="sxs-lookup"><span data-stu-id="a0159-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="a0159-143">Ancak, bu günlüğe kaydetme yalnızca, canlı hata ayıklama dışında varsayılan veya önerilen izleme düzeyleri olmayan Bilgi veya Verbose izleme düzeylerinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a0159-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0159-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0159-144">See also</span></span>

- [<span data-ttu-id="a0159-145">İzleme</span><span class="sxs-lookup"><span data-stu-id="a0159-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)

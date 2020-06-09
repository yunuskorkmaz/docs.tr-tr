---
title: İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0a09e387a4f964441f11d07a84bd492345d5b691
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578883"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="55def-102">İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları</span><span class="sxs-lookup"><span data-stu-id="55def-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="55def-103">Bu konu başlığı altında, gizli bilgilerin sunulanlarından nasıl koruyabileceğiniz ve WebHost kullanırken yararlı olan ipuçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55def-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="55def-104">WebHost ile özel bir Izleme dinleyicisi kullanma</span><span class="sxs-lookup"><span data-stu-id="55def-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="55def-105">Kendi izleme dinleyicinizi yazıyorsanız, izlemelerin Web 'de barındırılan bir hizmette kaybolması ihtimaline dikkat etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55def-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="55def-106">WebHost geri dönüştürüldüğünde canlı işlemi kapatır ve yinelenen bir işlem sürer.</span><span class="sxs-lookup"><span data-stu-id="55def-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="55def-107">Ancak, iki işlemin bir süredir aynı kaynağa erişimi olması gerekir, bu da dinleyici türüne bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="55def-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="55def-108">Bu durumda, `XmlWriterTraceListener` ikinci işlem için yeni bir izleme dosyası oluşturur; Windows olay izleme aynı oturum içinde birden çok işlemi yönetir ve aynı dosyaya erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="55def-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="55def-109">Kendi dinleyiciniz benzer işlevler sağlamıyorsa, dosya iki işlem tarafından kilitlendiğinde izlemeler kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="55def-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="55def-110">Ayrıca, özel bir İzleme dinleyicisinin, uzak bir veritabanına, örneğin, uzak bir veritabanına izleme ve mesaj gönderebildiği farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55def-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="55def-111">Bir uygulama dağıtıcı olarak, uygun erişim denetimiyle özel dinleyicileri yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55def-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="55def-112">Ayrıca, uzak konumda açığa çıkarılabilen herhangi bir kişisel bilgi için güvenlik denetimi de uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="55def-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="55def-113">Gizli bilgileri günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="55def-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="55def-114">İzlemeler, bir ileti kapsamda olduğunda ileti üst bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="55def-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="55def-115">İzleme etkin olduğunda, bir sorgu dizesi gibi uygulamaya özgü üst bilgilerde kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görünür hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="55def-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="55def-116">Uygulama dağıtıcı, yapılandırma ve izleme dosyalarında erişim denetimini zormaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="55def-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="55def-117">Bu tür bilgilerin görünmesini istemiyorsanız, izleme günlüklerini paylaşmak istiyorsanız izlemeyi devre dışı bırakmanız veya verilerin bir kısmını filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55def-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="55def-118">Aşağıdaki ipuçları, bir izleme dosyasının içeriğinin istenmeden gösterilmesini önlemeye yardımcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="55def-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="55def-119">Günlük dosyalarının hem WebHost hem de Self-Host senaryolarında Access Control listeleriyle (ACL) korunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="55def-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="55def-120">Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="55def-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="55def-121">Örneğin,. xml dosya uzantısı güvenli bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="55def-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="55def-122">Hizmet verilen uzantıların bir listesini görmek için IIS Yönetim Kılavuzu ' na bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55def-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="55def-123">Bir Web tarayıcısı kullanarak bir dış tarafın erişmesini engellemek için, WebHost vroot ortak dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.</span><span class="sxs-lookup"><span data-stu-id="55def-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="55def-124">Varsayılan olarak, Kullanıcı adı ve parola gibi anahtarlar ve kişisel bilgiler (PII), izlemelerde ve günlüğe kaydedilen iletilerde günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="55def-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="55def-125">Ancak Makine Yöneticisi, makinede `enableLoggingKnownPII` `machineSettings` çalışan uygulamaların bilinen kişisel olarak tanımlanabilen BILGILERI (PII) şu şekilde günlüğe kaydetmek için Machine. config dosyasının öğesindeki özniteliğini kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="55def-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="55def-126">Daha sonra bir uygulama dağıtıcı, bu `logKnownPii` özniteliği App. config veya Web. config dosyasında kullanarak PII günlüğünü aşağıdaki şekilde etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="55def-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="55def-127">Yalnızca her iki ayar de `true` PII günlüğü etkin olduğunda.</span><span class="sxs-lookup"><span data-stu-id="55def-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="55def-128">İki anahtar birleşimi, her bir uygulama için bilinen PII 'yi günlüğe kaydetme esnekliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="55def-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="55def-129">Bir yapılandırma dosyasında iki veya daha fazla özel kaynak belirtirseniz, yalnızca ilk kaynağın özniteliklerinin okunup okunduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="55def-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="55def-130">Diğerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="55def-130">The others are ignored.</span></span> <span data-ttu-id="55def-131">Bu, aşağıdaki App. config, File, PII için her iki kaynak için de PII günlüğü, ikinci kaynak için açık olarak etkinleştirilmiş olsa da bu şekilde günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="55def-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="55def-132">`<machineSettings enableLoggingKnownPii="Boolean"/>`Öğesi Machine. config dosyasının dışında varsa, sistem bir oluşturur <xref:System.Configuration.ConfigurationErrorsException> .</span><span class="sxs-lookup"><span data-stu-id="55def-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="55def-133">Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="55def-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="55def-134">Her iki öznitelik olarak ayarlandığında bir olay başlangıçta günlüğe kaydedilir `true` .</span><span class="sxs-lookup"><span data-stu-id="55def-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="55def-135">Bir olay, `logKnownPii` olarak ayarlanmışsa günlüğe kaydedilir `true` `enableLoggingKnownPii` `false` .</span><span class="sxs-lookup"><span data-stu-id="55def-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="55def-136">PII günlüğü hakkında daha fazla bilgi için bkz. [PII güvenlik kilitleme](../../samples/pii-security-lockdown.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="55def-136">For more information on PII logging, see [PII Security Lockdown](../../samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="55def-137">Makine Yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55def-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="55def-138">PII günlüğü etkinse, güvenlik anahtarları ve PII günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="55def-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="55def-139">Devre dışıysa, hassas ve uygulamaya özgü veriler hala ileti üstbilgilerinde ve gövdede günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="55def-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="55def-140">Gizlilikle ilgili daha kapsamlı bir tartışma ve PII 'nin gösterilmesini sağlama hakkında daha fazla bilgi için bkz. [Kullanıcı gizliliği](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="55def-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="55def-141">Buna ek olarak, ileti göndericisinin IP adresi bağlantı yönelimli aktarımlar için bağlantı başına bir kez günlüğe kaydedilir ve aksi takdirde ileti başına bir kez gönderilir.</span><span class="sxs-lookup"><span data-stu-id="55def-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="55def-142">Bu, gönderen onay olmadan yapılır.</span><span class="sxs-lookup"><span data-stu-id="55def-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="55def-143">Ancak, bu günlük yalnızca, canlı hata ayıklama haricinde, üretim ortamında varsayılan veya önerilen izleme düzeyleri olmayan bilgi veya ayrıntılı izleme düzeylerinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="55def-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55def-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55def-144">See also</span></span>

- [<span data-ttu-id="55def-145">İzleme</span><span class="sxs-lookup"><span data-stu-id="55def-145">Tracing</span></span>](index.md)

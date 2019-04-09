---
title: İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 72d35230820e8466cd9c63a76b26c7a23bdfe024
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130800"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="a625c-102">İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları</span><span class="sxs-lookup"><span data-stu-id="a625c-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="a625c-103">Bu konuda, WebHost kullanırken faydalı ipuçları yanı sıra açıklanmasını hassas bilgileri nasıl Koruyabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a625c-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="a625c-104">WebHost ile Özel İzleme dinleyicisi kullanma</span><span class="sxs-lookup"><span data-stu-id="a625c-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="a625c-105">Kendi İzleme dinleyicisi yazıyorsanız, bir Web servisinin söz konusu olduğunda izlemeleri kaybolabilir geliştiriciyi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a625c-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="a625c-106">WebHost geri dönüştürüldüğünde, yinelenen devralıyor ancak Canlı işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="a625c-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="a625c-107">Ancak, iki işlem dinleyici türde bağımlı bir süre için hala aynı kaynağa erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a625c-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="a625c-108">Bu durumda, `XmlWriterTraceListener` Windows olay izleme aynı oturumunda birden çok işlem yönetir ve aynı dosyaya erişim sunar; ikinci işlem için yeni bir izleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a625c-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="a625c-109">Kendi dinleyici benzer işlevleri sağlamıyorsa, dosyanın iki işlem tarafından kilitli değilken izlemeleri kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="a625c-110">Özel İzleme dinleyicisi izlemeleri ve iletileri kablo, örneğin, bir uzak veritabanına gönderebildiğini farkında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a625c-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="a625c-111">Bir uygulama dağıtıcı uygun erişim denetimi ile özel dinleyicileri yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a625c-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="a625c-112">Ayrıca, uzak konumu gösterilen herhangi bir kişisel bilgi denetimde güvenlik uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a625c-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="a625c-113">Hassas bilgi günlük kaydı</span><span class="sxs-lookup"><span data-stu-id="a625c-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="a625c-114">Kapsam içinde bir ileti olduğunda ileti üstbilgileri izlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a625c-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="a625c-115">İzleme etkin olduğunda, uygulamaya özgü üstbilgiler, sorgu dizesi gibi kişisel bilgileri; ve kredi kartı numarası gibi bilgileri gövde, günlüklerde görünür hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="a625c-116">Uygulama dağıtıcısı, yapılandırma ve izleme dosyaları üzerinde erişim denetimi uygulamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a625c-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="a625c-117">Bu tür bilgilerin görünür olmasını istemiyorsanız, izlemeyi devre dışı bırakmak veya verilerin bir kısmını izleme günlükleri paylaşmak istiyorsanız filtre gerekir.</span><span class="sxs-lookup"><span data-stu-id="a625c-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="a625c-118">Aşağıdaki ipuçları bir izleme dosyası içeriğini istenmeden açıklanmasını önlemenize yardımcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="a625c-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="a625c-119">Günlük dosyaları tarafından erişim denetim listeleri (ACL) WebHost ve barındırma senaryolarında korunan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a625c-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="a625c-120">Bir Web isteği sunularak kolayca sunulamayan bir dosya uzantısı'nı seçin.</span><span class="sxs-lookup"><span data-stu-id="a625c-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="a625c-121">Örneğin, .xml dosya uzantısı güvenli bir seçenek değil.</span><span class="sxs-lookup"><span data-stu-id="a625c-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="a625c-122">Sunulabilecek uzantıların listesini görmek için IIS Yönetim kılavuzuna bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a625c-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="a625c-123">Bir Web tarayıcısı kullanılarak harici bir tarafça erişilmesini önlemek için WebHost vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.</span><span class="sxs-lookup"><span data-stu-id="a625c-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="a625c-124">Varsayılan olarak, anahtarları ve kullanıcı adı ve parola gibi kişisel bilgileri (PII) izlemeleri günlüğe kaydedilmez ve iletileri günlüğe.</span><span class="sxs-lookup"><span data-stu-id="a625c-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="a625c-125">Bir makine yöneticisinin ancak kullanabilirsiniz `enableLoggingKnownPII` özniteliğini `machineSettings` makine üzerinde çalışan uygulamalar, bilinen kişisel bilgileri (PII) aşağıdaki gibi oturum izin vermek için Machine.config dosyasının öğesi:</span><span class="sxs-lookup"><span data-stu-id="a625c-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="a625c-126">Bir uygulama dağıtıcı ardından kullanabilirsiniz `logKnownPii` PII gibi günlüğe kaydetmeyi etkinleştirmek için App.config veya Web.config dosyasında özniteliği:</span><span class="sxs-lookup"><span data-stu-id="a625c-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="a625c-127">Yalnızca her iki ayarın olduğunda `true` PII ünlüğe kaydetme etkin olduğunu.</span><span class="sxs-lookup"><span data-stu-id="a625c-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="a625c-128">İki anahtar bileşimi, her uygulama için bilinen PII oturum esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a625c-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="a625c-129">Bir yapılandırma dosyasında iki veya daha fazla özel kaynağı belirtirseniz, yalnızca ilk kaynak özniteliklerini okunduğu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a625c-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="a625c-130">Diğerlerine göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-130">The others are ignored.</span></span> <span data-ttu-id="a625c-131">Bu, PII günlük açıkça ikinci kaynağı için etkinleştirilmiş olsa da aşağıdaki App.config için dosya, PII hem kaynakları için günlüğe kaydedilmez, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a625c-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="a625c-132">Varsa `<machineSettings enableLoggingKnownPii="Boolean"/>` öğesi Machine.config dosyasının dışında var, sistem oluşturur bir <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="a625c-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="a625c-133">Uygulama başlatıldığında veya yeniden değişiklikleri etkili olur.</span><span class="sxs-lookup"><span data-stu-id="a625c-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="a625c-134">Her iki öznitelik ayarlandığında başlangıçta bir olay kaydedilir `true`.</span><span class="sxs-lookup"><span data-stu-id="a625c-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="a625c-135">Bir olay, ayrıca kaydedilir `logKnownPii` ayarlanır `true` ancak `enableLoggingKnownPii` olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="a625c-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="a625c-136">PII günlüğe kaydetme hakkında daha fazla bilgi için bkz. [PII güvenlik kilidi](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="a625c-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="a625c-137">Makine Yöneticisi ve uygulama dağıtıcı aşırı bu iki anahtar kullanırken dikkatli.</span><span class="sxs-lookup"><span data-stu-id="a625c-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="a625c-138">PII günlüğe kaydetme etkinleştirilmişse, güvenlik anahtarları ve PII günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="a625c-139">Etkinleştirilirse, hala ileti üstbilgileri ve gövdeleri hassas ve uygulamaya özgü veriler günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="a625c-140">Gizlilik ve açıklanmasını PII koruma hakkında daha kapsamlı bir açıklama için bkz: [kullanıcı gizliliğini](https://go.microsoft.com/fwlink/?LinkID=94647).</span><span class="sxs-lookup"><span data-stu-id="a625c-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="a625c-141">Ayrıca, iletiyi gönderenin IP adresi, bir kez bağlantı tabanlı aktarımlar için bağlantı başına ve bir kez aksi gönderilen ileti başına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="a625c-142">Bu gönderen rızası gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a625c-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="a625c-143">Ancak, bu günlük yalnızca, varsayılan olmayan ya da önerilen izlemenin düzeylerin, üretimde dışında hata ayıklama Canlı bilgi veya ayrıntılı izleme düzeyleri gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a625c-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a625c-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a625c-144">See also</span></span>

- [<span data-ttu-id="a625c-145">İzleme</span><span class="sxs-lookup"><span data-stu-id="a625c-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)

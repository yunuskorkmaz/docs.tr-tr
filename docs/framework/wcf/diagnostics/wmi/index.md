---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: b14f9401266bdf7edccd7dca12cb818cdd2cb348
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121542"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="47fe1-102">Tanılama için Windows Yönetim İzlemesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="47fe1-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="47fe1-103">Windows Communication Foundation (WCF), bir WCF Windows Management Instrumentation (WMI) sağlayıcısı aracılığıyla bir hizmetin denetim verilerini çalışma zamanında ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="47fe1-104">WMI'yi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="47fe1-104">Enabling WMI</span></span>  
 <span data-ttu-id="47fe1-105">WMI, Microsoft'un Web Tabanlı Kurumsal Yönetim (WBEM) standardını uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="47fe1-106">WMI SDK hakkında daha fazla bilgi için [Windows Management Instrumentation'a](/windows/desktop/WmiSdk/wmi-start-page)bakın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="47fe1-107">WBEM, uygulamaların yönetim araçlarını dış yönetim araçlarına nasıl maruz bıraktamaları için bir endüstri standardıdır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="47fe1-108">WMI sağlayıcısı, WBEM uyumlu bir arabirim aracılığıyla çalışma zamanında enstrümantasyonu ortaya çıkaran bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="47fe1-109">Öznitelik/değer çiftleri olan bir WMI nesne kümesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="47fe1-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="47fe1-110">Çiftleri basit türleri bir dizi olabilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="47fe1-111">Yönetim araçları, çalışma zamanında arabirim üzerinden hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="47fe1-112">WCF, adresler, bağlamalar, davranışlar ve dinleyiciler gibi hizmetlerin özniteliklerini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="47fe1-113">Yerleşik WMI sağlayıcısı uygulamanın yapılandırma dosyasında etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="47fe1-114">Bu, aşağıdaki `wmiProviderEnabled` örnek yapılandırmada gösterildiği [ \<gibi, system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde [ \<>tanılama](../../../configure-apps/file-schema/wcf/diagnostics.md) özniteliği ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="47fe1-115">Bu yapılandırma girişi bir WMI arabirimini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="47fe1-116">Yönetim uygulamaları artık bu arayüz üzerinden bağlanabilir ve uygulamanın yönetim enstrümantasyonuna erişebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="47fe1-117">WMI Verilerine Erişim</span><span class="sxs-lookup"><span data-stu-id="47fe1-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="47fe1-118">WMI verilerine birçok farklı şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="47fe1-119">Microsoft komut dosyaları, Visual Basic uygulamaları, C++ uygulamaları ve .NET Framework için WMI API'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="47fe1-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="47fe1-120">Daha fazla bilgi için [WMI kullanma'ya](/windows/win32/wmisdk/using-wmi)bakın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-120">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="47fe1-121">.NET Framework sağlanan yöntemleri nizveolarak WMI verilerine erişmek için kullanıyorsanız, bağlantı kurulduğunda bu tür yöntemlerin özel durumlar oluşturabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="47fe1-122"><xref:System.Management.ManagementObject> Bağlantı, örneğin yapımı sırasında değil, gerçek veri alışverişini içeren ilk istek üzerine kurulur.</span><span class="sxs-lookup"><span data-stu-id="47fe1-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="47fe1-123">Bu nedenle, olası `try..catch` özel durumları yakalamak için bir blok kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="47fe1-124">İzleme ve ileti günlüğe kaydetme düzeyini ve WMI'deki `System.ServiceModel` izleme kaynağı için ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47fe1-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="47fe1-125">Bu [AppDomainInfo](appdomaininfo.md) örneğine erişerek yapılabilir, hangi bu Boolean `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel`özellikleri `LogMalformedMessages`ortaya `TraceLevel`çıkarır: , , ve .</span><span class="sxs-lookup"><span data-stu-id="47fe1-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="47fe1-126">Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri `false` yapılandırmada ayarlarsanız, bunları daha sonra uygulama çalışırken değiştirebilirsiniz. `true`</span><span class="sxs-lookup"><span data-stu-id="47fe1-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="47fe1-127">Bu, çalışma zamanında ileti günlüğe kaydetmeyi etkin bir şekilde etkinleştirecektir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="47fe1-128">Benzer şekilde, yapılandırma dosyanızda ileti günlüğe kaydetmeyi etkinleştiriseniz, WMI kullanarak çalışma zamanında devre dışı kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47fe1-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="47fe1-129">İleti günlüğe kaydetme için hiçbir ileti günlüğe kaydetme `System.ServiceModel` dinleyicisi yoksa veya yapılandırma dosyasında izleme için izleme dinleyicisi belirtilmemişse, değişiklikler WMI tarafından kabul edilse bile değişikliklerinizin hiçbirinin geçerli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="47fe1-130">İlgili dinleyicilerin düzgün bir şekilde ayarlanması hakkında daha fazla bilgi için Bkz. [İleti Günlüğe Kaydetme](../configuring-message-logging.md) ve [İzlemeyi Yapılandırma.](../tracing/configuring-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="47fe1-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="47fe1-131">Yapılandırma tarafından belirtilen diğer tüm izleme kaynaklarının izleme düzeyi, uygulama başladığında etkilidir ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="47fe1-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="47fe1-132">WCF komut `GetOperationCounterInstanceName` dosyası için bir yöntem ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="47fe1-133">Bu yöntem, bir işlem adı ile sağlarsanız bir performans sayacı örnek adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="47fe1-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="47fe1-134">Ancak, giriş doğrulamıyor.</span><span class="sxs-lookup"><span data-stu-id="47fe1-134">However, it does not validate your input.</span></span> <span data-ttu-id="47fe1-135">Bu nedenle, yanlış bir işlem adı sağlarsanız, yanlış bir sayaç adı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="47fe1-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="47fe1-136">WCF istemcisi hedef hizmete `OutgoingChannel` `Service` metodun içinde oluşturulmazsa, örneğin özelliği başka bir hizmete bağlanmak için bir hizmet tarafından açılan kanalları saymaz. `Service`</span><span class="sxs-lookup"><span data-stu-id="47fe1-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="47fe1-137">**Dikkat** WMI yalnızca <xref:System.TimeSpan> 3 ondalık noktaya kadar olan bir değeri destekler.</span><span class="sxs-lookup"><span data-stu-id="47fe1-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="47fe1-138">Örneğin, hizmetiniz özelliklerinden birini <xref:System.TimeSpan.MaxValue>, WMI üzerinden görüntülendiğinde 3 ondalık noktadan sonra kesilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="47fe1-139">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="47fe1-139">Security</span></span>  
 <span data-ttu-id="47fe1-140">WCF WMI sağlayıcısı bir ortamda hizmetlerin bulunmasına izin verdiği için, bu hizmete erişim sağlamak için çok dikkatli olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="47fe1-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="47fe1-141">Yalnızca varsayılan yönetici erişimini rahatlatırsanız, daha az güvenilen tarafların ortamınızdaki hassas verilere erişmesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47fe1-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="47fe1-142">Özellikle, uzaktan WMI erişimi izinleri gevşetin, sel saldırıları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="47fe1-143">Bir işlem aşırı WMI istekleri yle su basarsa, performansı düşürülebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="47fe1-144">Buna ek olarak, MOF dosyası için erişim izinlerini gevşetirseniz, daha az güvenilen taraflar WMI'nin davranışını değiştirebilir ve WMI şemasına yüklenen nesneleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="47fe1-145">Örneğin, kritik verilerin yöneticiden gizlenmesi veya dosyaya doldurmayan veya özel durumlara neden olmayan alanlar eklenecek şekilde alanlar kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="47fe1-146">Varsayılan olarak, WCF WMI sağlayıcısı yönetici için "yürütme yöntemi", "sağlayıcı yazma" ve "hesap etkinleştirme" izni ve ASP.NET, Yerel Hizmet ve Ağ Hizmeti için "hesap etkinleştirme" izni verir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="47fe1-147">Özellikle, Windows Vista olmayan platformlarda, ASP.NET hesabı WMI ServiceModel ad alanına erişimi okumuştur.</span><span class="sxs-lookup"><span data-stu-id="47fe1-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="47fe1-148">Bu ayrıcalıkları belirli bir kullanıcı grubuna vermek istemiyorsanız, WMI sağlayıcısını devre dışı bırakmanız (varsayılan olarak devre dışı bırakılır) veya belirli kullanıcı grubu için erişimi devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="47fe1-149">Ayrıca, yapılandırma yoluyla WMI'yi etkinleştirmeye çalıştığınızda, kullanıcı ayrıcalığı yetersiz olduğu için WMI etkinleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="47fe1-150">Ancak, bu hatayı kaydetmek için olay günlüğüne hiçbir olay yazılmamıştır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="47fe1-151">Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="47fe1-152">Başlat'ı tıklatın ve sonra çalıştır Ve **compmgmt.msc**yazın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="47fe1-153">**Özellikleri**seçmek için **Hizmetler ve Uygulama/WMI Denetimleri'ni** sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="47fe1-154">**Güvenlik** Sekmesi'ni seçin ve **Root/ServiceModel** ad alanına gidin.</span><span class="sxs-lookup"><span data-stu-id="47fe1-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="47fe1-155">**Güvenlik** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="47fe1-156">Erişimi denetlemek istediğiniz belirli grubu veya kullanıcıyı seçin ve izinleri yapılandırmak için **İzin Ver** veya **Reddet** onay kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="47fe1-157">Ek Kullanıcılara WCF WMI Kayıt İzni Verilmesi</span><span class="sxs-lookup"><span data-stu-id="47fe1-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="47fe1-158">WCF, yönetim verilerini WMI'ye maruz bırakır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="47fe1-159">Bunu bazen "ayrılmış sağlayıcı" olarak adlandırılan bir süreç içinde WMI sağlayıcısı barındırarak yapar.</span><span class="sxs-lookup"><span data-stu-id="47fe1-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="47fe1-160">Yönetim verilerinin açığa alınması için, bu sağlayıcıyı kaydeden hesabın uygun izinlere sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="47fe1-161">Windows'da, yalnızca küçük bir ayrıcalıklı hesap kümesi varsayılan olarak ayrılmış sağlayıcıları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="47fe1-162">Kullanıcılar genellikle varsayılan kümede olmayan bir hesap altında çalışan bir WCF hizmetinden WMI verilerini ortaya çıkarmak istediğinizden, bu bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="47fe1-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="47fe1-163">Bu erişimi sağlamak için, yöneticinin aşağıdaki sırada ek hesaba aşağıdaki izinleri vermesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="47fe1-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="47fe1-164">WCF WMI İsim Alanına erişim izni.</span><span class="sxs-lookup"><span data-stu-id="47fe1-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="47fe1-165">WCF Decoupled WMI Sağlayıcısı'nı kaydetme izni.</span><span class="sxs-lookup"><span data-stu-id="47fe1-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="47fe1-166">WMI ad alanı erişim izni vermek için</span><span class="sxs-lookup"><span data-stu-id="47fe1-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="47fe1-167">Aşağıdaki PowerShell komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="47fe1-168">Bu PowerShell komut dosyası, Yerleşik Kullanıcılar grubuna "root/servicemodel" WMI ad alanına erişim sağlamak için Güvenlik Tanımlayıcı Tanım Dili (SDDL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="47fe1-169">Aşağıdaki ALA'ları belirtir:</span><span class="sxs-lookup"><span data-stu-id="47fe1-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="47fe1-170">Yerleşik yönetici (BA) - zaten erişimi vardı.</span><span class="sxs-lookup"><span data-stu-id="47fe1-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="47fe1-171">Ağ Hizmeti (NS) - Zaten erişimi vardı.</span><span class="sxs-lookup"><span data-stu-id="47fe1-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="47fe1-172">Yerel sistem (LS) - zaten erişimi vardı.</span><span class="sxs-lookup"><span data-stu-id="47fe1-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="47fe1-173">Yerleşik Kullanıcılar - Erişim izni verecek grup.</span><span class="sxs-lookup"><span data-stu-id="47fe1-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="47fe1-174">Sağlayıcı kaydı erişimi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="47fe1-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="47fe1-175">Aşağıdaki PowerShell komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="47fe1-176">Rasgele Kullanıcılara veya Gruplara Erişim Verme</span><span class="sxs-lookup"><span data-stu-id="47fe1-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="47fe1-177">Bu bölümdeki örnek, wmi sağlayıcı kayıt ayrıcalıklarını tüm yerel kullanıcılara verir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="47fe1-178">Yerleşik olmayan bir kullanıcıya veya gruba erişim izni vermek istiyorsanız, o kullanıcının veya grubun Güvenlik Tanımlayıcısını (SID) edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group's Security Identifier (SID).</span></span> <span data-ttu-id="47fe1-179">Rasgele bir kullanıcı için SID almak için basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="47fe1-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="47fe1-180">Bir yöntem istenilen kullanıcı olarak oturum açmak ve sonra aşağıdaki kabuk komutunu vermektir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="47fe1-181">Bu, geçerli kullanıcının SID'sini sağlar, ancak bu yöntem herhangi bir rasgele kullanıcıüzerinde SID almak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="47fe1-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="47fe1-182">SID almak için başka bir yöntem yönetim görevleri için Windows 2000 Kaynak Kiti Araçları [getsid.exe](/windows/win32/wmisdk/using-wmi) aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-182">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="47fe1-183">Bu araç, iki kullanıcının (yerel veya etki alanı) SID'sini karşılaştırır ve yan etki olarak iki SID'yi komut satırına yazdırır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="47fe1-184">Daha fazla bilgi için, [Bilinen SIT'lere](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems)bakın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-184">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="47fe1-185">Uzak WMI Nesne Örneklerine Erişim</span><span class="sxs-lookup"><span data-stu-id="47fe1-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="47fe1-186">Uzak bir makinede WCF WMI örneklerine erişmeniz gerekiyorsa, erişmek için kullandığınız araçlarda paket gizliliğini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="47fe1-187">Aşağıdaki bölümde WMI CIM Studio, Windows Management Instrumentation Tester ve .NET SDK 2.0'ı kullanarak bunların nasıl elde edilebildiğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="47fe1-188">WMI CIM Stüdyo</span><span class="sxs-lookup"><span data-stu-id="47fe1-188">WMI CIM Studio</span></span>

<span data-ttu-id="47fe1-189">WMI İdari Araçları'nı yüklediyseniz, WMI örneklerine erişmek için WMI CIM Studio'yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47fe1-189">If you've installed WMI Administrative Tools, you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="47fe1-190">Araçlar aşağıdaki klasördedir:</span><span class="sxs-lookup"><span data-stu-id="47fe1-190">The tools are in the following folder:</span></span>
  
<span data-ttu-id="47fe1-191">*%windir%\Program Dosyaları\WMI Araçları\\*</span><span class="sxs-lookup"><span data-stu-id="47fe1-191">*%windir%\Program Files\WMI Tools\\*</span></span>
  
1. <span data-ttu-id="47fe1-192">Ad **alanına Bağlan:pencere,** **root\ServiceModel** yazın ve **Tamam'ı tıklatın.**</span><span class="sxs-lookup"><span data-stu-id="47fe1-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="47fe1-193">**WMI CIM Studio Giriş** penceresinde, pencereyi genişletmek için **Seçenekler >>** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="47fe1-194">Kimlik Doğrulama **düzeyi**için Paket **gizliliği'ni** seçin ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="47fe1-195">Windows Yönetimi Enstrümantasyon Test Cihazı</span><span class="sxs-lookup"><span data-stu-id="47fe1-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="47fe1-196">Bu araç Windows tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-196">This tool is installed by Windows.</span></span> <span data-ttu-id="47fe1-197">Çalıştırmak için **Başlat/Çalıştır** iletişim kutusuna **cmd.exe** yazarak bir komut konsolu başlatın ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="47fe1-198">Ardından, komut penceresinde **wbemtest.exe** yazın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="47fe1-199">Windows Yönetimi Instrumentation Tester aracı daha sonra başlatılır.</span><span class="sxs-lookup"><span data-stu-id="47fe1-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="47fe1-200">Pencerenin sağ üst köşesindeki **Bağlan** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="47fe1-201">Yeni pencerede, **Ad Alanı** alanı için **root\ServiceModel'i** girin ve **Kimlik Doğrulama düzeyi**için Paket **gizliliğini** seçin.</span><span class="sxs-lookup"><span data-stu-id="47fe1-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="47fe1-202">**Bağlan**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="47fe1-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="47fe1-203">Yönetilen Kodu Kullanma</span><span class="sxs-lookup"><span data-stu-id="47fe1-203">Using Managed Code</span></span>  
 <span data-ttu-id="47fe1-204">Ayrıca, ad alanı tarafından sağlanan sınıfları kullanarak uzaktan <xref:System.Management> WMI örneklerine programlı olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47fe1-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="47fe1-205">Aşağıdaki kod örneği bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="47fe1-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```

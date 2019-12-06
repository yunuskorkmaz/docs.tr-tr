---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 26758c8a4f537f9522d5ab650ae6b3cd8f044db2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837447"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="4038d-102">Tanılama için Windows Yönetim İzlemesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="4038d-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="4038d-103">Windows Communication Foundation (WCF) bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla çalışma zamanında bir hizmetin İnceleme verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4038d-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="4038d-104">WMI etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="4038d-104">Enabling WMI</span></span>  
 <span data-ttu-id="4038d-105">WMI, Microsoft 'un web tabanlı kuruluş yönetimi (WBEM) standardı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="4038d-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="4038d-106">WMI SDK hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="4038d-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="4038d-107">WBEM, uygulamaların yönetim araçları 'nı dış yönetim araçlarına nasıl sergilekullandığını gösteren bir sektör standardıdır.</span><span class="sxs-lookup"><span data-stu-id="4038d-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="4038d-108">WMI sağlayıcısı, çalışma zamanında WBEM ile uyumlu bir arabirim aracılığıyla izleme sunan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="4038d-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="4038d-109">Öznitelik/değer çiftlerine sahip bir WMI nesneleri kümesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="4038d-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="4038d-110">Çiftler bir dizi basit türden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="4038d-111">Yönetim Araçları, çalışma zamanında arabirim aracılığıyla hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="4038d-112">WCF, adresler, bağlamalar, davranışlar ve dinleyicileri gibi hizmetlerin özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4038d-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="4038d-113">Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="4038d-114">Bu, aşağıdaki örnek yapılandırmada gösterildiği gibi [\<System. serviceModel >](../../../configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde [\<Tanılama >](../../../configure-apps/file-schema/wcf/diagnostics.md) `wmiProviderEnabled` özniteliği aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="4038d-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4038d-115">Bu yapılandırma girişi bir WMI arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="4038d-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="4038d-116">Yönetim uygulamaları artık bu arabirimden bağlanabilir ve uygulamanın yönetim araçlarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="4038d-117">WMI verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="4038d-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="4038d-118">WMI verilerine birçok farklı yolla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="4038d-119">Microsoft, betikler, Visual Basic uygulamalar, C++ uygulamalar ve .NET Framework Için WMI API 'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4038d-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="4038d-120">Daha fazla bilgi için bkz. [WMI kullanma](https://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="4038d-120">For more information, see [Using WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="4038d-121">WMI verilerine programlı olarak erişmek için .NET Framework sağlanan yöntemleri kullanırsanız, bu tür yöntemlerin bağlantı kurulurken özel durumlar oluşturduğunu bilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="4038d-122"><xref:System.Management.ManagementObject> örneğinin oluşturulması sırasında bağlantı kurulmadı, ancak gerçek veri değişimini içeren ilk istek.</span><span class="sxs-lookup"><span data-stu-id="4038d-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="4038d-123">Bu nedenle, olası özel durumları yakalamak için bir `try..catch` bloğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4038d-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="4038d-124">İzleme ve mesaj günlüğü düzeyini ve WMI 'daki `System.ServiceModel` izleme kaynağı için ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="4038d-125">Bu, bu Boole özelliklerini sunan [AppDomainInfo](appdomaininfo.md) örneğine erişerek yapılabilir: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`ve `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="4038d-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="4038d-126">Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri yapılandırmada `false` ayarlarsanız, uygulama çalışırken `true` daha sonra değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="4038d-127">Bu işlem, çalışma zamanında ileti günlüğe kaydetmeyi etkin bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4038d-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="4038d-128">Benzer şekilde, yapılandırma dosyanızda ileti günlüğünü etkinleştirirseniz, WMI kullanarak çalışma zamanında devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="4038d-129">İleti günlüğe kaydetme için bir ileti günlüğe kaydetme `System.ServiceModel` veya izleme dinleyicilerinin yapılandırma dosyasında belirtilmediği durumlarda, değişiklikler WMI tarafından kabul edilse bile değişikliklerden hiçbiri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4038d-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="4038d-130">İlgili dinleyicileri doğru şekilde ayarlama hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../configuring-message-logging.md) ve [izlemeyi yapılandırma](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="4038d-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="4038d-131">Yapılandırma tarafından belirtilen diğer tüm izleme kaynaklarının izleme düzeyi uygulama başlatıldığında etkilidir ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4038d-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="4038d-132">WCF, betik oluşturma için bir `GetOperationCounterInstanceName` yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="4038d-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="4038d-133">Bu yöntem, bir işlem adı ile sağlarsanız bir performans sayacı örnek adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="4038d-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="4038d-134">Ancak, girişinizi doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="4038d-134">However, it does not validate your input.</span></span> <span data-ttu-id="4038d-135">Bu nedenle, yanlış bir işlem adı sağlarsanız, yanlış bir sayaç adı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4038d-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="4038d-136">`Service` örneğinin `OutgoingChannel` özelliği, başka bir hizmete bağlanmak için bir hizmet tarafından açılan kanalları saymaz (hedef hizmete yönelik WCF istemcisi, `Service` yönteminde oluşturulmadıysa).</span><span class="sxs-lookup"><span data-stu-id="4038d-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="4038d-137">**Dikkat** edin WMI yalnızca 3 ondalık noktaya kadar <xref:System.TimeSpan> bir değeri destekler.</span><span class="sxs-lookup"><span data-stu-id="4038d-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="4038d-138">Örneğin, hizmetiniz özelliklerinden birini <xref:System.TimeSpan.MaxValue>olarak ayarladıysanız, WMI üzerinden görüntülendiğinde 3 ondalık noktadan sonra değeri kesilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="4038d-139">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="4038d-139">Security</span></span>  
 <span data-ttu-id="4038d-140">WCF WMI sağlayıcısı bir ortamdaki hizmetlerin bulunmasına izin verdiğinden, buna erişim vermek için çok dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4038d-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="4038d-141">Varsayılan yalnızca yönetici erişimini rahatladıysanız, ortamınızda hassas verilere daha az güvenilir taraflar erişebilmeye izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="4038d-142">Özellikle, uzak WMI erişimiyle ilgili izinleri gevbir şekilde bırakırsanız, taşması saldırıları meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="4038d-143">Bir işlem aşırı sayıda WMI isteği ile taştığında, performansı düşebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="4038d-144">Ayrıca, MOF dosyası için erişim izinlerine güveniyorsanız, daha az güvenilir taraflar WMI davranışını değiştirebilir ve WMI şemasında yüklenen nesneleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="4038d-145">Örneğin, kritik verilerin yöneticiden kaldırılması veya bir özel durum doldurulmayan veya neden olmayan alanlar dosyaya eklenebileceği için alanlar kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="4038d-146">Varsayılan olarak, WCF WMI sağlayıcısı yönetici için "yürütme yöntemi", "sağlayıcı yazma" ve "hesabı etkinleştir" iznini ve ASP.NET, yerel hizmet ve ağ hizmeti için "hesabı etkinleştir" iznini verir.</span><span class="sxs-lookup"><span data-stu-id="4038d-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="4038d-147">Özellikle, Windows dışı Vista platformlarında, ASP.NET hesabının WMI ServiceModel ad alanına okuma erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="4038d-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="4038d-148">Bu ayrıcalıkları belirli bir kullanıcı grubuna vermek istemiyorsanız, WMI sağlayıcısını devre dışı bırakmanız gerekir (varsayılan olarak devre dışıdır) ya da belirli kullanıcı grubu için erişimi devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4038d-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="4038d-149">Ayrıca, WMI 'yi yapılandırma yoluyla etkinleştirmeye çalıştığınızda, yetersiz kullanıcı ayrıcalıkları nedeniyle WMI etkinleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="4038d-150">Ancak, bu hatayı kaydetmek için olay günlüğüne hiçbir olay yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="4038d-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="4038d-151">Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4038d-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="4038d-152">Başlat ' a ve ardından Çalıştır ' a tıklayıp **compmgmt. msc**yazın.</span><span class="sxs-lookup"><span data-stu-id="4038d-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="4038d-153">**Özellikler**' i seçmek için **Hizmetler ve uygulama/WMI denetimleri** öğesine sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4038d-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="4038d-154">**Güvenlik** sekmesini seçin ve **kök/ServiceModel** ad alanına gidin.</span><span class="sxs-lookup"><span data-stu-id="4038d-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="4038d-155">**Güvenlik** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4038d-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="4038d-156">Erişimi denetlemek istediğiniz belirli bir grup veya kullanıcıyı seçin ve izinleri yapılandırmak için **Izin ver** veya **Reddet** onay kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4038d-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="4038d-157">Ek kullanıcılara WCF WMI kayıt Izinleri verme</span><span class="sxs-lookup"><span data-stu-id="4038d-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="4038d-158">WCF, yönetim verilerini WMI 'ya gösterir.</span><span class="sxs-lookup"><span data-stu-id="4038d-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="4038d-159">Bu işlemi, bazen "ayrılmış sağlayıcı" olarak adlandırılan işlem içi bir WMI sağlayıcısını barındırarak yapar.</span><span class="sxs-lookup"><span data-stu-id="4038d-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="4038d-160">Yönetim verilerinin açığa çıkarılması için, bu sağlayıcıyı kaydeden hesabın uygun izinlere sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4038d-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="4038d-161">Windows 'da, yalnızca küçük bir ayrıcalıklı hesap kümesi varsayılan olarak ayrılmış sağlayıcıları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="4038d-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="4038d-162">Bu bir sorun olduğundan, kullanıcılar genellikle varsayılan kümesinde olmayan bir hesap altında çalışan bir WCF hizmetinden WMI verilerini açığa çıkarmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="4038d-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="4038d-163">Bu erişimi sağlamak için, yöneticinin ek hesaba aşağıdaki sırayla aşağıdaki izinleri vermesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="4038d-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="4038d-164">WCF WMI ad alanına erişme izni.</span><span class="sxs-lookup"><span data-stu-id="4038d-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="4038d-165">WCF ayrılmış WMI sağlayıcısını kaydetme izni.</span><span class="sxs-lookup"><span data-stu-id="4038d-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="4038d-166">WMI ad alanı erişim izni vermek için</span><span class="sxs-lookup"><span data-stu-id="4038d-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="4038d-167">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4038d-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="4038d-168">Bu PowerShell betiği, yerleşik kullanıcılar grubuna "root/ServiceModel" WMI ad alanına erişim izni vermek için güvenlik tanımlayıcısı tanım dili 'ni (SDDL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4038d-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="4038d-169">Aşağıdaki ACL 'Leri belirtir:</span><span class="sxs-lookup"><span data-stu-id="4038d-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="4038d-170">Yerleşik yönetici (BA)-zaten erişime sahipti.</span><span class="sxs-lookup"><span data-stu-id="4038d-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="4038d-171">Ağ hizmeti (NS)-zaten erişime sahipti.</span><span class="sxs-lookup"><span data-stu-id="4038d-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="4038d-172">Yerel sistem (LS)-zaten erişime sahipti.</span><span class="sxs-lookup"><span data-stu-id="4038d-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="4038d-173">Yerleşik kullanıcılar-erişim verilecek grup.</span><span class="sxs-lookup"><span data-stu-id="4038d-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="4038d-174">Sağlayıcı kayıt erişimi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="4038d-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="4038d-175">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4038d-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="4038d-176">Rastgele kullanıcılara veya gruplara erişim verme</span><span class="sxs-lookup"><span data-stu-id="4038d-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="4038d-177">Bu bölümdeki örnek, tüm yerel kullanıcılara WMI sağlayıcı kayıt ayrıcalıkları verir.</span><span class="sxs-lookup"><span data-stu-id="4038d-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="4038d-178">İçinde yerleşik olmayan bir kullanıcıya veya gruba erişim vermek istiyorsanız, bu kullanıcı veya grubun güvenlik tanımlayıcısını (SID) edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4038d-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="4038d-179">Rastgele bir kullanıcı için SID almanın basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="4038d-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="4038d-180">Bir yöntem, istenen kullanıcı olarak oturum açıp aşağıdaki kabuk komutunu yayınvermektir.</span><span class="sxs-lookup"><span data-stu-id="4038d-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="4038d-181">Bu, geçerli kullanıcının SID 'sini sağlar, ancak bu yöntem herhangi bir rastgele kullanıcının SID 'sini almak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4038d-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="4038d-182">SID 'yi almaya yönelik başka bir yöntem, [yönetim görevleri Için Windows 2000 Kaynak Seti araçlarından](https://go.microsoft.com/fwlink/?LinkId=178660) [GETSID. exe](https://go.microsoft.com/fwlink/?LinkId=186467) aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4038d-182">Another method to get the SID is to use the [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](https://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="4038d-183">Bu araç iki kullanıcının (yerel veya etki alanı) SID 'Lerini karşılaştırır ve yan etkisi olarak iki SID 'yi komut satırına yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4038d-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="4038d-184">Daha fazla bilgi için bkz. [tanınmış SID 'ler](https://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="4038d-184">For more information, see [Well Known SIDs](https://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="4038d-185">Uzak WMI nesne örneklerine erişme</span><span class="sxs-lookup"><span data-stu-id="4038d-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="4038d-186">Uzak bir makinedeki WCF WMI örneklerine erişmeniz gerekiyorsa, erişim için kullandığınız araçlarda paket gizliliğini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4038d-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="4038d-187">Aşağıdaki bölümde, bu, WMI CıM Studio, Windows Yönetim Araçları Sınayıcısı ve .NET SDK 2,0 ile nasıl elde edileceğini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="4038d-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="4038d-188">WMI CıM Studio</span><span class="sxs-lookup"><span data-stu-id="4038d-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="4038d-189">[WMI yönetim araçları](https://go.microsoft.com/fwlink/?LinkId=95185)'nı yüklediyseniz WMI örneklerine erışmek IÇIN WMI CIM Studio 'yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="4038d-190">Araçlar şu klasörlerdir</span><span class="sxs-lookup"><span data-stu-id="4038d-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="4038d-191">**%windir%\Program Files\WMI araçları\\**</span><span class="sxs-lookup"><span data-stu-id="4038d-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="4038d-192">**Ad alanına bağlan:** penceresinde, **Root\servicemodel** yazın ve Tamam ' a tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="4038d-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="4038d-193">**WMI CIM Studio oturumu açma** penceresinde, **seçenekleri > >** düğmesine tıklayarak pencereyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="4038d-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="4038d-194">**Kimlik doğrulama düzeyi**için **paket gizliliği** ' ni seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4038d-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="4038d-195">Windows Yönetim Araçları Sınayıcısı</span><span class="sxs-lookup"><span data-stu-id="4038d-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="4038d-196">Bu araç Windows tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4038d-196">This tool is installed by Windows.</span></span> <span data-ttu-id="4038d-197">Çalıştırmak için **Başlat/Çalıştır** iletişim kutusuna **cmd. exe** yazarak bir komut konsolu başlatın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4038d-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="4038d-198">Ardından, komut penceresine **WBEMTest. exe** yazın.</span><span class="sxs-lookup"><span data-stu-id="4038d-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="4038d-199">Windows Yönetim Araçları sınayıcı aracı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4038d-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="4038d-200">Pencerenin sağ üst köşesindeki **Bağlan** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4038d-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="4038d-201">Yeni pencerede, **ad alanı** alanı için **Root\servicemodel** yazın ve **kimlik doğrulama düzeyi**için **paket gizliliği** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="4038d-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="4038d-202">**Bağlan**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4038d-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="4038d-203">Yönetilen kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="4038d-203">Using Managed Code</span></span>  
 <span data-ttu-id="4038d-204">Ayrıca, <xref:System.Management> ad alanı tarafından sunulan sınıfları kullanarak uzak WMI örneklerine da erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4038d-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="4038d-205">Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4038d-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```

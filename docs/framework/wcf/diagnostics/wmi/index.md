---
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: ecc5c754a51a8e1a52797dfd0af0891704eaad1f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591246"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="cf7de-102">Tanılama için Windows Yönetim İzlemesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf7de-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="cf7de-103">Windows Communication Foundation (WCF) hizmetinin çalışma zamanında bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla denetleme verileri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cf7de-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="cf7de-104">WMI etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cf7de-104">Enabling WMI</span></span>  
 <span data-ttu-id="cf7de-105">WMI Web tabanlı kuruluş yönetimi (WBEM) standart Microsoft uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="cf7de-106">WMI SDK'sı hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları'nı](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="cf7de-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="cf7de-107">WBEM, uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı nasıl kullanıma için standart bir endüstri standardıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="cf7de-108">WMI sağlayıcısı izleme çalışma zamanında bir WBEM uyumlu arabirimi üzerinden kullanıma sunan bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="cf7de-109">Bu öznitelik/değer çiftleri olan WMI nesneleri kümesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="cf7de-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="cf7de-110">Birkaç basit türler çiftleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="cf7de-111">Yönetim Araçları hizmetler zamanında arabirimi aracılığıyla bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="cf7de-112">WCF hizmetleri adresler, bağlamalar, davranışları ve dinleyicileri gibi öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="cf7de-113">Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="cf7de-114">Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="cf7de-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="cf7de-115">Bu yapılandırma girişi WMI arabirimini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cf7de-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="cf7de-116">Yönetim uygulamaları artık bu arabirimi üzerinden bağlanabilir ve Yönetim Araçları uygulamanın erişim.</span><span class="sxs-lookup"><span data-stu-id="cf7de-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="cf7de-117">WMI verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="cf7de-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="cf7de-118">WMI verilerini birçok farklı şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="cf7de-119">Microsoft Visual Basic uygulamaları, betikleri için WMI API'lerini sağlar C++ uygulamaları ve .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf7de-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="cf7de-120">Daha fazla bilgi için [WMI kullanarak](https://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="cf7de-120">For more information, see [Using WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cf7de-121">WMI veri programlı olarak erişmek için sağlanan yöntemleri .NET Framework kullanırsanız, tür yöntemler bağlantı kurulduğunda özel durumlar oluşturabilecek farkında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="cf7de-122">Oluşumu sırasında bağlantı kurulmaz <xref:System.Management.ManagementObject> örneği, ancak ilk istek gerçek veri değişimi ilgili.</span><span class="sxs-lookup"><span data-stu-id="cf7de-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="cf7de-123">Bu nedenle, kullanması gereken bir `try..catch` olası özel durumları yakalama bloğu.</span><span class="sxs-lookup"><span data-stu-id="cf7de-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="cf7de-124">İzleme ve ileti günlüğe kaydetme düzeyi yanı için ileti günlüğe kaydetme seçenekleri değiştirebilirsiniz `System.ServiceModel` WMI izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="cf7de-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="cf7de-125">Bu erişerek yapılabilir [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) bu Boolean özellikleri sunan bir örneği: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, ve `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="cf7de-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="cf7de-126">Bu nedenle, İzleme dinleyicisi için ileti günlüğe kaydetmeyi yapılandırın, ancak ayarlayın, bu seçenekleri için `false` yapılandırması, daha sonra bunları değiştirebilirsiniz `true` uygulama çalışırken.</span><span class="sxs-lookup"><span data-stu-id="cf7de-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="cf7de-127">Bu durum, ileti günlüğe kaydetme, çalışma zamanında etkili bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="cf7de-128">Yapılandırma dosyanızda günlük iletisi etkinleştirirseniz, benzer şekilde, size, WMI'yı kullanarak çalışma zamanında devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="cf7de-129">Bilmeniz gereken olması durumunda ileti günlüğünü izleme dinleyicileri ileti günlüğe kaydetme veya no `System.ServiceModel` izleme dinleyicilerine izleme için yapılandırma dosyasında belirtilen, değişiklikleri WMI tarafından kabul edilir olsa da, değişikliklerin hiçbiri etkili olur, alınır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="cf7de-130">Düzgün bir şekilde ilgili dinleyicileri ayarlama hakkında daha fazla bilgi için bkz. [iletileri günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) ve [yapılandırma izleme](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="cf7de-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="cf7de-131">Uygulama başladığında yapılandırması tarafından belirtilen diğer tüm izleme kaynakları izleme düzeyini etkilidir ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="cf7de-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="cf7de-132">WCF sunan bir `GetOperationCounterInstanceName` komut dosyası için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf7de-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="cf7de-133">Bir işlem adıyla sağlarsanız, bu yöntem bir performans sayacı örneği adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf7de-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="cf7de-134">Ancak, giriş doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-134">However, it does not validate your input.</span></span> <span data-ttu-id="cf7de-135">Hatalı işlem adı sağlarsanız, bu nedenle, bir yanlış sayaç adı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cf7de-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="cf7de-136">`OutgoingChannel` Özelliği `Service` örneği başka bir hizmete bağlanmak için bir hizmet içinde hedef hizmeti WCF istemcisi oluşturulmamışsa açan kanalları sayısı değil `Service` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf7de-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="cf7de-137">**Uyarı** WMI yalnızca destekleyen bir <xref:System.TimeSpan> en fazla 3 ondalık nokta değeri.</span><span class="sxs-lookup"><span data-stu-id="cf7de-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="cf7de-138">Örneğin, hizmetiniz için özelliklerinden birini ayarlar <xref:System.TimeSpan.MaxValue>, değeri WMI aracılığıyla görüntülendiğinde 3 ondalık nokta sonrasında kesilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="cf7de-139">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="cf7de-139">Security</span></span>  
 <span data-ttu-id="cf7de-140">WCF WMI sağlayıcısı, bir ortamda Hizmetleri bulma izin verdiğinden, sizin ona erişim izni verme için dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="cf7de-141">Varsayılan yalnızca yönetici erişimi yöntemlerinde, ortamınızda en az güvenilen taraf hassas verilere erişimi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="cf7de-142">WMI uzaktan erişim izinlerini çözmek, özellikle saldırıları taşmasını ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="cf7de-143">Bir işlem tarafından aşırı WMI isteklerini kurtarılmakta, kendi performans düşebilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="cf7de-144">Ayrıca, MOF dosyasını erişim izinlerini hafifletin, en az güvenilen taraf WMI davranışını değiştirmek ve WMI Şeması nesneleri değiştirme.</span><span class="sxs-lookup"><span data-stu-id="cf7de-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="cf7de-145">Örneğin, alanlar, kritik veri Yöneticisi'nden altına gizlenmiş veya dosyaya doldurmak veya özel durumlarına neden alanlar eklenmiş şekilde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="cf7de-146">Varsayılan olarak, "yürütme yöntemi", WCF WMI sağlayıcısı verir. "Sağlayıcı yazma" ve "hesabı etkinleştir" izni için ASP.NET, yerel hizmet ve ağ hizmeti ve yönetici "hesabı etkinleştir" izin.</span><span class="sxs-lookup"><span data-stu-id="cf7de-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="cf7de-147">Özellikle, şirket dışı[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformları, ASP.NET hesabı okuyun ServiceModel WMI ad alanına erişimi.</span><span class="sxs-lookup"><span data-stu-id="cf7de-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="cf7de-148">Belirli bir kullanıcı grubuna Bu ayrıcalıkları vermek istemiyorsanız (varsayılan olarak devre dışıdır) WMI sağlayıcısı devre dışı bırakmak veya erişimi belirli bir kullanıcı grubu için devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="cf7de-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="cf7de-149">WMI aracılığıyla yapılandırması etkinleştirmeye çalıştığınızda, buna ek olarak, WMI yetersiz kullanıcı ayrıcalıkların yetersizliği etkinleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="cf7de-150">Ancak, olay, bu hatayı kaydetmek için olay günlüğüne yazılır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="cf7de-151">Kullanıcı ayrıcalık düzeyleri değiştirmek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf7de-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="cf7de-152">Başlat'a tıklayın ve ardından çalıştırın ve türü **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="cf7de-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="cf7de-153">Sağ **Hizmetleri ve uygulama/WMI denetimleri** seçilecek **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="cf7de-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="cf7de-154">Seçin **güvenlik** sekmesine gidin **kök/ServiceModel** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cf7de-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="cf7de-155">Tıklayın **güvenlik** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cf7de-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="cf7de-156">Belirli bir grup veya erişimi denetlemek ve kullanmak istediğiniz kullanıcıyı seçin **izin** veya **Reddet** izinlerini yapılandırmak için onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="cf7de-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="cf7de-157">Ek kullanıcılar için WCF WMI kayıt izinleri veriliyor</span><span class="sxs-lookup"><span data-stu-id="cf7de-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="cf7de-158">WCF WMI yönetimi verilerini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cf7de-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="cf7de-159">Bunu bir "ayrılmış sağlayıcı" olarak da adlandırılan bir işlem içi WMI sağlayıcısı barındırarak yapar.</span><span class="sxs-lookup"><span data-stu-id="cf7de-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="cf7de-160">Yönetim verilerini sağlamak bu sağlayıcısını Kaydet hesabı uygun izinlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="cf7de-161">Windows ayrıcalıklı hesaplar yalnızca küçük bir kümesi, varsayılan olarak ayrılmış sağlayıcılar kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="cf7de-162">Kullanıcıların yaygın olarak WMI verilerinden varsayılan kümede olmayan bir hesap altında çalışan bir WCF Hizmeti kullanıma sunmak istediğiniz bir sorun olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="cf7de-163">Bu erişimi sağlamak için yönetici aşağıdaki sırayla ek hesap aşağıdaki izinleri vermeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="cf7de-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="cf7de-164">WCF WMI Namespace'için erişim izni.</span><span class="sxs-lookup"><span data-stu-id="cf7de-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="cf7de-165">WCF ayrılmış WMI sağlayıcısını kaydetme izni.</span><span class="sxs-lookup"><span data-stu-id="cf7de-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="cf7de-166">WMI ad alanı erişim izni vermek için</span><span class="sxs-lookup"><span data-stu-id="cf7de-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="cf7de-167">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf7de-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="cf7de-168">Bu PowerShell Betiği, "kök/servicemodel" WMI ad alanına yerleşik kullanıcı grubu erişimi vermek için Güvenlik Tanımlayıcısı Tanım Dili (SDDL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="cf7de-169">Aşağıdaki EDL'ler belirtir:</span><span class="sxs-lookup"><span data-stu-id="cf7de-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="cf7de-170">Yerleşik yönetici (BA) - erişim zaten var.</span><span class="sxs-lookup"><span data-stu-id="cf7de-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="cf7de-171">Ağ Hizmeti (NS) - zaten erişebiliyordu.</span><span class="sxs-lookup"><span data-stu-id="cf7de-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="cf7de-172">Yerel Sistem (LS) - erişim zaten var.</span><span class="sxs-lookup"><span data-stu-id="cf7de-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="cf7de-173">Yerleşik kullanıcılar - erişim izni vermek için bir grup.</span><span class="sxs-lookup"><span data-stu-id="cf7de-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="cf7de-174">Sağlayıcı vermek için kayıt erişim</span><span class="sxs-lookup"><span data-stu-id="cf7de-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="cf7de-175">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf7de-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="cf7de-176">Rastgele kullanıcılara veya gruplara erişim izni verme</span><span class="sxs-lookup"><span data-stu-id="cf7de-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="cf7de-177">Bu bölümdeki örnek, tüm yerel kullanıcılar için WMI sağlayıcısı kayıt ayrıcalıklar verir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="cf7de-178">Ardından kullanıcı veya yerleşik olmayan bir gruba erişim vermek istiyorsanız, bu kullanıcı veya grubun güvenlik tanımlayıcısı (SID) almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="cf7de-179">Herhangi bir kullanıcı için SID almak için basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="cf7de-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="cf7de-180">İstenen kullanıcı olarak oturum açın ve ardından aşağıdaki Kabuk komutu vermek için bir yöntem var.</span><span class="sxs-lookup"><span data-stu-id="cf7de-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="cf7de-181">Bu, geçerli kullanıcının SID'si sağlar, ancak bu yöntem, üzerinde herhangi bir kullanıcı SID almak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="cf7de-182">SID almak için başka bir yöntem [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) gelen aracı [Windows 2000 Kaynak Seti Araçları yönetim görevleri için](https://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="cf7de-182">Another method to get the SID is to use the [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](https://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="cf7de-183">SID (yerel veya etki alanı) iki kullanıcı bu aracı karşılaştırır ve bir yan etkisi komut satırına iki SID yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="cf7de-184">Daha fazla bilgi için [iyi bilinen SID](https://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="cf7de-184">For more information, see [Well Known SIDs](https://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="cf7de-185">Uzak WMI nesne örneklerini erişme</span><span class="sxs-lookup"><span data-stu-id="cf7de-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="cf7de-186">Uzak makinede WCF WMI örnekleri erişmeniz gerekiyorsa, paket gizlilik erişmek için kullandığınız araçları etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="cf7de-187">Aşağıdaki bölümde, WMI CIM Studio, Windows Yönetim Araçları Sınayıcısı, hem de .NET SDK 2. 0'ı kullanarak bu elde etmek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf7de-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="cf7de-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="cf7de-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="cf7de-189">Yüklediyseniz [WMI Yönetimsel Araçlar](https://go.microsoft.com/fwlink/?LinkId=95185), erişim WMI örnekleri için WMI CIM Studio kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="cf7de-190">Araçlar, aşağıdaki klasörde yer</span><span class="sxs-lookup"><span data-stu-id="cf7de-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="cf7de-191">**%windir%\Program Files\WMI araçları\\**</span><span class="sxs-lookup"><span data-stu-id="cf7de-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="cf7de-192">İçinde **ad Connect:** penceresinde, tür **root\ServiceModel** tıklatıp **Tamam.**</span><span class="sxs-lookup"><span data-stu-id="cf7de-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="cf7de-193">İçinde **WMI CIM Studio oturum açma** penceresinde tıklayın **Seçenekleri >>** düğmesini penceresini genişletin.</span><span class="sxs-lookup"><span data-stu-id="cf7de-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="cf7de-194">Seçin **paket gizlilik** için **kimlik doğrulama düzeyi**, tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cf7de-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="cf7de-195">Windows Yönetim Araçları test aracı</span><span class="sxs-lookup"><span data-stu-id="cf7de-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="cf7de-196">Bu araç, Windows tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-196">This tool is installed by Windows.</span></span> <span data-ttu-id="cf7de-197">Çalıştırmak için yazarak bir komut konsolunu Başlat **cmd.exe** içinde **başlangıç/çalıştırma** iletişim kutusu ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cf7de-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="cf7de-198">Ardından yazın **wbemtest.exe** komut penceresinde.</span><span class="sxs-lookup"><span data-stu-id="cf7de-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="cf7de-199">Windows Yönetim Araçları Sınayıcısı aracı sonra başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="cf7de-200">Tıklayın **Connect** pencerenin sağ üst köşesindeki düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cf7de-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="cf7de-201">Yeni pencerede girin **root\ServiceModel** için **Namespace** alan ve seçim **paket gizlilik** için **kimlik doğrulama düzeyi**.</span><span class="sxs-lookup"><span data-stu-id="cf7de-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="cf7de-202">**Bağlan**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cf7de-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="cf7de-203">Yönetilen kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="cf7de-203">Using Managed Code</span></span>  
 <span data-ttu-id="cf7de-204">Ayrıca uzak WMI örnekleri program aracılığıyla tarafından sağlanan sınıfları kullanarak erişebileceğiniz <xref:System.Management> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cf7de-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="cf7de-205">Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```

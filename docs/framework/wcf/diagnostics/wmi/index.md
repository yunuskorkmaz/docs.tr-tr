---
description: 'Hakkında daha fazla bilgi edinin: Tanılama için Windows Yönetim Araçları kullanma'
title: Tanılama için Windows Yönetim İzlemesini Kullanma
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 508422e8e060e608032d7ed22c5736c56c838f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653881"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="25d00-103">Tanılama için Windows Yönetim İzlemesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="25d00-103">Using Windows Management Instrumentation for Diagnostics</span></span>

<span data-ttu-id="25d00-104">Windows Communication Foundation (WCF) bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla çalışma zamanında bir hizmetin İnceleme verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d00-104">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="25d00-105">WMI etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="25d00-105">Enabling WMI</span></span>  

 <span data-ttu-id="25d00-106">WMI, Microsoft 'un Web-Based Kurumsal Yönetim (WBEM) standardı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="25d00-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="25d00-107">WMI SDK hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="25d00-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="25d00-108">WBEM, uygulamaların yönetim araçları 'nı dış yönetim araçlarına nasıl sergilekullandığını gösteren bir sektör standardıdır.</span><span class="sxs-lookup"><span data-stu-id="25d00-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="25d00-109">WMI sağlayıcısı, çalışma zamanında WBEM ile uyumlu bir arabirim aracılığıyla izleme sunan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="25d00-109">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="25d00-110">Öznitelik/değer çiftlerine sahip bir WMI nesneleri kümesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="25d00-110">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="25d00-111">Çiftler bir dizi basit türden olabilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-111">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="25d00-112">Yönetim Araçları, çalışma zamanında arabirim aracılığıyla hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-112">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="25d00-113">WCF, adresler, bağlamalar, davranışlar ve dinleyicileri gibi hizmetlerin özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d00-113">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="25d00-114">Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-114">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="25d00-115">Bu, `wmiProviderEnabled` [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) Aşağıdaki örnek yapılandırmada gösterildiği gibi bölümünde öğesinin özniteliği aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="25d00-115">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="25d00-116">Bu yapılandırma girişi bir WMI arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="25d00-116">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="25d00-117">Yönetim uygulamaları artık bu arabirimden bağlanabilir ve uygulamanın yönetim araçlarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-117">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="25d00-118">WMI verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="25d00-118">Accessing WMI Data</span></span>  

 <span data-ttu-id="25d00-119">WMI verilerine birçok farklı yolla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-119">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="25d00-120">Microsoft, betikler, Visual Basic uygulamalar, C++ uygulamaları ve .NET Framework için WMI API 'Leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="25d00-120">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="25d00-121">Daha fazla bilgi için bkz. [WMI kullanma](/windows/win32/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="25d00-121">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="25d00-122">WMI verilerine programlı olarak erişmek için .NET Framework sağlanan yöntemleri kullanırsanız, bu tür yöntemlerin bağlantı kurulurken özel durumlar oluşturduğunu bilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="25d00-122">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="25d00-123">Bu bağlantı, örneğin oluşturulması sırasında <xref:System.Management.ManagementObject> , ancak gerçek veri değişimini içeren ilk istekte kurulmaz.</span><span class="sxs-lookup"><span data-stu-id="25d00-123">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="25d00-124">Bu nedenle, `try..catch` olası özel durumları yakalamak için bir blok kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d00-124">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="25d00-125">İzleme ve mesaj günlüğü düzeyini, `System.ServiceModel` WMI 'daki izleme kaynağı için de ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d00-125">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="25d00-126">Bu, bu Boole özelliklerini sunan [AppDomainInfo](appdomaininfo.md) örneğine erişerek yapılabilir: `LogMessagesAtServiceLevel` , `LogMessagesAtTransportLevel` , `LogMalformedMessages` ve `TraceLevel` .</span><span class="sxs-lookup"><span data-stu-id="25d00-126">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="25d00-127">Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri `false` yapılandırma bölümünde ayarlarsanız, daha sonra `true` uygulamanın çalıştığı zaman olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d00-127">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="25d00-128">Bu işlem, çalışma zamanında ileti günlüğe kaydetmeyi etkin bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="25d00-128">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="25d00-129">Benzer şekilde, yapılandırma dosyanızda ileti günlüğünü etkinleştirirseniz, WMI kullanarak çalışma zamanında devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d00-129">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="25d00-130">İleti günlüğe kaydetme için hiçbir ileti günlüğe kaydetme veya `System.ServiceModel` yapılandırma dosyasında izleme dinleyicilerinin belirtilmediği durumlarda, DEĞIŞIKLIKLER WMI tarafından kabul edilse de, değişikliklerinizin etkin olmadığı farkında olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="25d00-130">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="25d00-131">İlgili dinleyicileri doğru şekilde ayarlama hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../configuring-message-logging.md) ve [izlemeyi yapılandırma](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="25d00-131">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="25d00-132">Yapılandırma tarafından belirtilen diğer tüm izleme kaynaklarının izleme düzeyi uygulama başlatıldığında etkilidir ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="25d00-132">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="25d00-133">WCF, `GetOperationCounterInstanceName` komut dosyası oluşturmak için bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="25d00-133">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="25d00-134">Bu yöntem, bir işlem adı ile sağlarsanız bir performans sayacı örnek adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="25d00-134">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="25d00-135">Ancak, girişinizi doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="25d00-135">However, it does not validate your input.</span></span> <span data-ttu-id="25d00-136">Bu nedenle, yanlış bir işlem adı sağlarsanız, yanlış bir sayaç adı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25d00-136">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="25d00-137">`OutgoingChannel`Örneğin özelliği, `Service` hedef HIZMETE yönelik WCF istemcisi yönteminde oluşturulmadıysa başka bir hizmete bağlanmak için bir hizmet tarafından açılan kanalları saymaz `Service` .</span><span class="sxs-lookup"><span data-stu-id="25d00-137">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="25d00-138">**Dikkat** edin WMI yalnızca <xref:System.TimeSpan> 3 ondalık noktaya kadar bir değeri destekler.</span><span class="sxs-lookup"><span data-stu-id="25d00-138">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="25d00-139">Örneğin, hizmetiniz özelliklerinden birini olarak ayarlarsa <xref:System.TimeSpan.MaxValue> , WMI üzerinden görüntülendiğinde 3 ondalık noktadan sonra değeri kesilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-139">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="25d00-140">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="25d00-140">Security</span></span>  

 <span data-ttu-id="25d00-141">WCF WMI sağlayıcısı bir ortamdaki hizmetlerin bulunmasına izin verdiğinden, buna erişim vermek için çok dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d00-141">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="25d00-142">Varsayılan yalnızca yönetici erişimini rahatladıysanız, ortamınızda hassas verilere daha az güvenilir taraflar erişebilmeye izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d00-142">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="25d00-143">Özellikle, uzak WMI erişimiyle ilgili izinleri gevbir şekilde bırakırsanız, taşması saldırıları meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-143">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="25d00-144">Bir işlem aşırı sayıda WMI isteği ile taştığında, performansı düşebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-144">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="25d00-145">Ayrıca, MOF dosyası için erişim izinlerine güveniyorsanız, daha az güvenilir taraflar WMI davranışını değiştirebilir ve WMI şemasında yüklenen nesneleri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-145">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="25d00-146">Örneğin, kritik verilerin yöneticiden kaldırılması veya bir özel durum doldurulmayan veya neden olmayan alanlar dosyaya eklenebileceği için alanlar kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-146">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="25d00-147">Varsayılan olarak, WCF WMI sağlayıcısı yönetici için "yürütme yöntemi", "sağlayıcı yazma" ve "hesabı etkinleştir" iznini ve ASP.NET, yerel hizmet ve ağ hizmeti için "hesabı etkinleştir" iznini verir.</span><span class="sxs-lookup"><span data-stu-id="25d00-147">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="25d00-148">Özellikle, Windows dışı Vista platformlarında, ASP.NET hesabının WMI ServiceModel ad alanına okuma erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="25d00-148">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="25d00-149">Bu ayrıcalıkları belirli bir kullanıcı grubuna vermek istemiyorsanız, WMI sağlayıcısını devre dışı bırakmanız gerekir (varsayılan olarak devre dışıdır) ya da belirli kullanıcı grubu için erişimi devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d00-149">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="25d00-150">Ayrıca, WMI 'yi yapılandırma yoluyla etkinleştirmeye çalıştığınızda, yetersiz kullanıcı ayrıcalıkları nedeniyle WMI etkinleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-150">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="25d00-151">Ancak, bu hatayı kaydetmek için olay günlüğüne hiçbir olay yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="25d00-151">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="25d00-152">Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="25d00-152">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="25d00-153">Başlat ' a ve ardından Çalıştır ' a tıklayıp **compmgmt. msc** yazın.</span><span class="sxs-lookup"><span data-stu-id="25d00-153">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="25d00-154">**Özellikler**' i seçmek için **Hizmetler ve uygulama/WMI denetimleri** öğesine sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="25d00-154">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="25d00-155">**Güvenlik** sekmesini seçin ve **kök/ServiceModel** ad alanına gidin.</span><span class="sxs-lookup"><span data-stu-id="25d00-155">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="25d00-156">**Güvenlik** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="25d00-156">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="25d00-157">Erişimi denetlemek istediğiniz belirli bir grup veya kullanıcıyı seçin ve izinleri yapılandırmak için **Izin ver** veya **Reddet** onay kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="25d00-157">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="25d00-158">Ek kullanıcılara WCF WMI kayıt Izinleri verme</span><span class="sxs-lookup"><span data-stu-id="25d00-158">Granting WCF WMI Registration Permissions to Additional Users</span></span>  

 <span data-ttu-id="25d00-159">WCF, yönetim verilerini WMI 'ya gösterir.</span><span class="sxs-lookup"><span data-stu-id="25d00-159">WCF exposes management data to WMI.</span></span> <span data-ttu-id="25d00-160">Bu işlemi, bazen "ayrılmış sağlayıcı" olarak adlandırılan işlem içi bir WMI sağlayıcısını barındırarak yapar.</span><span class="sxs-lookup"><span data-stu-id="25d00-160">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="25d00-161">Yönetim verilerinin açığa çıkarılması için, bu sağlayıcıyı kaydeden hesabın uygun izinlere sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d00-161">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="25d00-162">Windows 'da, yalnızca küçük bir ayrıcalıklı hesap kümesi varsayılan olarak ayrılmış sağlayıcıları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="25d00-162">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="25d00-163">Bu bir sorun olduğundan, kullanıcılar genellikle varsayılan kümesinde olmayan bir hesap altında çalışan bir WCF hizmetinden WMI verilerini açığa çıkarmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="25d00-163">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="25d00-164">Bu erişimi sağlamak için, yöneticinin ek hesaba aşağıdaki sırayla aşağıdaki izinleri vermesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="25d00-164">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="25d00-165">WCF WMI ad alanına erişme izni.</span><span class="sxs-lookup"><span data-stu-id="25d00-165">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="25d00-166">WCF ayrılmış WMI sağlayıcısını kaydetme izni.</span><span class="sxs-lookup"><span data-stu-id="25d00-166">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="25d00-167">WMI ad alanı erişim izni vermek için</span><span class="sxs-lookup"><span data-stu-id="25d00-167">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="25d00-168">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="25d00-168">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="25d00-169">Bu PowerShell betiği, Built-In kullanıcılarına "root/ServiceModel" WMI ad alanına erişim izni vermek için güvenlik tanımlayıcısı tanım dili (SDDL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="25d00-169">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="25d00-170">Aşağıdaki ACL 'Leri belirtir:</span><span class="sxs-lookup"><span data-stu-id="25d00-170">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="25d00-171">Built-In Yöneticisi (BA)-zaten erişime sahipti.</span><span class="sxs-lookup"><span data-stu-id="25d00-171">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="25d00-172">Ağ hizmeti (NS)-zaten erişime sahipti.</span><span class="sxs-lookup"><span data-stu-id="25d00-172">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="25d00-173">Yerel sistem (LS)-zaten erişime sahipti.</span><span class="sxs-lookup"><span data-stu-id="25d00-173">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="25d00-174">Built-In kullanıcılar-erişim izni verilecek grup.</span><span class="sxs-lookup"><span data-stu-id="25d00-174">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="25d00-175">Sağlayıcı kayıt erişimi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="25d00-175">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="25d00-176">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="25d00-176">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="25d00-177">Rastgele kullanıcılara veya gruplara erişim verme</span><span class="sxs-lookup"><span data-stu-id="25d00-177">Granting Access to Arbitrary Users or Groups</span></span>  

 <span data-ttu-id="25d00-178">Bu bölümdeki örnek, tüm yerel kullanıcılara WMI sağlayıcı kayıt ayrıcalıkları verir.</span><span class="sxs-lookup"><span data-stu-id="25d00-178">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="25d00-179">İçinde yerleşik olmayan bir kullanıcıya veya gruba erişim vermek istiyorsanız, bu kullanıcı veya grubun güvenlik tanımlayıcısını (SID) edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d00-179">If you want to grant access to a user or group that is not built in, then you must obtain that user or group's Security Identifier (SID).</span></span> <span data-ttu-id="25d00-180">Rastgele bir kullanıcı için SID almanın basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="25d00-180">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="25d00-181">Bir yöntem, istenen kullanıcı olarak oturum açıp aşağıdaki kabuk komutunu yayınvermektir.</span><span class="sxs-lookup"><span data-stu-id="25d00-181">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="25d00-182">Bu, geçerli kullanıcının SID 'sini sağlar, ancak bu yöntem herhangi bir rastgele kullanıcının SID 'sini almak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25d00-182">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="25d00-183">SID 'yi almaya yönelik başka bir yöntem, yönetim görevleri için Windows 2000 Kaynak Seti araçlarından [getsid.exe](/windows/win32/wmisdk/using-wmi) aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="25d00-183">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="25d00-184">Bu araç iki kullanıcının (yerel veya etki alanı) SID 'Lerini karşılaştırır ve yan etkisi olarak iki SID 'yi komut satırına yazdırır.</span><span class="sxs-lookup"><span data-stu-id="25d00-184">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="25d00-185">Daha fazla bilgi için bkz. [tanınmış SID 'ler](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="25d00-185">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="25d00-186">Uzak WMI nesne örneklerine erişme</span><span class="sxs-lookup"><span data-stu-id="25d00-186">Accessing Remote WMI Object Instances</span></span>  

 <span data-ttu-id="25d00-187">Uzak bir makinedeki WCF WMI örneklerine erişmeniz gerekiyorsa, erişim için kullandığınız araçlarda paket gizliliğini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="25d00-187">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="25d00-188">Aşağıdaki bölümde, bu, WMI CıM Studio, Windows Yönetim Araçları Sınayıcısı ve .NET SDK 2,0 ile nasıl elde edileceğini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="25d00-188">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="25d00-189">WMI CıM Studio</span><span class="sxs-lookup"><span data-stu-id="25d00-189">WMI CIM Studio</span></span>

<span data-ttu-id="25d00-190">WMI yönetim araçları 'nı yüklediyseniz WMI örneklerine erişmek için WMI CıM Studio 'Yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d00-190">If you've installed WMI Administrative Tools, you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="25d00-191">Araçlar şu klasörslardır:</span><span class="sxs-lookup"><span data-stu-id="25d00-191">The tools are in the following folder:</span></span>
  
<span data-ttu-id="25d00-192">*%windir%\Program Files\WMI araçları\\*</span><span class="sxs-lookup"><span data-stu-id="25d00-192">*%windir%\Program Files\WMI Tools\\*</span></span>
  
1. <span data-ttu-id="25d00-193">**Ad alanına bağlan:** penceresinde, **Root\servicemodel** yazın ve Tamam ' a tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="25d00-193">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="25d00-194">**WMI CIM Studio oturumu açma** penceresinde, **seçenekleri >>** düğmesine tıklayarak pencereyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="25d00-194">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="25d00-195">**Kimlik doğrulama düzeyi** için **paket gizliliği** ' ni seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="25d00-195">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="25d00-196">Windows Yönetim Araçları Sınayıcısı</span><span class="sxs-lookup"><span data-stu-id="25d00-196">Windows Management Instrumentation Tester</span></span>  

 <span data-ttu-id="25d00-197">Bu araç Windows tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="25d00-197">This tool is installed by Windows.</span></span> <span data-ttu-id="25d00-198">Çalıştırmak için **Başlat/Çalıştır** iletişim kutusuna **cmd.exe** yazarak bir komut konsolu başlatın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="25d00-198">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="25d00-199">Ardından, komut penceresine **wbemtest.exe** yazın.</span><span class="sxs-lookup"><span data-stu-id="25d00-199">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="25d00-200">Windows Yönetim Araçları sınayıcı aracı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="25d00-200">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="25d00-201">Pencerenin sağ üst köşesindeki **Bağlan** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="25d00-201">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="25d00-202">Yeni pencerede, **ad alanı** alanı için **Root\servicemodel** yazın ve **kimlik doğrulama düzeyi** için **paket gizliliği** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="25d00-202">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="25d00-203">**Bağlan**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="25d00-203">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="25d00-204">Yönetilen kodu kullanma</span><span class="sxs-lookup"><span data-stu-id="25d00-204">Using Managed Code</span></span>  

 <span data-ttu-id="25d00-205">Ayrıca, ad alanı tarafından sunulan sınıfları kullanarak uzak WMI örneklerine programlı bir şekilde erişebilirsiniz <xref:System.Management> .</span><span class="sxs-lookup"><span data-stu-id="25d00-205">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="25d00-206">Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="25d00-206">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```

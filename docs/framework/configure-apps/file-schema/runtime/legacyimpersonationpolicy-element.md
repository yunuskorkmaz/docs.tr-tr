---
title: '&lt;Legacyımpersonationpolicy&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196aaa35561cba7925bcd005474cccb393494250
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699891"
---
# <a name="ltlegacyimpersonationpolicygt-element"></a><span data-ttu-id="fc208-102">&lt;Legacyımpersonationpolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="fc208-102">&lt;legacyImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="fc208-103">Windows kimliği, geçerli iş parçacığı üzerindeki yürütme içeriği için akış ayarlarından bağımsız olarak zaman uyumsuz noktalar arasında geçmeyen belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc208-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="fc208-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fc208-104">\<configuration></span></span>  
<span data-ttu-id="fc208-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="fc208-105">\<runtime></span></span>  
<span data-ttu-id="fc208-106">\<Legacyımpersonationpolicy ></span><span class="sxs-lookup"><span data-stu-id="fc208-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc208-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc208-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc208-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc208-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fc208-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc208-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc208-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc208-110">Attributes</span></span>  
  
|<span data-ttu-id="fc208-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc208-111">Attribute</span></span>|<span data-ttu-id="fc208-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc208-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fc208-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fc208-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fc208-114">Belirten <xref:System.Security.Principal.WindowsIdentity> bağımsız olarak, zaman uyumsuz noktalar ötesine geçmeyen <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde akış.</span><span class="sxs-lookup"><span data-stu-id="fc208-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fc208-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc208-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fc208-116">Değer</span><span class="sxs-lookup"><span data-stu-id="fc208-116">Value</span></span>|<span data-ttu-id="fc208-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc208-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fc208-118"><xref:System.Security.Principal.WindowsIdentity> bağlı olarak zaman uyumsuz noktalar arasındaki akış <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı için akış.</span><span class="sxs-lookup"><span data-stu-id="fc208-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="fc208-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fc208-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="fc208-120"><xref:System.Security.Principal.WindowsIdentity> bağımsız olarak, zaman uyumsuz noktalar ötesine geçmeyen <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde akış.</span><span class="sxs-lookup"><span data-stu-id="fc208-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc208-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc208-121">Child Elements</span></span>  
 <span data-ttu-id="fc208-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc208-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc208-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc208-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fc208-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc208-124">Element</span></span>|<span data-ttu-id="fc208-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc208-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fc208-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fc208-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fc208-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fc208-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc208-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc208-128">Remarks</span></span>  
 <span data-ttu-id="fc208-129">.NET Framework sürümleri 1.0 ve 1.1 içinde <xref:System.Security.Principal.WindowsIdentity> tüm kullanıcı tanımlı zaman uyumsuz noktalar ötesine geçmeyen.</span><span class="sxs-lookup"><span data-stu-id="fc208-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="fc208-130">.NET Framework sürüm 2.0 ile başlayarak, bir <xref:System.Threading.ExecutionContext> yürütülmekte olan iş parçacığını ve hakkında bilgi içeren nesne akışları uygulama etki alanı içinde zaman uyumsuz noktalar arasında.</span><span class="sxs-lookup"><span data-stu-id="fc208-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="fc208-131"><xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamında bulunur ve bu nedenle de zaman uyumsuz noktalar arasında bir kimliğe bürünülmüş bağlamdaki varsa, bu da akar, yani akar.</span><span class="sxs-lookup"><span data-stu-id="fc208-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="fc208-132">Kullanabileceğiniz .NET Framework 2.0 ile başlayarak, `<legacyImpersonationPolicy>` belirtmek için öğe <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktalar ötesine geçmeyen.</span><span class="sxs-lookup"><span data-stu-id="fc208-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc208-133">Ortak dil çalışma zamanı (CLR), yönetilmeyen kod veya Win32 işlevlere doğrudan çağrılar aracılığıyla değil gibi platform yönetilen kod dışında gerçekleştirilen kimliğe bürünme, yalnızca yönetilen kod kullanarak gerçekleştirilen işlemleri çağırmak kimliğe bürünme farkındadır.</span><span class="sxs-lookup"><span data-stu-id="fc208-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="fc208-134">Yalnızca yönetilen <xref:System.Security.Principal.WindowsIdentity> sürece, nesneler zaman uyumsuz noktalar arasında akış `alwaysFlowImpersonationPolicy` öğe kümesi true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="fc208-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="fc208-135">Ayar `alwaysFlowImpersonationPolicy` öğesi true belirtir Windows kimliği her zaman arasında nasıl kimliğe bürünme gerçekleştirilip gerçekleştirilmediğine bakılmaksızın zaman uyumsuz noktalar, geçen.</span><span class="sxs-lookup"><span data-stu-id="fc208-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="fc208-136">Daha fazla bilgi için bkz: zaman uyumsuz noktalar arasında akan bilgi yönetilmeyen kimliğe bürünme [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="fc208-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="fc208-137">Bu varsayılan davranışı başka iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fc208-137">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="fc208-138">İş parçacığı başına temelinde yönetilen kodda.</span><span class="sxs-lookup"><span data-stu-id="fc208-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="fc208-139">İş parçacığı başına temelinde akışını değiştirerek gösterilmemesini sağlayabilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fc208-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="fc208-140">Ortak dil çalışma zamanı (CLR) yüklemeye çağrısında yönetilmeyen barındırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fc208-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="fc208-141">CLR'yi yüklemek için yönetilmeyen bir barındırma arabiriminin (yerine basit yönetilen bir yürütülebilir dosya) kullandıysanız çağrısında bir özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="fc208-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="fc208-142">İşlemin tümünü Uyumluluk modunu etkinleştirmek için `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) STARTUP_LEGACY_IMPERSONATION için.</span><span class="sxs-lookup"><span data-stu-id="fc208-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="fc208-143">Daha fazla bilgi için [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="fc208-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fc208-144">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="fc208-144">Configuration File</span></span>  
 <span data-ttu-id="fc208-145">Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc208-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="fc208-146">Bir ASP.NET uygulaması için kimliğe bürünme akışı bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.</span><span class="sxs-lookup"><span data-stu-id="fc208-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="fc208-147">Varsayılan olarak ASP.NET kimliğe bürünme akışı aspnet.config dosyasında aşağıdaki yapılandırma ayarlarını kullanarak devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="fc208-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="fc208-148">ASP.NET'te, kimliğe bürünme akışını bunun yerine, izin vermek istiyorsanız aşağıdaki yapılandırma ayarları açıkça kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="fc208-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="fc208-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc208-149">Example</span></span>  
 <span data-ttu-id="fc208-150">Aşağıdaki örnek, Windows kimliği zaman uyumsuz noktalar ötesine geçmeyen eski davranışını belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc208-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc208-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc208-151">See also</span></span>
- [<span data-ttu-id="fc208-152">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fc208-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="fc208-153">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="fc208-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="fc208-154">\<Alwaysflowımpersonationpolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="fc208-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)

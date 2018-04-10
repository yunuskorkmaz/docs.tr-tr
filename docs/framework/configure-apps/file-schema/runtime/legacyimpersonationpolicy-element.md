---
title: '&lt;Legacyımpersonationpolicy&gt; öğesi'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a50ad06026b6ef2f819abefc22016aee29f8ab5
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="ltlegacyimpersonationpolicygt-element"></a><span data-ttu-id="33a90-102">&lt;Legacyımpersonationpolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="33a90-102">&lt;legacyImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="33a90-103">Windows Identity geçerli iş parçacığı üzerinde yürütme bağlamı akış ayarlarına bakılmaksızın zaman uyumsuz noktaları arasında akışını değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="33a90-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="33a90-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="33a90-104">\<configuration></span></span>  
<span data-ttu-id="33a90-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="33a90-105">\<runtime></span></span>  
<span data-ttu-id="33a90-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="33a90-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a90-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33a90-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33a90-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="33a90-108">Attributes and Elements</span></span>  
 <span data-ttu-id="33a90-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33a90-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33a90-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="33a90-110">Attributes</span></span>  
  
|<span data-ttu-id="33a90-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="33a90-111">Attribute</span></span>|<span data-ttu-id="33a90-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33a90-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="33a90-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="33a90-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="33a90-114">Belirleyen <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktaları arasında bağımsız olarak, akış değil <xref:System.Threading.ExecutionContext> akış geçerli iş parçacığının ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33a90-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="33a90-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="33a90-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="33a90-116">Değer</span><span class="sxs-lookup"><span data-stu-id="33a90-116">Value</span></span>|<span data-ttu-id="33a90-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33a90-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="33a90-118"><xref:System.Security.Principal.WindowsIdentity> akışları bağlı olarak zaman uyumsuz noktaları arasında <xref:System.Threading.ExecutionContext> akış geçerli iş parçacığı için ayarları.</span><span class="sxs-lookup"><span data-stu-id="33a90-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="33a90-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="33a90-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="33a90-120"><xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktaları arasında bağımsız olarak, akış değil <xref:System.Threading.ExecutionContext> akış geçerli iş parçacığının ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33a90-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33a90-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="33a90-121">Child Elements</span></span>  
 <span data-ttu-id="33a90-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="33a90-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33a90-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="33a90-123">Parent Elements</span></span>  
  
|<span data-ttu-id="33a90-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="33a90-124">Element</span></span>|<span data-ttu-id="33a90-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33a90-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="33a90-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="33a90-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="33a90-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="33a90-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33a90-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33a90-128">Remarks</span></span>  
 <span data-ttu-id="33a90-129">.NET Framework sürüm 1.0 ve 1.1 <xref:System.Security.Principal.WindowsIdentity> tüm kullanıcı tanımlı zaman uyumsuz noktaları arasında akış değil.</span><span class="sxs-lookup"><span data-stu-id="33a90-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="33a90-130">.NET Framework sürüm 2.0 ile başlayarak, var olan bir <xref:System.Threading.ExecutionContext> şu anda yürütülen iş parçacığı ve hakkında bilgi içeren nesne uygulama etki alanı içinde zaman uyumsuz noktaları arasında akar.</span><span class="sxs-lookup"><span data-stu-id="33a90-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="33a90-131"><xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamı içinde bulunur ve bu nedenle de zaman uyumsuz noktaları arasında bir kimliğe bürünme bağlamı zaten varsa, bu da akar, yani akar.</span><span class="sxs-lookup"><span data-stu-id="33a90-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="33a90-132">.NET Framework 2.0 ile başlayarak, kullanabilirsiniz `<legacyImpersonationPolicy>` belirtmek için öğesi <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktaları arasında akış değil.</span><span class="sxs-lookup"><span data-stu-id="33a90-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33a90-133">Ortak dil çalışma zamanı (CLR), yönetilmeyen kod veya Win32 işlevleri için doğrudan çağrılar aracılığıyla değil platformu ile gibi yönetilen kod dışında gerçekleştirilen kimliğe bürünme yalnızca yönetilen kodu kullanarak gerçekleştirilen işlemler çağırma kimliğe bürünme bilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33a90-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="33a90-134">Yalnızca yönetilen <xref:System.Security.Principal.WindowsIdentity> sürece, nesneleri zaman uyumsuz noktaları arasında akış `alwaysFlowImpersonationPolicy` öğesini ayarlamak true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="33a90-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="33a90-135">Ayarı `alwaysFlowImpersonationPolicy` öğesi true belirtir Windows kimliği her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akan olduğunu.</span><span class="sxs-lookup"><span data-stu-id="33a90-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="33a90-136">Daha fazla bilgi için zaman uyumsuz noktaları arasında akan bilgi yönetilmeyen kimliğe bürünme için bkz: [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="33a90-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="33a90-137">Diğer iki yolla bu varsayılan davranışı değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="33a90-137">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="33a90-138">İş parçacığı başına temelinde yönetilen kodu.</span><span class="sxs-lookup"><span data-stu-id="33a90-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="33a90-139">İş parçacığı başına temelinde akış değiştirerek gizleyebilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="33a90-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="33a90-140">Ortak dil çalışma zamanı (CLR) yüklemek için çağrısında yönetilmeyen barındırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="33a90-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="33a90-141">Yönetilmeyen bir barındırma arabirimi (yerine basit Yönetilen yürütülebilir) CLR yüklemek için kullanılırsa, çağrısında özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="33a90-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="33a90-142">Tüm işlem için Uyumluluk modunu etkinleştirmek için ayarlanmış `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) STARTUP_LEGACY_IMPERSONATION için.</span><span class="sxs-lookup"><span data-stu-id="33a90-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="33a90-143">Daha fazla bilgi için bkz: [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="33a90-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="33a90-144">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="33a90-144">Configuration File</span></span>  
 <span data-ttu-id="33a90-145">Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33a90-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="33a90-146">Bir ASP.NET uygulaması için kimliğe bürünme akış bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.</span><span class="sxs-lookup"><span data-stu-id="33a90-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="33a90-147">Varsayılan olarak ASP.NET kimliğe bürünme akış aspnet.config dosyasında aşağıdaki yapılandırma ayarları kullanarak devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="33a90-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="33a90-148">ASP.NET, bunun yerine, kimliğe bürünme akışını izin vermek istiyorsanız aşağıdaki yapılandırma ayarları açıkça kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="33a90-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="33a90-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="33a90-149">Example</span></span>  
 <span data-ttu-id="33a90-150">Aşağıdaki örnek Windows kimliğini zaman uyumsuz noktaları arasında akış olmayan eski davranışı belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="33a90-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33a90-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33a90-151">See Also</span></span>  
 [<span data-ttu-id="33a90-152">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="33a90-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="33a90-153">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="33a90-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="33a90-154">\<Alwaysflowımpersonationpolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="33a90-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)

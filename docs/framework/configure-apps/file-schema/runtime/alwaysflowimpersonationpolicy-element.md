---
title: "&lt;Alwaysflowımpersonationpolicy&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be1df955f7586848968cb32cd66a4c6889cfffa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a><span data-ttu-id="1a211-102">&lt;Alwaysflowımpersonationpolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="1a211-102">&lt;alwaysFlowImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="1a211-103">Windows Identity her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akan olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a211-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="1a211-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1a211-104">\<configuration></span></span>  
<span data-ttu-id="1a211-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="1a211-105">\<runtime></span></span>  
<span data-ttu-id="1a211-106">\<Alwaysflowımpersonationpolicy ></span><span class="sxs-lookup"><span data-stu-id="1a211-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a211-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a211-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a211-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a211-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1a211-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a211-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a211-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a211-110">Attributes</span></span>  
  
|<span data-ttu-id="1a211-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a211-111">Attribute</span></span>|<span data-ttu-id="1a211-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a211-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1a211-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1a211-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a211-114">Windows kimliğini zaman uyumsuz noktaları arasında akan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a211-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1a211-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a211-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1a211-116">Değer</span><span class="sxs-lookup"><span data-stu-id="1a211-116">Value</span></span>|<span data-ttu-id="1a211-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a211-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1a211-118">Kimlik akan zaman uyumsuz noktaları arasında kimliğe bürünme üzerinden gerçekleştirilir sürece Windows yöntemleri gibi yönetilen <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a211-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="1a211-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1a211-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1a211-120">Windows Identity her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akar.</span><span class="sxs-lookup"><span data-stu-id="1a211-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a211-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a211-121">Child Elements</span></span>  
 <span data-ttu-id="1a211-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="1a211-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a211-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a211-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1a211-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a211-124">Element</span></span>|<span data-ttu-id="1a211-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a211-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1a211-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1a211-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1a211-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1a211-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a211-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a211-128">Remarks</span></span>  
 <span data-ttu-id="1a211-129">.NET Framework sürüm 1.0 ve 1.1, Windows kimliğini zaman uyumsuz noktaları arasında geçmez.</span><span class="sxs-lookup"><span data-stu-id="1a211-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="1a211-130">.NET Framework sürüm 2. 0'da, var olan bir <xref:System.Threading.ExecutionContext> şu anda yürütülen iş parçacığı hakkında bilgi içerir ve uygulama etki alanı içinde zaman uyumsuz noktaları arasında akan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1a211-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="1a211-131"><xref:System.Security.Principal.WindowsIdentity> Da akışları kullanarak kimliğe bürünme ulaşılmıştı sağlanan, zaman uyumsuz noktaları arasında akan bilgilerinin bir parçası olarak yönetilen yöntemleri gibi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> ve platform gibi diğer yollarla üzerinden değil yerel yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="1a211-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="1a211-132">Bu öğe, Windows kimlik kimliğe bürünme nasıl ulaşılmıştı bağımsız olarak zaman uyumsuz noktaları arasında akan belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a211-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="1a211-133">Diğer iki yolla bu varsayılan davranışı değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a211-133">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="1a211-134">İş parçacığı başına temelinde yönetilen kodu.</span><span class="sxs-lookup"><span data-stu-id="1a211-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="1a211-135">İş parçacığı başına temelinde akış değiştirerek gizleyebilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a211-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="1a211-136">Ortak dil çalışma zamanı (CLR) yüklemek için çağrısında yönetilmeyen barındırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1a211-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="1a211-137">Yönetilmeyen bir barındırma arabirimi (yerine basit Yönetilen yürütülebilir) CLR yüklemek için kullanılırsa, çağrısında özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="1a211-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="1a211-138">Tüm işlem için Uyumluluk modunu etkinleştirmek için ayarlanmış `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) için `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span><span class="sxs-lookup"><span data-stu-id="1a211-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="1a211-139">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="1a211-139">Configuration File</span></span>  
 <span data-ttu-id="1a211-140">Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a211-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="1a211-141">Bir ASP.NET uygulaması için kimliğe bürünme akış bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.</span><span class="sxs-lookup"><span data-stu-id="1a211-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="1a211-142">Varsayılan olarak ASP.NET kimliğe bürünme akış aspnet.config dosyasında aşağıdaki yapılandırma ayarları kullanarak devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="1a211-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1a211-143">ASP.NET, bunun yerine, kimliğe bürünme akışını izin vermek istiyorsanız aşağıdaki yapılandırma ayarları açıkça kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="1a211-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="1a211-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a211-144">Example</span></span>  
 <span data-ttu-id="1a211-145">Aşağıdaki örnek, kimliğe bürünme araçlarla yönetilen yöntemleri dışında bile elde yüklendiğinde Windows kimliğini zaman uyumsuz noktaları arasında akar belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a211-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a211-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a211-146">See Also</span></span>  
 [<span data-ttu-id="1a211-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1a211-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1a211-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="1a211-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1a211-149">\<Legacyımpersonationpolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="1a211-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)

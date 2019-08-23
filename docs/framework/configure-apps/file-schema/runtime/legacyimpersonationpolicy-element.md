---
title: <legacyImpersonationPolicy> Öğesi
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
ms.openlocfilehash: da01d0dac2e67d6c0131a2b5965472bbd19213fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927324"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="5af3f-102">\<Legacyımpersonationpolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="5af3f-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="5af3f-103">Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="5af3f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5af3f-104">\<configuration></span></span>  
<span data-ttu-id="5af3f-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="5af3f-105">\<runtime></span></span>  
<span data-ttu-id="5af3f-106">\<Legacyımpersonationpolicy ></span><span class="sxs-lookup"><span data-stu-id="5af3f-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af3f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5af3f-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5af3f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af3f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5af3f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5af3f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5af3f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5af3f-110">Attributes</span></span>  
  
|<span data-ttu-id="5af3f-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5af3f-111">Attribute</span></span>|<span data-ttu-id="5af3f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af3f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5af3f-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5af3f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5af3f-114">Geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> akış ayarlarından bağımsız olarak, öğesinin zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5af3f-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5af3f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5af3f-116">Değer</span><span class="sxs-lookup"><span data-stu-id="5af3f-116">Value</span></span>|<span data-ttu-id="5af3f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af3f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5af3f-118"><xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığının <xref:System.Threading.ExecutionContext> akış ayarlarına bağlı olarak zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="5af3f-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="5af3f-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5af3f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5af3f-120"><xref:System.Security.Principal.WindowsIdentity>, geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> akış ayarlarından bağımsız olarak, zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5af3f-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af3f-121">Child Elements</span></span>  
 <span data-ttu-id="5af3f-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5af3f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5af3f-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af3f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5af3f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5af3f-124">Element</span></span>|<span data-ttu-id="5af3f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af3f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5af3f-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5af3f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5af3f-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5af3f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5af3f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5af3f-128">Remarks</span></span>  
 <span data-ttu-id="5af3f-129">1,0 ve 1,1 <xref:System.Security.Principal.WindowsIdentity> .NET Framework sürümlerinde, Kullanıcı tanımlı zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="5af3f-130">.NET Framework sürüm 2,0 ' den başlayarak, şu anda yürütülmekte <xref:System.Threading.ExecutionContext> olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="5af3f-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="5af3f-131">, <xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamına dahil edilmiştir ve bu nedenle zaman uyumsuz noktalara akar, yani bir kimliğe bürünme bağlamı varsa, bu da akacaktır.</span><span class="sxs-lookup"><span data-stu-id="5af3f-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="5af3f-132">.NET Framework 2,0 ' den başlayarak, zaman uyumsuz noktalarda akış `<legacyImpersonationPolicy>` yapmaz öğesini <xref:System.Security.Principal.WindowsIdentity> belirtmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5af3f-133">Ortak dil çalışma zamanı (CLR), yönetilen kod kullanılarak gerçekleştirilen kimliğe bürünme işlemlerinden, yönetilmeyen koda platform çağırma veya doğrudan Win32 işlevlerine yapılan çağrılar aracılığıyla yapılan kimliğe bürünme işlemlerinden haberdar olur.</span><span class="sxs-lookup"><span data-stu-id="5af3f-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="5af3f-134">Öğe true <xref:System.Security.Principal.WindowsIdentity> (`<alwaysFlowImpersonationPolicy enabled="true"/>`) olarak ayarlanmadığı takdirde, yalnızca yönetilen nesneler zaman uyumsuz noktalara `alwaysFlowImpersonationPolicy` akabilir.</span><span class="sxs-lookup"><span data-stu-id="5af3f-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="5af3f-135">`alwaysFlowImpersonationPolicy` Öğesinin true olarak ayarlanması, kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5af3f-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="5af3f-136">Zaman uyumsuz noktalarda yönetilmeyen kimliğe bürünme ile akan hakkında daha fazla bilgi için bkz [ \<. alwaysFlowImpersonationPolicy > öğesi](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="5af3f-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="5af3f-137">Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5af3f-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="5af3f-138">Yönetilen kodda iş parçacığı başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="5af3f-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="5af3f-139"><xref:System.Threading.ExecutionContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>Ve ayarlarını,<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya yönteminikullanarakdeğiştirerekişparçacığıbaşınatemelindeakışıgizleyebilirsiniz<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>. <xref:System.Security.SecurityContext></span><span class="sxs-lookup"><span data-stu-id="5af3f-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="5af3f-140">Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="5af3f-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="5af3f-141">CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="5af3f-142">Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini STARTUP_LEGACY_IMPERSONATION olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5af3f-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="5af3f-143">Daha fazla bilgi için bkz [ \<. alwaysFlowImpersonationPolicy > öğesi](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="5af3f-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5af3f-144">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="5af3f-144">Configuration File</span></span>  
 <span data-ttu-id="5af3f-145">.NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5af3f-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="5af3f-146">Bir ASP.NET uygulaması için, kimliğe bürünme akışı \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan Aspnet. config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5af3f-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="5af3f-147">ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak ASPNET. config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="5af3f-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="5af3f-148">ASP.NET ' de, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="5af3f-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="5af3f-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="5af3f-149">Example</span></span>  
 <span data-ttu-id="5af3f-150">Aşağıdaki örnek, zaman uyumsuz noktalarda Windows kimliğini Flow olmayan eski davranışın nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5af3f-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5af3f-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5af3f-151">See also</span></span>

- [<span data-ttu-id="5af3f-152">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5af3f-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5af3f-153">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5af3f-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5af3f-154">\<alwaysFlowImpersonationPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="5af3f-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)

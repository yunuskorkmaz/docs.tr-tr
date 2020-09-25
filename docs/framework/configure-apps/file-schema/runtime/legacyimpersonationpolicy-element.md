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
ms.openlocfilehash: ca10c809ddf319817aaa074ba5fc3415abf6387d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192522"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="0d008-102">\<legacyImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0d008-102">\<legacyImpersonationPolicy> Element</span></span>

<span data-ttu-id="0d008-103">Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0d008-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="0d008-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d008-104">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d008-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d008-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0d008-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0d008-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d008-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d008-107">Attributes</span></span>  
  
|<span data-ttu-id="0d008-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0d008-108">Attribute</span></span>|<span data-ttu-id="0d008-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d008-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0d008-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0d008-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="0d008-111"><xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> Geçerli iş parçacığındaki akış ayarlarından bağımsız olarak, öğesinin zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0d008-111">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0d008-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0d008-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="0d008-113">Değer</span><span class="sxs-lookup"><span data-stu-id="0d008-113">Value</span></span>|<span data-ttu-id="0d008-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d008-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0d008-115"><xref:System.Security.Principal.WindowsIdentity> geçerli iş parçacığının akış ayarlarına bağlı olarak zaman uyumsuz noktalara akar <xref:System.Threading.ExecutionContext> .</span><span class="sxs-lookup"><span data-stu-id="0d008-115"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="0d008-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0d008-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0d008-117"><xref:System.Security.Principal.WindowsIdentity> , <xref:System.Threading.ExecutionContext> geçerli iş parçacığındaki akış ayarlarından bağımsız olarak, zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0d008-117"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d008-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d008-118">Child Elements</span></span>  

 <span data-ttu-id="0d008-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d008-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d008-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0d008-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0d008-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d008-121">Element</span></span>|<span data-ttu-id="0d008-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d008-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d008-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0d008-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0d008-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0d008-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d008-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d008-125">Remarks</span></span>  

 <span data-ttu-id="0d008-126">1,0 ve 1,1 .NET Framework sürümlerinde, <xref:System.Security.Principal.WindowsIdentity> Kullanıcı tanımlı zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0d008-126">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="0d008-127">.NET Framework sürüm 2,0 ' den başlayarak, <xref:System.Threading.ExecutionContext> Şu anda yürütülmekte olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="0d008-127">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="0d008-128">, <xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamına dahil edilmiştir ve bu nedenle zaman uyumsuz noktalara akar, yani bir kimliğe bürünme bağlamı varsa, bu da akacaktır.</span><span class="sxs-lookup"><span data-stu-id="0d008-128">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="0d008-129">.NET Framework 2,0 ' den başlayarak, `<legacyImpersonationPolicy>`  <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktalarda akış yapmaz öğesini belirtmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d008-129">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d008-130">Ortak dil çalışma zamanı (CLR), yönetilen kod kullanılarak gerçekleştirilen kimliğe bürünme işlemlerinden, yönetilmeyen koda platform çağırma veya doğrudan Win32 işlevlerine yapılan çağrılar aracılığıyla yapılan kimliğe bürünme işlemlerinden haberdar olur.</span><span class="sxs-lookup"><span data-stu-id="0d008-130">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="0d008-131"><xref:System.Security.Principal.WindowsIdentity> `alwaysFlowImpersonationPolicy` Öğe true () olarak ayarlanmadığı takdirde, yalnızca yönetilen nesneler zaman uyumsuz noktalara akabilir `<alwaysFlowImpersonationPolicy enabled="true"/>` .</span><span class="sxs-lookup"><span data-stu-id="0d008-131">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="0d008-132">`alwaysFlowImpersonationPolicy`Öğesinin true olarak ayarlanması, kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d008-132">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="0d008-133">Zaman uyumsuz noktalarda yönetilmeyen kimliğe bürünme ile akan hakkında daha fazla bilgi için bkz. [ \<alwaysFlowImpersonationPolicy> öğesi](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="0d008-133">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="0d008-134">Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d008-134">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="0d008-135">Yönetilen kodda iş parçacığı başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="0d008-135">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="0d008-136"><xref:System.Threading.ExecutionContext>Ve <xref:System.Security.SecurityContext> ayarlarını <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> , <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemini kullanarak değiştirerek iş parçacığı başına temelinde akışı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d008-136">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="0d008-137">Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="0d008-137">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="0d008-138">CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d008-138">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="0d008-139">Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevinin](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini STARTUP_LEGACY_IMPERSONATION olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d008-139">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="0d008-140">Daha fazla bilgi için, bkz. [ \<alwaysFlowImpersonationPolicy> öğesi](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="0d008-140">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0d008-141">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="0d008-141">Configuration File</span></span>  

 <span data-ttu-id="0d008-142">.NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d008-142">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="0d008-143">Bir ASP.NET uygulaması için, kimliğe bürünme akışı \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir \<Windows Folder> .</span><span class="sxs-lookup"><span data-stu-id="0d008-143">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="0d008-144">ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="0d008-144">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="0d008-145">ASP.NET ' de, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0d008-145">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="0d008-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d008-146">Example</span></span>  

 <span data-ttu-id="0d008-147">Aşağıdaki örnek, zaman uyumsuz noktalarda Windows kimliğini Flow olmayan eski davranışın nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d008-147">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d008-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d008-148">See also</span></span>

- [<span data-ttu-id="0d008-149">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0d008-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d008-150">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0d008-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0d008-151">\<alwaysFlowImpersonationPolicy> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="0d008-151">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)

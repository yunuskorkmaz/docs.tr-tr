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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154110"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="3cde9-102">\<legacyImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3cde9-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="3cde9-103">Geçerli iş parçacığı üzerindeki yürütme bağlamının akış ayarlarına bakılmaksızın, Windows kimliğinin eşzamanlı noktalar arasında akmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="3cde9-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3cde9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3cde9-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3cde9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3cde9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="3cde9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cde9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cde9-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cde9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3cde9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3cde9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3cde9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cde9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3cde9-110">Attributes</span></span>  
  
|<span data-ttu-id="3cde9-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3cde9-111">Attribute</span></span>|<span data-ttu-id="3cde9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cde9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3cde9-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3cde9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3cde9-114">Geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> akış ayarlarından bağımsız olarak, asenkron noktalar arasında akmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3cde9-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3cde9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3cde9-116">Değer</span><span class="sxs-lookup"><span data-stu-id="3cde9-116">Value</span></span>|<span data-ttu-id="3cde9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cde9-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3cde9-118"><xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığının akış ayarlarına <xref:System.Threading.ExecutionContext> bağlı olarak asynchronous noktaları boyunca akar.</span><span class="sxs-lookup"><span data-stu-id="3cde9-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="3cde9-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3cde9-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3cde9-120"><xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> akış ayarlarına bakılmaksızın, eşzamanlı noktalar arasında akmaz.</span><span class="sxs-lookup"><span data-stu-id="3cde9-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cde9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3cde9-121">Child Elements</span></span>  
 <span data-ttu-id="3cde9-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="3cde9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cde9-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3cde9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3cde9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="3cde9-124">Element</span></span>|<span data-ttu-id="3cde9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cde9-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3cde9-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3cde9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3cde9-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cde9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cde9-128">Remarks</span></span>  
 <span data-ttu-id="3cde9-129">.NET Framework sürümleri 1.0 ve 1.1'de kullanıcı <xref:System.Security.Principal.WindowsIdentity> tanımlı eşsenkronize noktalar arasında akmaz.</span><span class="sxs-lookup"><span data-stu-id="3cde9-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="3cde9-130">.NET Framework sürüm 2.0 ile başlayarak, şu anda çalıştırılabilen iş parçacığı hakkında bilgi içeren bir <xref:System.Threading.ExecutionContext> nesne vardır ve bir uygulama etki alanı içinde eşzamanlı noktalar arasında akar.</span><span class="sxs-lookup"><span data-stu-id="3cde9-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="3cde9-131">Bu <xref:System.Security.Principal.WindowsIdentity> yürütme bağlamında dahil edilir ve bu nedenle de asynchronous noktaları arasında akar, yani bir kimliğe bürünme bağlamı varsa, o da akacak.</span><span class="sxs-lookup"><span data-stu-id="3cde9-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="3cde9-132">.NET Framework 2.0 ile başlayarak, `<legacyImpersonationPolicy>` eşzamanlı noktalar <xref:System.Security.Principal.WindowsIdentity> arasında akmayan belirtme öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cde9-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cde9-133">Ortak dil çalışma süresi (CLR), yönetilen koda platform çağırma veya Win32 işlevlerine doğrudan çağrılar yoluyla gerçekleştirilen işlevler gibi yönetilen kod dışında gerçekleştirilen kimliğe bürünme işlemleri değil, yalnızca yönetilen kod kullanılarak gerçekleştirilen kimliğe bürünme işlemlerinin farkındadır.</span><span class="sxs-lookup"><span data-stu-id="3cde9-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="3cde9-134">Yalnızca <xref:System.Security.Principal.WindowsIdentity> yönetilen nesneler, öğe doğru olarak ayarlanmadıkça, eşzamanlı noktalar`<alwaysFlowImpersonationPolicy enabled="true"/>`arasında akabilir ( ). `alwaysFlowImpersonationPolicy`</span><span class="sxs-lookup"><span data-stu-id="3cde9-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="3cde9-135">Öğeyi `alwaysFlowImpersonationPolicy` doğru olarak ayarlamak, kimliğe bürünme nasıl gerçekleştirildiğini niçin olursa olsun, Windows kimliğinin her zaman eşzamanlı noktalar arasında aktığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="3cde9-136">Eşzamanlı noktalar arasında yönetilmeyen kimliğe bürünme hakkında daha fazla bilgi [ \<için, her zamanFlowImpersonationPolicy> Öğesi'ne](alwaysflowimpersonationpolicy-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3cde9-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="3cde9-137">Bu varsayılan davranışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3cde9-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="3cde9-138">İş parçacığı başına olarak yönetilen kodda.</span><span class="sxs-lookup"><span data-stu-id="3cde9-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="3cde9-139">İş parçacığı başına <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>akışı, (veya <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi) kullanarak ve ayarları değiştirerek bastırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cde9-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="3cde9-140">Ortak dil çalışma süresini (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="3cde9-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="3cde9-141">CLR'yi yüklemek için yönetilmeyen bir barındırma arabirimi (basit yönetilen çalıştırılabilir lik yerine) kullanılırsa, [CorBindToRuntimeEx Fonksiyonu](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cde9-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="3cde9-142">Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx Fonksiyonu](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) nun parametresini STARTUP_LEGACY_IMPERSONATION ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3cde9-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="3cde9-143">Daha fazla bilgi için [ \<alwaysFlowImpersonationPolicy> Öğesi'ne](alwaysflowimpersonationpolicy-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3cde9-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3cde9-144">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="3cde9-144">Configuration File</span></span>  
 <span data-ttu-id="3cde9-145">Bir .NET Framework uygulamasında, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="3cde9-146">Bir ASP.NET uygulama için, kimliğe bürünme akışı \<Windows Klasörü>\Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="3cde9-147">ASP.NET varsayılan olarak aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3cde9-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="3cde9-148">ASP.NET, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3cde9-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="3cde9-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cde9-149">Example</span></span>  
 <span data-ttu-id="3cde9-150">Aşağıdaki örnek, Windows kimliğini niçin asynchronous noktaları arasında akmayacak eski davranışın nasıl belirtilen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3cde9-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cde9-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cde9-151">See also</span></span>

- [<span data-ttu-id="3cde9-152">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3cde9-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3cde9-153">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3cde9-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3cde9-154">\<alwaysFlowImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3cde9-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)

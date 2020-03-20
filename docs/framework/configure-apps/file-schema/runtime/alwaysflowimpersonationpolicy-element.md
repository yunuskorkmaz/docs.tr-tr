---
title: <alwaysFlowImpersonationPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154489"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="4c15d-102">\<alwaysFlowImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4c15d-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="4c15d-103">Kimliğe bürünme nasıl gerçekleştirildiği ne olursa olsun, Windows kimliğinin her zaman eşzamanlı noktalar arasında aktığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c15d-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="4c15d-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c15d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4c15d-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c15d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="4c15d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolitika>**</span><span class="sxs-lookup"><span data-stu-id="4c15d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="4c15d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c15d-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c15d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c15d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4c15d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c15d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c15d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c15d-110">Attributes</span></span>  
  
|<span data-ttu-id="4c15d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c15d-111">Attribute</span></span>|<span data-ttu-id="4c15d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c15d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4c15d-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c15d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4c15d-114">Windows kimliğinin eşzamanlı noktalar arasında akıp akmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c15d-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4c15d-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c15d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4c15d-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4c15d-116">Value</span></span>|<span data-ttu-id="4c15d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c15d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4c15d-118">Windows kimliği, kimliğe bürünme gibi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>yönetilen yöntemlerle yapılmadığı sürece, eşzamanlı noktalar arasında akmaz.</span><span class="sxs-lookup"><span data-stu-id="4c15d-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="4c15d-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4c15d-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4c15d-120">Windows kimliği, kimliğe bürünme nasıl gerçekleştirildiği ne olursa olsun, her zaman eşzamanlı noktalar arasında akar.</span><span class="sxs-lookup"><span data-stu-id="4c15d-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c15d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c15d-121">Child Elements</span></span>  
 <span data-ttu-id="4c15d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4c15d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c15d-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c15d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4c15d-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c15d-124">Element</span></span>|<span data-ttu-id="4c15d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c15d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4c15d-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4c15d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4c15d-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4c15d-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c15d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c15d-128">Remarks</span></span>  
 <span data-ttu-id="4c15d-129">.NET Framework 1.0 ve 1.1 sürümlerinde, Windows kimliği eşzamanlı noktalar arasında akmaz.</span><span class="sxs-lookup"><span data-stu-id="4c15d-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="4c15d-130">.NET Framework sürüm 2.0'da, <xref:System.Threading.ExecutionContext> şu anda çalıştırılabilen iş parçacığı hakkında bilgi içeren ve bunu bir uygulama etki alanı içindeki eşzamanlı noktalar arasında akan bir nesne vardır.</span><span class="sxs-lookup"><span data-stu-id="4c15d-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="4c15d-131">Ayrıca, <xref:System.Security.Principal.WindowsIdentity> eşzamanlı noktalar arasında akan bilgilerin bir parçası olarak akar, örneğin platform gibi diğer <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemlerle değil, yerel yöntemlere çağrılması gibi yönetilen yöntemler kullanılarak elde edildi.</span><span class="sxs-lookup"><span data-stu-id="4c15d-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="4c15d-132">Bu öğe, kimliğe bürünme nasıl elde edildiklerine bakılmaksızın, Windows kimliğinin eşzamanlı noktalar arasında aktığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c15d-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="4c15d-133">Bu varsayılan davranışı iki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c15d-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="4c15d-134">İş parçacığı başına olarak yönetilen kodda.</span><span class="sxs-lookup"><span data-stu-id="4c15d-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="4c15d-135">İş parçacığı başına <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>akışı, ", <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>" veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi kullanarak ve ayarları değiştirerek bastırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c15d-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="4c15d-136">Ortak dil çalışma süresini (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="4c15d-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="4c15d-137">CLR'yi yüklemek için yönetilmeyen bir barındırma arabirimi (basit yönetilen çalıştırılabilir lik yerine) kullanılırsa, [CorBindToRuntimeEx Fonksiyonu](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c15d-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="4c15d-138">Tüm işlem için uyumluluk modunu etkinleştirmek `flags` için [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Fonksiyonu `STARTUP_ALWAYSFLOW_IMPERSONATION`için parametreyi .</span><span class="sxs-lookup"><span data-stu-id="4c15d-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4c15d-139">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="4c15d-139">Configuration File</span></span>  
 <span data-ttu-id="4c15d-140">Bir .NET Framework uygulamasında, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c15d-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="4c15d-141">Bir ASP.NET uygulama için, kimliğe bürünme akışı \<Windows Klasörü>\Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c15d-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="4c15d-142">ASP.NET varsayılan olarak aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c15d-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4c15d-143">ASP.NET, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="4c15d-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="4c15d-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c15d-144">Example</span></span>  
 <span data-ttu-id="4c15d-145">Aşağıdaki örnek, kimliğe bürünme yönetilen yöntemler dışında araçlarla elde edilse bile, Windows kimliğinin eşzamanlı noktalar arasında aktığını nasıl belirteceğimiz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c15d-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c15d-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c15d-146">See also</span></span>

- [<span data-ttu-id="4c15d-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4c15d-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4c15d-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4c15d-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4c15d-149">\<legacyImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4c15d-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)

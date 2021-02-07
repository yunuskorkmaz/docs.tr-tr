---
description: 'Daha fazla bilgi edinin: <alwaysFlowImpersonationPolicy> öğesi'
title: <alwaysFlowImpersonationPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 5ee8e763eddb810143522ce9e6df780ee77c26c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719376"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="e24aa-103">\<alwaysFlowImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="e24aa-103">\<alwaysFlowImpersonationPolicy> Element</span></span>

<span data-ttu-id="e24aa-104">Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e24aa-104">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="e24aa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e24aa-105">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e24aa-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e24aa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e24aa-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e24aa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e24aa-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e24aa-108">Attributes</span></span>  
  
|<span data-ttu-id="e24aa-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e24aa-109">Attribute</span></span>|<span data-ttu-id="e24aa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e24aa-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e24aa-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e24aa-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e24aa-112">Windows kimliğinin zaman uyumsuz noktalarda akış yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e24aa-112">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e24aa-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e24aa-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e24aa-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e24aa-114">Value</span></span>|<span data-ttu-id="e24aa-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e24aa-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e24aa-116">Kimliğe bürünme, gibi yönetilen yöntemler aracılığıyla gerçekleştirilmediği sürece, Windows kimliği zaman uyumsuz noktalarda akış yapmaz <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .</span><span class="sxs-lookup"><span data-stu-id="e24aa-116">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="e24aa-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="e24aa-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e24aa-118">Windows kimliği, kimliğe bürünme işlemi ne olursa olsun, her zaman zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="e24aa-118">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e24aa-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e24aa-119">Child Elements</span></span>  

 <span data-ttu-id="e24aa-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e24aa-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e24aa-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e24aa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e24aa-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e24aa-122">Element</span></span>|<span data-ttu-id="e24aa-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e24aa-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e24aa-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e24aa-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e24aa-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e24aa-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e24aa-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e24aa-126">Remarks</span></span>  

 <span data-ttu-id="e24aa-127">.NET Framework sürüm 1,0 ve 1,1 ' de, Windows kimliği zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e24aa-127">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="e24aa-128">.NET Framework sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> yürütülmekte olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="e24aa-128">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="e24aa-129"><xref:System.Security.Principal.WindowsIdentity>Aynı zamanda, kimliğe bürünmeyi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> Yerel yöntemlere yönelik platform Invoke gibi diğer yollarla değil, gibi yönetilen yöntemler kullanılarak elde edildiği zaman uyumsuz noktalarda akan bilgilerin bir parçası olarak da akar.</span><span class="sxs-lookup"><span data-stu-id="e24aa-129">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="e24aa-130">Bu öğe, kimliğe bürünme 'nin nasıl elde edildiğini bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akmasını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e24aa-130">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="e24aa-131">Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e24aa-131">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="e24aa-132">Yönetilen kodda iş parçacığı başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="e24aa-132">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="e24aa-133"><xref:System.Threading.ExecutionContext>Ve <xref:System.Security.SecurityContext> ayarlarını <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> ,, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemini kullanarak değiştirerek iş parçacığı başına temelinde akışı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e24aa-133">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="e24aa-134">Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="e24aa-134">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="e24aa-135">CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e24aa-135">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="e24aa-136">Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevinin](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini olarak ayarlayın `STARTUP_ALWAYSFLOW_IMPERSONATION` .</span><span class="sxs-lookup"><span data-stu-id="e24aa-136">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e24aa-137">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="e24aa-137">Configuration File</span></span>  

 <span data-ttu-id="e24aa-138">.NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e24aa-138">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="e24aa-139">Bir ASP.NET uygulaması için, kimliğe bürünme akışı \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir \<Windows Folder> .</span><span class="sxs-lookup"><span data-stu-id="e24aa-139">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="e24aa-140">ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="e24aa-140">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e24aa-141">ASP.NET ' de, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e24aa-141">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e24aa-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="e24aa-142">Example</span></span>  

 <span data-ttu-id="e24aa-143">Aşağıdaki örnek, kimliğe bürünme, yönetilen yöntemlerin dışında bir şekilde elde edildiğinde, Windows kimliğinin zaman uyumsuz noktalarda akışa nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e24aa-143">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e24aa-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e24aa-144">See also</span></span>

- [<span data-ttu-id="e24aa-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e24aa-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e24aa-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e24aa-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e24aa-147">\<legacyImpersonationPolicy> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="e24aa-147">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)

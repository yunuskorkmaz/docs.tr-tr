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
ms.openlocfilehash: 06e91ea6989dcdf0b2a179e7d6ce79b8d9aaff03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118349"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="e2666-102">\<alwaysFlowImpersonationPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="e2666-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="e2666-103">Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2666-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="e2666-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e2666-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2666-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="e2666-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e2666-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysflowımpersonationpolicy >** </span><span class="sxs-lookup"><span data-stu-id="e2666-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="e2666-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2666-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2666-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2666-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2666-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2666-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2666-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2666-110">Attributes</span></span>  
  
|<span data-ttu-id="e2666-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2666-111">Attribute</span></span>|<span data-ttu-id="e2666-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2666-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e2666-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e2666-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e2666-114">Windows kimliğinin zaman uyumsuz noktalarda akış yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2666-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e2666-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2666-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e2666-116">Değer</span><span class="sxs-lookup"><span data-stu-id="e2666-116">Value</span></span>|<span data-ttu-id="e2666-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2666-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e2666-118">Kimliğe bürünme, <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>gibi yönetilen yöntemler aracılığıyla gerçekleştirilmediği sürece, Windows kimliği zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e2666-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="e2666-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e2666-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e2666-120">Windows kimliği, kimliğe bürünme işlemi ne olursa olsun, her zaman zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="e2666-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2666-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2666-121">Child Elements</span></span>  
 <span data-ttu-id="e2666-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e2666-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2666-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2666-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e2666-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2666-124">Element</span></span>|<span data-ttu-id="e2666-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2666-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e2666-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e2666-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e2666-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e2666-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2666-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2666-128">Remarks</span></span>  
 <span data-ttu-id="e2666-129">.NET Framework sürüm 1,0 ve 1,1 ' de, Windows kimliği zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e2666-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="e2666-130">.NET Framework sürüm 2,0 ' de, şu anda yürütülmekte olan iş parçacığı hakkında bilgi içeren bir <xref:System.Threading.ExecutionContext> nesnesi vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="e2666-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="e2666-131"><xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktalarda akan bilgilerin bir parçası olarak akar, kimliğe bürünme, yerel yöntemlere yönelik platform çağırma gibi diğer yollarla değil, <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> gibi yönetilen yöntemler kullanılarak elde edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2666-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="e2666-132">Bu öğe, kimliğe bürünme 'nin nasıl elde edildiğini bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akmasını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2666-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="e2666-133">Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e2666-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="e2666-134">Yönetilen kodda iş parçacığı başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="e2666-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="e2666-135"><xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemini kullanarak <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> ayarlarını değiştirerek akışı her iş parçacığı temelinde gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2666-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="e2666-136">Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="e2666-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="e2666-137">CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2666-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="e2666-138">Tüm işlemin uyumluluk modunu etkinleştirmek için [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) için `flags` parametresini `STARTUP_ALWAYSFLOW_IMPERSONATION`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2666-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e2666-139">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="e2666-139">Configuration File</span></span>  
 <span data-ttu-id="e2666-140">.NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2666-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="e2666-141">Bir ASP.NET uygulaması için, kimliğe bürünme akışı \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan Aspnet. config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2666-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="e2666-142">ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak ASPNET. config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="e2666-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e2666-143">ASP.NET ' de, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e2666-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e2666-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2666-144">Example</span></span>  
 <span data-ttu-id="e2666-145">Aşağıdaki örnek, kimliğe bürünme, yönetilen yöntemlerin dışında bir şekilde elde edildiğinde, Windows kimliğinin zaman uyumsuz noktalarda akışa nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2666-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2666-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2666-146">See also</span></span>

- [<span data-ttu-id="e2666-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e2666-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e2666-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e2666-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e2666-149">\<Legacyımpersonationpolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="e2666-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)

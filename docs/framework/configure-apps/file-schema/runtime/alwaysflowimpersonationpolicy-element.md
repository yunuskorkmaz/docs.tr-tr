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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154489"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="ddd3c-102">\<alwaysFlowImpersonationPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ddd3c-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="ddd3c-103">Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="ddd3c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddd3c-104">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddd3c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddd3c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ddd3c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddd3c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ddd3c-107">Attributes</span></span>  
  
|<span data-ttu-id="ddd3c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ddd3c-108">Attribute</span></span>|<span data-ttu-id="ddd3c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddd3c-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ddd3c-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ddd3c-111">Windows kimliğinin zaman uyumsuz noktalarda akış yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-111">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ddd3c-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ddd3c-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="ddd3c-113">Değer</span><span class="sxs-lookup"><span data-stu-id="ddd3c-113">Value</span></span>|<span data-ttu-id="ddd3c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddd3c-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ddd3c-115">Kimliğe bürünme, gibi yönetilen yöntemler aracılığıyla gerçekleştirilmediği sürece, Windows kimliği zaman uyumsuz noktalarda akış yapmaz <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .</span><span class="sxs-lookup"><span data-stu-id="ddd3c-115">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="ddd3c-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ddd3c-117">Windows kimliği, kimliğe bürünme işlemi ne olursa olsun, her zaman zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-117">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddd3c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddd3c-118">Child Elements</span></span>  
 <span data-ttu-id="ddd3c-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ddd3c-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddd3c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ddd3c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddd3c-121">Element</span></span>|<span data-ttu-id="ddd3c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddd3c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ddd3c-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ddd3c-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddd3c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddd3c-125">Remarks</span></span>  
 <span data-ttu-id="ddd3c-126">.NET Framework sürüm 1,0 ve 1,1 ' de, Windows kimliği zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-126">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="ddd3c-127">.NET Framework sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> yürütülmekte olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-127">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="ddd3c-128"><xref:System.Security.Principal.WindowsIdentity>Aynı zamanda, kimliğe bürünmeyi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> Yerel yöntemlere yönelik platform Invoke gibi diğer yollarla değil, gibi yönetilen yöntemler kullanılarak elde edildiği zaman uyumsuz noktalarda akan bilgilerin bir parçası olarak da akar.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-128">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="ddd3c-129">Bu öğe, kimliğe bürünme 'nin nasıl elde edildiğini bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akmasını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-129">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="ddd3c-130">Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ddd3c-130">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="ddd3c-131">Yönetilen kodda iş parçacığı başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-131">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="ddd3c-132"><xref:System.Threading.ExecutionContext>Ve <xref:System.Security.SecurityContext> ayarlarını <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> ,, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemini kullanarak değiştirerek iş parçacığı başına temelinde akışı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-132">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="ddd3c-133">Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-133">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="ddd3c-134">CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-134">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="ddd3c-135">Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevinin](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini olarak ayarlayın `STARTUP_ALWAYSFLOW_IMPERSONATION` .</span><span class="sxs-lookup"><span data-stu-id="ddd3c-135">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ddd3c-136">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="ddd3c-136">Configuration File</span></span>  
 <span data-ttu-id="ddd3c-137">.NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-137">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="ddd3c-138">Bir ASP.NET uygulaması için, kimliğe bürünme akışı \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan Aspnet. config dosyasında yapılandırılabilir \<Windows Folder> .</span><span class="sxs-lookup"><span data-stu-id="ddd3c-138">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="ddd3c-139">ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak ASPNET. config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="ddd3c-139">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ddd3c-140">ASP.NET ' de, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ddd3c-140">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="ddd3c-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddd3c-141">Example</span></span>  
 <span data-ttu-id="ddd3c-142">Aşağıdaki örnek, kimliğe bürünme, yönetilen yöntemlerin dışında bir şekilde elde edildiğinde, Windows kimliğinin zaman uyumsuz noktalarda akışa nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-142">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddd3c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddd3c-143">See also</span></span>

- [<span data-ttu-id="ddd3c-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="ddd3c-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ddd3c-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ddd3c-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ddd3c-146">\<legacyImpersonationPolicy>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ddd3c-146">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)

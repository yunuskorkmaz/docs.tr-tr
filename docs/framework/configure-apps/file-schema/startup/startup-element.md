---
title: "&lt;Başlangıç&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a502cb309bce3a1a2fb55c9e5477b7a6a395960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="1482e-102">&lt;Başlangıç&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="1482e-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="1482e-103">Ortak dil çalışma zamanı başlangıç bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1482e-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="1482e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1482e-104">\<configuration></span></span>  
<span data-ttu-id="1482e-105">\<Başlangıç ></span><span class="sxs-lookup"><span data-stu-id="1482e-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1482e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1482e-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1482e-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1482e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1482e-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1482e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1482e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1482e-109">Attributes</span></span>  
  
|<span data-ttu-id="1482e-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1482e-110">Attribute</span></span>|<span data-ttu-id="1482e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1482e-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="1482e-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1482e-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1482e-113">Etkinleştirilip etkinleştirilmeyeceğini belirtir [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] çalışma zamanı etkinleştirme İlkesi kullanmak için veya [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] etkinleştirme ilkesi.</span><span class="sxs-lookup"><span data-stu-id="1482e-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="1482e-114">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="1482e-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="1482e-115">Değer</span><span class="sxs-lookup"><span data-stu-id="1482e-115">Value</span></span>|<span data-ttu-id="1482e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1482e-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="1482e-117">Etkinleştirme [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] eski çalışma zamanı etkinleştirme teknikleri bağlamak için seçilen çalışma için çalışma zamanı etkinleştirme İlkesi (gibi [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) yerine yapılandırma dosyasından seçilen çalışma zamanı bunları CLR Version 2.0 sürümü capping.</span><span class="sxs-lookup"><span data-stu-id="1482e-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="1482e-118">Bu nedenle, CLR sürüm 4 veya sonrası yapılandırma dosyasından seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulan karma mod derlemeleri ile seçilen CLR sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1482e-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="1482e-119">Bu değer ayarlandığında CLR sürüm 1.1 veya CLR Version 2.0 sürümü etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma aynı işlemine yüklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="1482e-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="1482e-120">Etkinleştirme için varsayılan bir ilke kullanmak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra eski çalışma zamanı etkinleştirme teknikleri CLR sürüm 1.1 veya 2.0 yükleme işlemine izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="1482e-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="1482e-121">Bu değer ayarlandığında, karma mod derlemeleri .NET Framework 4 veya sonraki sürümüyle oluşturulmuş sürece yüklenmesini .NET Framework 4 veya sonraki engeller.</span><span class="sxs-lookup"><span data-stu-id="1482e-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="1482e-122">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1482e-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1482e-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1482e-123">Child Elements</span></span>  
  
|<span data-ttu-id="1482e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1482e-124">Element</span></span>|<span data-ttu-id="1482e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1482e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1482e-126">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="1482e-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="1482e-127">Uygulamanın yalnızca sürüm 1.0 ortak dil çalışma zamanı desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1482e-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="1482e-128">Çalışma zamanı sürüm 1.1 veya üstünün ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="1482e-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="1482e-129">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="1482e-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="1482e-130">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1482e-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1482e-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1482e-131">Parent Elements</span></span>  
  
|<span data-ttu-id="1482e-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="1482e-132">Element</span></span>|<span data-ttu-id="1482e-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1482e-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1482e-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1482e-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1482e-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1482e-135">Remarks</span></span>  
 <span data-ttu-id="1482e-136"> **\<SupportedRuntime >** öğesi sürüm 1.1 veya üstünün çalışma zamanının kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1482e-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="1482e-137">Yalnızca sürüm 1.0 çalışma zamanının desteklemek için oluşturulan uygulamaların kullanmalıdır  **\<requiredRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="1482e-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="1482e-138">Microsoft Internet Explorer'da barındırılan bir uygulama için başlangıç kodu yoksayar  **\<başlangıç >** öğesi ve kendi alt öğelerini.</span><span class="sxs-lookup"><span data-stu-id="1482e-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="1482e-139">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="1482e-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="1482e-140">Bu öznitelik, uygulamanız eski etkinleştirme yolları gibi kullanıyorsa yararlıdır [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), ve önceki bir sürümünü yerine CLR sürüm 4 etkinleştirmek için bu yollar istediğiniz veya uygulamanız ise ile oluşturulan [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ancak bir bağımlılığa sahip .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derleme üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1482e-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="1482e-141">Bu senaryolarda, öznitelik kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="1482e-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1482e-142">Öznitelik ayarını `true` CLR sürüm 1.1 veya CLR Version 2.0 sürümü aynı işlemine etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma yüklenmesini engeller (bkz [COM birlikte çalışma için yan yana yürütme](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="1482e-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1482e-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="1482e-143">Example</span></span>  
 <span data-ttu-id="1482e-144">Aşağıdaki örnek çalışma zamanı sürümü bir yapılandırma dosyası belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1482e-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1482e-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1482e-145">See Also</span></span>  
 [<span data-ttu-id="1482e-146">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1482e-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="1482e-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="1482e-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1482e-148">\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme</span><span class="sxs-lookup"><span data-stu-id="1482e-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [<span data-ttu-id="1482e-149">COM birlikte çalışma için yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="1482e-149">Side-by-Side Execution for COM Interop</span></span>](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="1482e-150">İşlem İçi Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="1482e-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)

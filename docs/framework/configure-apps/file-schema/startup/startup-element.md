---
description: 'Daha fazla bilgi edinin: <startup> öğesi'
title: <startup> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 82ece56aaa05376237922b3bd54b6f15967adf8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639828"
---
# <a name="startup-element"></a><span data-ttu-id="ab64c-103">\<startup> öğesi</span><span class="sxs-lookup"><span data-stu-id="ab64c-103">\<startup> element</span></span>

<span data-ttu-id="ab64c-104">Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-104">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="ab64c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab64c-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab64c-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ab64c-106">Attributes and elements</span></span>

 <span data-ttu-id="ab64c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab64c-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab64c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab64c-108">Attributes</span></span>

|<span data-ttu-id="ab64c-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ab64c-109">Attribute</span></span>|<span data-ttu-id="ab64c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab64c-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="ab64c-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ab64c-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ab64c-112">.NET Framework 2,0 çalışma zamanı etkinleştirme ilkesinin etkinleştirilip etkinleştirilmeyeceğini veya .NET Framework 4 etkinleştirme ilkesini kullanmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-112">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ab64c-113">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="ab64c-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="ab64c-114">Değer</span><span class="sxs-lookup"><span data-stu-id="ab64c-114">Value</span></span>|<span data-ttu-id="ab64c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab64c-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="ab64c-116">Eski çalışma zamanı etkinleştirme tekniklerini ( [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi) yapılandırma dosyasından seçilen çalışma zamanına bağlamak yerine, bunları CLR sürüm 2,0 ' de kullanmak yerine, seçilen çalışma zamanı için .NET Framework 2,0 çalışma zamanı etkinleştirme ilkesini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ab64c-116">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="ab64c-117">Bu nedenle, yapılandırma dosyasından CLR sürüm 4 veya üzeri seçilirse, önceki .NET Framework sürümleriyle oluşturulan karma mod derlemeleri seçilen CLR sürümü ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="ab64c-118">Bu değeri ayarlamak, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ab64c-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="ab64c-119">.NET Framework 4 ve üzeri için varsayılan etkinleştirme ilkesini kullanarak, eski çalışma zamanı etkinleştirme tekniklerinin işleme yönelik CLR sürüm 1,1 veya 2,0 ' i yüklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="ab64c-120">Bu değeri ayarlamak, karışık mod derlemelerin .NET Framework 4 ' e veya üzeri bir sürüme derlenmedikleri takdirde, .NET Framework 4 veya üzeri bir sürümü ile oluşturulmalarına engel olur.</span><span class="sxs-lookup"><span data-stu-id="ab64c-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="ab64c-121">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ab64c-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ab64c-122">Child elements</span></span>

|<span data-ttu-id="ab64c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab64c-123">Element</span></span>|<span data-ttu-id="ab64c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab64c-124">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="ab64c-125">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-125">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ab64c-126">Çalışma zamanı sürüm 1,1 veya üzeri ile oluşturulan uygulamalar öğesini kullanmalıdır **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="ab64c-126">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="ab64c-127">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-127">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab64c-128">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ab64c-128">Parent elements</span></span>

|<span data-ttu-id="ab64c-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab64c-129">Element</span></span>|<span data-ttu-id="ab64c-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab64c-130">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ab64c-131">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ab64c-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab64c-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab64c-132">Remarks</span></span>

 <span data-ttu-id="ab64c-133">**\<supportedRuntime>** Öğesi, çalışma zamanının 1,1 veya sonraki bir sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab64c-133">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="ab64c-134">Yalnızca çalışma zamanının 1,0 sürümünü desteklemeye yönelik uygulamalar **\<requiredRuntime>** öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab64c-134">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="ab64c-135">Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, **\<startup>** öğesini ve onun alt öğelerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="ab64c-135">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ab64c-136">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="ab64c-136">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="ab64c-137">Bu öznitelik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların daha önceki bir sürüm yerine CLR sürüm 4 ' ü etkinleştirmesini istiyorsanız ya da uygulamanız .NET Framework 4 ile oluşturulup daha önceki bir .NET Framework sürümüyle oluşturulmuş bir karma mod derlemesine bağımlılığı varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ab64c-137">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="ab64c-138">Bu senaryolarda özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="ab64c-138">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="ab64c-139">Özniteliğinin ayarlanması `true` , CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller, işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır (bkz. [com birlikte çalışma Için yan yana yürütme](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="ab64c-139">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="ab64c-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab64c-140">Example</span></span>

 <span data-ttu-id="ab64c-141">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab64c-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab64c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab64c-142">See also</span></span>

- [<span data-ttu-id="ab64c-143">Başlangıç ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="ab64c-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ab64c-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ab64c-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ab64c-145">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ab64c-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="ab64c-146">[COM birlikte çalışması için yan yana yürütme](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ab64c-146">[Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="ab64c-147">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="ab64c-147">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)

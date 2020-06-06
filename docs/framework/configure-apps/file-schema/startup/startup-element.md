---
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
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153743"
---
# <a name="startup-element"></a><span data-ttu-id="13236-102">\<startup> öğesi</span><span class="sxs-lookup"><span data-stu-id="13236-102">\<startup> element</span></span>

<span data-ttu-id="13236-103">Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="13236-103">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="13236-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13236-104">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13236-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="13236-105">Attributes and elements</span></span>

 <span data-ttu-id="13236-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13236-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="13236-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13236-107">Attributes</span></span>

|<span data-ttu-id="13236-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="13236-108">Attribute</span></span>|<span data-ttu-id="13236-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13236-109">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="13236-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="13236-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="13236-111">.NET Framework 2,0 çalışma zamanı etkinleştirme ilkesinin etkinleştirilip etkinleştirilmeyeceğini veya .NET Framework 4 etkinleştirme ilkesini kullanmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="13236-111">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="13236-112">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="13236-112">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="13236-113">Değer</span><span class="sxs-lookup"><span data-stu-id="13236-113">Value</span></span>|<span data-ttu-id="13236-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13236-114">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="13236-115">Eski çalışma zamanı etkinleştirme tekniklerini ( [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi) yapılandırma dosyasından seçilen çalışma zamanına bağlamak yerine, bunları CLR sürüm 2,0 ' de kullanmak yerine, seçilen çalışma zamanı için .NET Framework 2,0 çalışma zamanı etkinleştirme ilkesini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="13236-115">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="13236-116">Bu nedenle, yapılandırma dosyasından CLR sürüm 4 veya üzeri seçilirse, önceki .NET Framework sürümleriyle oluşturulan karma mod derlemeleri seçilen CLR sürümü ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="13236-116">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="13236-117">Bu değeri ayarlamak, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="13236-117">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="13236-118">.NET Framework 4 ve üzeri için varsayılan etkinleştirme ilkesini kullanarak, eski çalışma zamanı etkinleştirme tekniklerinin işleme yönelik CLR sürüm 1,1 veya 2,0 ' i yüklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="13236-118">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="13236-119">Bu değeri ayarlamak, karışık mod derlemelerin .NET Framework 4 ' e veya üzeri bir sürüme derlenmedikleri takdirde, .NET Framework 4 veya üzeri bir sürümü ile oluşturulmalarına engel olur.</span><span class="sxs-lookup"><span data-stu-id="13236-119">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="13236-120">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="13236-120">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="13236-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="13236-121">Child elements</span></span>

|<span data-ttu-id="13236-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="13236-122">Element</span></span>|<span data-ttu-id="13236-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13236-123">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="13236-124">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="13236-124">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="13236-125">Çalışma zamanı sürüm 1,1 veya üzeri ile oluşturulan uygulamalar öğesini kullanmalıdır **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="13236-125">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="13236-126">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="13236-126">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13236-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="13236-127">Parent elements</span></span>

|<span data-ttu-id="13236-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="13236-128">Element</span></span>|<span data-ttu-id="13236-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13236-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="13236-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="13236-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13236-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13236-131">Remarks</span></span>

 <span data-ttu-id="13236-132">**\<supportedRuntime>** Öğesi, çalışma zamanının 1,1 veya sonraki bir sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13236-132">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="13236-133">Yalnızca çalışma zamanının 1,0 sürümünü desteklemeye yönelik uygulamalar **\<requiredRuntime>** öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13236-133">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="13236-134">Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, **\<startup>** öğesini ve onun alt öğelerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="13236-134">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="13236-135">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="13236-135">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="13236-136">Bu öznitelik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların daha önceki bir sürüm yerine CLR sürüm 4 ' ü etkinleştirmesini istiyorsanız ya da uygulamanız .NET Framework 4 ile oluşturulup daha önceki bir .NET Framework sürümüyle oluşturulmuş bir karma mod derlemesine bağımlılığı varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="13236-136">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="13236-137">Bu senaryolarda özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="13236-137">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="13236-138">Özniteliğinin ayarlanması `true` , CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller, işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır (bkz. [com birlikte çalışma Için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="13236-138">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="13236-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="13236-139">Example</span></span>

 <span data-ttu-id="13236-140">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13236-140">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="13236-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13236-141">See also</span></span>

- [<span data-ttu-id="13236-142">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="13236-142">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="13236-143">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="13236-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="13236-144">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="13236-144">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="13236-145">[COM birlikte çalışması için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="13236-145">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="13236-146">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="13236-146">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)

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
ms.openlocfilehash: 634d9c5248c33619abec50d441d95c111febdcbf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699411"
---
# <a name="startup-element"></a><span data-ttu-id="4c27e-102">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="4c27e-102">\<startup> element</span></span>

<span data-ttu-id="4c27e-103">Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="4c27e-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="4c27e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4c27e-105">&nbsp;&nbsp; **\<başlatma >**</span><span class="sxs-lookup"><span data-stu-id="4c27e-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="4c27e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c27e-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c27e-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4c27e-107">Attributes and elements</span></span>

 <span data-ttu-id="4c27e-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c27e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c27e-109">Attributes</span></span>

|<span data-ttu-id="4c27e-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c27e-110">Attribute</span></span>|<span data-ttu-id="4c27e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c27e-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="4c27e-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4c27e-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4c27e-113">.NET Framework 2,0 çalışma zamanı etkinleştirme ilkesinin etkinleştirilip etkinleştirilmeyeceğini veya .NET Framework 4 etkinleştirme ilkesini kullanmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="4c27e-114">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c27e-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="4c27e-115">Değer</span><span class="sxs-lookup"><span data-stu-id="4c27e-115">Value</span></span>|<span data-ttu-id="4c27e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c27e-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="4c27e-117">Eski çalışma zamanı etkinleştirme tekniklerini ( [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi) yapılandırma dosyasından seçilen çalışma zamanına bağlamak yerine, bunları CLR sürüm 2,0 ' de kullanmak yerine, seçilen çalışma zamanı için .NET Framework 2,0 çalışma zamanı etkinleştirme ilkesini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="4c27e-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="4c27e-118">Bu nedenle, yapılandırma dosyasından CLR sürüm 4 veya üzeri seçilirse, önceki .NET Framework sürümleriyle oluşturulan karma mod derlemeleri seçilen CLR sürümü ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="4c27e-119">Bu değeri ayarlamak, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="4c27e-120">.NET Framework 4 ve üzeri için varsayılan etkinleştirme ilkesini kullanarak, eski çalışma zamanı etkinleştirme tekniklerinin işleme yönelik CLR sürüm 1,1 veya 2,0 ' i yüklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="4c27e-121">Bu değeri ayarlamak, karışık mod derlemelerin .NET Framework 4 ' e veya üzeri bir sürüme derlenmedikleri takdirde, .NET Framework 4 veya üzeri bir sürümü ile oluşturulmalarına engel olur.</span><span class="sxs-lookup"><span data-stu-id="4c27e-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="4c27e-122">Bu değer varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4c27e-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4c27e-123">Child elements</span></span>

|<span data-ttu-id="4c27e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c27e-124">Element</span></span>|<span data-ttu-id="4c27e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c27e-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c27e-126">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="4c27e-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="4c27e-127">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="4c27e-128">Çalışma zamanı sürüm 1,1 veya üzeri ile oluşturulan uygulamalar **\<supportedRuntime >** öğesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="4c27e-129">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="4c27e-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="4c27e-130">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4c27e-131">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4c27e-131">Parent elements</span></span>

|<span data-ttu-id="4c27e-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c27e-132">Element</span></span>|<span data-ttu-id="4c27e-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c27e-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4c27e-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4c27e-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4c27e-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c27e-135">Remarks</span></span>

 <span data-ttu-id="4c27e-136">**\<supportedruntime >** öğesi, çalışma zamanının 1,1 veya sonraki bir sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="4c27e-137">Yalnızca çalışma zamanının 1,0 sürümünü desteklemek üzere oluşturulan uygulamalar **\<requiredRuntime >** öğesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="4c27e-138">Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, **\<başlangıç >** öğesini ve onun alt öğelerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="4c27e-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="4c27e-139">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c27e-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="4c27e-140">Bu öznitelik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların daha önceki bir sürüm yerine CLR sürüm 4 ' ü etkinleştirmesini istiyorsanız ya da uygulamanız .NET Framework 4 ile oluşturulup daha önceki bir .NET Framework sürümüyle oluşturulmuş bir karma mod derlemesine bağımlılığı varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c27e-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="4c27e-141">Bu senaryolarda, özniteliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4c27e-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="4c27e-142">Özniteliği `true` olarak ayarlamak, CLR sürüm 1,1 veya CLR sürüm 2,0 ' nin aynı işleme yüklenmesini engeller ve işlem içi yan yana özelliğini etkin bir şekilde devre dışı bırakır (bkz. [com birlikte çalışması Için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="4c27e-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="4c27e-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c27e-143">Example</span></span>

 <span data-ttu-id="4c27e-144">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c27e-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4c27e-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c27e-145">See also</span></span>

- [<span data-ttu-id="4c27e-146">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4c27e-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4c27e-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4c27e-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4c27e-148">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4c27e-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="4c27e-149">[COM birlikte çalışması için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4c27e-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="4c27e-150">İşlem İçi Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="4c27e-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)

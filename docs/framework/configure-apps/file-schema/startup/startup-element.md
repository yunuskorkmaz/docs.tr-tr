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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153743"
---
# <a name="startup-element"></a><span data-ttu-id="e0d49-102">\<başlangıç> öğesi</span><span class="sxs-lookup"><span data-stu-id="e0d49-102">\<startup> element</span></span>

<span data-ttu-id="e0d49-103">Ortak dil çalışma zamanı başlangıç bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="e0d49-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="e0d49-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e0d49-105">&nbsp;&nbsp;**\<başlangıç>**</span><span class="sxs-lookup"><span data-stu-id="e0d49-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="e0d49-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0d49-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0d49-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d49-107">Attributes and elements</span></span>

 <span data-ttu-id="e0d49-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0d49-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0d49-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0d49-109">Attributes</span></span>

|<span data-ttu-id="e0d49-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0d49-110">Attribute</span></span>|<span data-ttu-id="e0d49-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d49-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="e0d49-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e0d49-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e0d49-113">.NET Framework 2.0 çalışma zamanı etkinleştirme ilkesini etkinleştirmek mi yoksa .NET Framework 4 etkinleştirme ilkesini mi kullanacağınızı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="e0d49-114">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="e0d49-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="e0d49-115">Değer</span><span class="sxs-lookup"><span data-stu-id="e0d49-115">Value</span></span>|<span data-ttu-id="e0d49-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d49-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="e0d49-117">Seçilen çalışma zamanı için .NET Framework 2.0 çalışma zamanı etkinleştirme ilkesini etkinleştirin, bu da eski çalışma zamanı etkinleştirme tekniklerini [(CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi) CLR sürüm 2.0'da kapamak yerine yapılandırma dosyasından seçilen çalışma süresine bağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e0d49-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="e0d49-118">Böylece, yapılandırma dosyasından CLR sürüm 4 veya daha sonra seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulan karma modlu derlemeler seçilen CLR sürümüyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="e0d49-119">Bu değerin ayarlanması, CLR sürüm 1.1 veya CLR sürüm 2.0'ın aynı işleme yüklenmesine engel olur ve işlem içi yan yana özelliği etkin bir şekilde devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="e0d49-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="e0d49-120">.NET Framework 4 ve sonraki için varsayılan etkinleştirme ilkesini kullanın, bu da eski çalışma zamanı etkinleştirme tekniklerinin CLR sürüm 1.1 veya 2.0'ı işleme yüklemesine izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="e0d49-121">Bu değerin ayarlanması, karma modlu derlemelerin .NET Framework 4 veya daha sonra ile oluşturulmadığı sürece .NET Framework 4'e veya daha sonra yüklenmelerini önler.</span><span class="sxs-lookup"><span data-stu-id="e0d49-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="e0d49-122">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e0d49-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e0d49-123">Child elements</span></span>

|<span data-ttu-id="e0d49-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0d49-124">Element</span></span>|<span data-ttu-id="e0d49-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d49-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0d49-126">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="e0d49-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="e0d49-127">Uygulamanın yalnızca ortak dil çalışma süresinin yalnızca sürüm 1.0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="e0d49-128">Çalışma zamanı sürüm 1.1 veya sonraki sürümle oluşturulmuş uygulamalar \*\* \<desteklenen Runtime>\*\* öğesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d49-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="e0d49-129">\<desteklenenRuntime></span><span class="sxs-lookup"><span data-stu-id="e0d49-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="e0d49-130">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0d49-131">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e0d49-131">Parent elements</span></span>

|<span data-ttu-id="e0d49-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0d49-132">Element</span></span>|<span data-ttu-id="e0d49-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d49-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e0d49-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e0d49-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0d49-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0d49-135">Remarks</span></span>

 <span data-ttu-id="e0d49-136">\*\* \<Desteklenen Runtime>\*\* öğesi sürüm 1.1 veya daha sonra çalışma süresi kullanılarak oluşturulmuş tüm uygulamalar tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d49-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="e0d49-137">Çalışma zamanının yalnızca sürüm 1.0 sürümünü desteklemek için oluşturulmuş \*\* \<uygulamalar, gerekli Runtime>\*\* öğesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d49-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="e0d49-138">Microsoft Internet Explorer'da barındırılan bir \*\* \<\*\* uygulamanın başlangıç kodu, başlangıç>öğesini ve alt öğelerini yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="e0d49-139">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="e0d49-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="e0d49-140">Bu özellik, uygulamanız [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)gibi eski etkinleştirme yollarını kullanıyorsa ve bu yolların önceki bir sürüm yerine CLR'nin 4 sürümünü etkinleştirmesini istiyorsanız veya uygulamanız .NET Framework 4 ile oluşturulmuşsa, ancak .NET Framework'ün önceki bir sürümüyle oluşturulmuş karma modlu bir derlemeye bağımlıysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0d49-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="e0d49-141">Bu senaryolarda, özniteliği ' `true`ne göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0d49-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="e0d49-142">Özellik, CLR `true` sürüm 1.1 veya CLR sürüm 2.0'ın aynı işleme yüklenmesine engel olur ve işlem içi yan yana özelliği etkin bir şekilde devre dışı bırakmaz (bkz. [COM Interop için Yan Yana Yürütme).](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e0d49-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="e0d49-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0d49-143">Example</span></span>

 <span data-ttu-id="e0d49-144">Aşağıdaki örnekte, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl belirtilen şekli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0d49-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e0d49-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d49-145">See also</span></span>

- [<span data-ttu-id="e0d49-146">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e0d49-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e0d49-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e0d49-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e0d49-148">Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın</span><span class="sxs-lookup"><span data-stu-id="e0d49-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="e0d49-149">[COM Interop için Yan Yana Yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e0d49-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="e0d49-150">Devam Eden Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="e0d49-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)

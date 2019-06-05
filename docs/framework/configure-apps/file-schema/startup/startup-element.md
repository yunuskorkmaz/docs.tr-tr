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
ms.openlocfilehash: e40ca31ddc40cccbeb3b8dda1d148ddec5032d7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489544"
---
# <a name="startup-element"></a><span data-ttu-id="a0d17-102">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="a0d17-102">\<startup> element</span></span>

<span data-ttu-id="a0d17-103">Ortak dil çalışma zamanı başlatma bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="a0d17-104">\<Yapılandırma > \<başlangıç ></span><span class="sxs-lookup"><span data-stu-id="a0d17-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="a0d17-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0d17-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0d17-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d17-106">Attributes and elements</span></span>

 <span data-ttu-id="a0d17-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0d17-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0d17-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0d17-108">Attributes</span></span>

|<span data-ttu-id="a0d17-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0d17-109">Attribute</span></span>|<span data-ttu-id="a0d17-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d17-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="a0d17-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0d17-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0d17-112">Etkinleştirilip etkinleştirilmeyeceğini belirtir [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] çalışma zamanı etkinleştirme İlkesi veya .NET Framework 4 etkinleştirme ilkesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0d17-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="a0d17-113">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="a0d17-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="a0d17-114">Değer</span><span class="sxs-lookup"><span data-stu-id="a0d17-114">Value</span></span>|<span data-ttu-id="a0d17-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d17-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="a0d17-116">Etkinleştirme [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] eski çalışma zamanını etkinleştirme teknikleri bağlama için olan seçilen çalışma zamanı, çalışma zamanı etkinleştirme İlkesi (gibi [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) yerine yapılandırma dosyasından seçilen çalışma zamanı bunları CLR Version 2.0 sürümü capping.</span><span class="sxs-lookup"><span data-stu-id="a0d17-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="a0d17-117">Bu nedenle, CLR 4 veya sonraki bir sürümü yapılandırma dosyasından seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulmuş karışık mod derlemeleri seçilen CLR sürümü ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="a0d17-118">Bu değer ayarlandığında CLR sürüm 1.1 veya CLR Version 2.0 sürümü ile aynı işleme etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma, yükleme engeller.</span><span class="sxs-lookup"><span data-stu-id="a0d17-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="a0d17-119">Eski çalışma zamanını etkinleştirme teknikleri'CLR sürüm 1.1 veya 2.0 işlemine yüklemeye izin ver olan .NET Framework 4 ve sonraki sürümlerinde, varsayılan etkinleştirme ilkesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0d17-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="a0d17-120">Bu değeri ayarlamak, karma mod derlemeler .NET Framework 4 veya sonraki sürümüyle oluşturulmuş karşılamadıkça .NET Framework 4 veya daha sonra yüklemeyi engeller.</span><span class="sxs-lookup"><span data-stu-id="a0d17-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="a0d17-121">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a0d17-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0d17-122">Child elements</span></span>

|<span data-ttu-id="a0d17-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0d17-123">Element</span></span>|<span data-ttu-id="a0d17-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d17-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0d17-125">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="a0d17-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="a0d17-126">Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="a0d17-127">Çalışma zamanı sürüm 1.1 veya üzeri ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0d17-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="a0d17-128">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="a0d17-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="a0d17-129">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a0d17-130">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a0d17-130">Parent elements</span></span>

|<span data-ttu-id="a0d17-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0d17-131">Element</span></span>|<span data-ttu-id="a0d17-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d17-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a0d17-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a0d17-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0d17-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0d17-134">Remarks</span></span>

 <span data-ttu-id="a0d17-135">**\<SupportedRuntime >** öğesi sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="a0d17-136">Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır  **\<requiredRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0d17-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="a0d17-137">Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar  **\<başlangıç >** öğesi ve onun alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a0d17-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="a0d17-138">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="a0d17-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="a0d17-139">Bu uygulamanız gibi eski etkinleştirme yollarını kullanıyorsa yararlı bir özniteliktir [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), ve daha önceki bir sürümü yerine CLR'nin sürüm 4 etkinleştirmek için bu yollar istediğiniz veya uygulamanız ise ile oluşturulan, .NET Framework 4 ancak .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derleme üzerinde bağımlılık vardır.</span><span class="sxs-lookup"><span data-stu-id="a0d17-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="a0d17-140">Bu senaryolarda, öznitelik ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="a0d17-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="a0d17-141">Özniteliğini `true` CLR sürüm 1.1 veya CLR Version 2.0 sürümü ile aynı işleme, etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma yüklenmesini engeller (bkz [COM birlikte çalışma için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="a0d17-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="a0d17-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0d17-142">Example</span></span>

 <span data-ttu-id="a0d17-143">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0d17-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a0d17-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0d17-144">See also</span></span>

- [<span data-ttu-id="a0d17-145">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a0d17-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a0d17-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="a0d17-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a0d17-147">Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a0d17-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="a0d17-148">[COM birlikte çalışma için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0d17-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="a0d17-149">İşlem İçi Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="a0d17-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)

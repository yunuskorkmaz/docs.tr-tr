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
ms.openlocfilehash: d98f8d672ed1de1a5065a0390dba29992bcc1b39
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634466"
---
# <a name="startup-element"></a><span data-ttu-id="115fa-102">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="115fa-102">\<startup> element</span></span>

<span data-ttu-id="115fa-103">Ortak dil çalışma zamanı başlatma bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="115fa-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="115fa-104">\<Yapılandırma > \<başlangıç ></span><span class="sxs-lookup"><span data-stu-id="115fa-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="115fa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="115fa-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="115fa-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="115fa-106">Attributes and elements</span></span>

 <span data-ttu-id="115fa-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="115fa-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="115fa-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="115fa-108">Attributes</span></span>

|<span data-ttu-id="115fa-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="115fa-109">Attribute</span></span>|<span data-ttu-id="115fa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="115fa-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="115fa-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="115fa-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="115fa-112">Etkinleştirilip etkinleştirilmeyeceğini belirtir [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] çalışma zamanı etkinleştirme İlkesi mi kullanılacağını [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] etkinleştirme ilkesi.</span><span class="sxs-lookup"><span data-stu-id="115fa-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="115fa-113">useLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="115fa-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="115fa-114">Değer</span><span class="sxs-lookup"><span data-stu-id="115fa-114">Value</span></span>|<span data-ttu-id="115fa-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="115fa-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="115fa-116">Etkinleştirme [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] eski çalışma zamanını etkinleştirme teknikleri bağlama için olan seçilen çalışma zamanı, çalışma zamanı etkinleştirme İlkesi (gibi [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) yerine yapılandırma dosyasından seçilen çalışma zamanı bunları CLR Version 2.0 sürümü capping.</span><span class="sxs-lookup"><span data-stu-id="115fa-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="115fa-117">Bu nedenle, CLR 4 veya sonraki bir sürümü yapılandırma dosyasından seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulmuş karışık mod derlemeleri seçilen CLR sürümü ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="115fa-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="115fa-118">Bu değer ayarlandığında CLR sürüm 1.1 veya CLR Version 2.0 sürümü ile aynı işleme etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma, yükleme engeller.</span><span class="sxs-lookup"><span data-stu-id="115fa-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="115fa-119">İçin varsayılan etkinleştirme ilkeyi [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra eski çalışma zamanını etkinleştirme teknikleri'CLR sürüm 1.1 veya 2.0 işleme yüklemek izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="115fa-119">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="115fa-120">Bu değeri ayarlamak, karma mod derlemeler .NET Framework 4 veya sonraki sürümüyle oluşturulmuş karşılamadıkça .NET Framework 4 veya daha sonra yüklemeyi engeller.</span><span class="sxs-lookup"><span data-stu-id="115fa-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="115fa-121">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="115fa-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="115fa-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="115fa-122">Child elements</span></span>

|<span data-ttu-id="115fa-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="115fa-123">Element</span></span>|<span data-ttu-id="115fa-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="115fa-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="115fa-125">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="115fa-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="115fa-126">Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="115fa-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="115fa-127">Çalışma zamanı sürüm 1.1 veya üzeri ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="115fa-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="115fa-128">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="115fa-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="115fa-129">Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="115fa-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="115fa-130">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="115fa-130">Parent elements</span></span>

|<span data-ttu-id="115fa-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="115fa-131">Element</span></span>|<span data-ttu-id="115fa-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="115fa-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="115fa-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="115fa-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="115fa-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="115fa-134">Remarks</span></span>

 <span data-ttu-id="115fa-135"> *\*\<SupportedRuntime >** öğesi sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="115fa-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="115fa-136">Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır  **\<requiredRuntime >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="115fa-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="115fa-137">Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar  **\<başlangıç >** öğesi ve onun alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="115fa-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="115fa-138">UseLegacyV2RuntimeActivationPolicy özniteliği</span><span class="sxs-lookup"><span data-stu-id="115fa-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="115fa-139">Bu uygulamanız gibi eski etkinleştirme yollarını kullanıyorsa yararlı bir özniteliktir [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), ve daha önceki bir sürümü yerine CLR'nin sürüm 4 etkinleştirmek için bu yollar istediğiniz veya uygulamanız ise ile oluşturulmuş [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ancak bağımlıdır .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derleme.</span><span class="sxs-lookup"><span data-stu-id="115fa-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="115fa-140">Bu senaryolarda, öznitelik ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="115fa-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="115fa-141">Özniteliğini `true` CLR sürüm 1.1 veya CLR Version 2.0 sürümü ile aynı işleme, etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma yüklenmesini engeller (bkz [COM birlikte çalışma için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="115fa-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="115fa-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="115fa-142">Example</span></span>

 <span data-ttu-id="115fa-143">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="115fa-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="115fa-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="115fa-144">See also</span></span>

- [<span data-ttu-id="115fa-145">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="115fa-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="115fa-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="115fa-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="115fa-147">Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="115fa-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="115fa-148">[COM birlikte çalışma için yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="115fa-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="115fa-149">İşlem İçi Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="115fa-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)

---
title: <requiredRuntime> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: 19fa1561ca3acd845918d952379c5227121465b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174075"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="3d2f6-102">\<requiredRuntime> öğesi</span><span class="sxs-lookup"><span data-stu-id="3d2f6-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="3d2f6-103">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="3d2f6-104">Bu öğe kullanımdan kaldırılmıştır ve artık kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="3d2f6-105">[`supportedRuntime`](supportedruntime-element.md)Bunun yerine öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="3d2f6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d2f6-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d2f6-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3d2f6-107">Attributes and elements</span></span>

<span data-ttu-id="3d2f6-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d2f6-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d2f6-109">Attributes</span></span>

|<span data-ttu-id="3d2f6-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3d2f6-110">Attribute</span></span>|<span data-ttu-id="3d2f6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d2f6-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="3d2f6-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3d2f6-113">Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="3d2f6-114">Dize değeri, .NET Framework yükleme kökünün altında bulunan dizin adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="3d2f6-115">Dize değerinin içeriği ayrıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="3d2f6-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3d2f6-117">Çalışma zamanı başlangıç kodunun, çalışma zamanı sürümünü belirlemede kayıt defterini arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="3d2f6-118">safemode özniteliği</span><span class="sxs-lookup"><span data-stu-id="3d2f6-118">safemode attribute</span></span>

|<span data-ttu-id="3d2f6-119">Değer</span><span class="sxs-lookup"><span data-stu-id="3d2f6-119">Value</span></span>|<span data-ttu-id="3d2f6-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d2f6-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="3d2f6-121">Çalışma zamanı başlangıç kodu kayıt defterine bakar.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="3d2f6-122">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="3d2f6-123">Çalışma zamanı başlangıç kodu kayıt defterinde görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3d2f6-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3d2f6-124">Child elements</span></span>

<span data-ttu-id="3d2f6-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d2f6-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3d2f6-126">Parent elements</span></span>

|<span data-ttu-id="3d2f6-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="3d2f6-127">Element</span></span>|<span data-ttu-id="3d2f6-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d2f6-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3d2f6-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="3d2f6-130">Öğesini içerir `<requiredRuntime>` .</span><span class="sxs-lookup"><span data-stu-id="3d2f6-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d2f6-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d2f6-131">Remarks</span></span>

 <span data-ttu-id="3d2f6-132">Yalnızca çalışma zamanının 1,0 sürümünü desteklemeye yönelik uygulamalar `<requiredRuntime>` öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="3d2f6-133">Çalışma zamanının 1,1 veya sonraki bir sürümünü kullanarak oluşturulan uygulamalar `<supportedRuntime>` öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="3d2f6-134">Yapılandırma dosyasını belirtmek için [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) işlevini kullanırsanız, `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="3d2f6-135">`<supportedRuntime>` [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)kullandığınızda öğe yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="3d2f6-136">`version`Öznitelik dizesinin belirtilen .NET Framework sürümü için yükleme klasörü adıyla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="3d2f6-137">Bu dize yorumlanmadı.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-137">This string is not interpreted.</span></span> <span data-ttu-id="3d2f6-138">Çalışma zamanı başlangıç kodu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmez; başlangıç kodu bir hata iletisi gösterir ve sonlandırılıyor.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="3d2f6-139">Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, `<requiredRuntime>` öğesini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="3d2f6-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d2f6-140">Example</span></span>

<span data-ttu-id="3d2f6-141">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3d2f6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d2f6-142">See also</span></span>

- [<span data-ttu-id="3d2f6-143">Başlangıç ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3d2f6-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3d2f6-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3d2f6-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3d2f6-145">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3d2f6-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

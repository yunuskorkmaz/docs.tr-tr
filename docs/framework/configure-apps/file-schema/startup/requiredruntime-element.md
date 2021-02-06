---
description: 'Daha fazla bilgi edinin: <requiredRuntime> öğesi'
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
ms.openlocfilehash: e9d0a88a65f72ec03f3b2b124920d8265b8bf0c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639854"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="18e99-103">\<requiredRuntime> öğesi</span><span class="sxs-lookup"><span data-stu-id="18e99-103">\<requiredRuntime> element</span></span>

<span data-ttu-id="18e99-104">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18e99-104">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="18e99-105">Bu öğe kullanımdan kaldırılmıştır ve artık kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="18e99-105">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="18e99-106">[`supportedRuntime`](supportedruntime-element.md)Bunun yerine öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18e99-106">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="18e99-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="18e99-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18e99-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="18e99-108">Attributes and elements</span></span>

<span data-ttu-id="18e99-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18e99-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="18e99-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18e99-110">Attributes</span></span>

|<span data-ttu-id="18e99-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="18e99-111">Attribute</span></span>|<span data-ttu-id="18e99-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18e99-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="18e99-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="18e99-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18e99-114">Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="18e99-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="18e99-115">Dize değeri, .NET Framework yükleme kökünün altında bulunan dizin adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18e99-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="18e99-116">Dize değerinin içeriği ayrıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="18e99-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="18e99-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="18e99-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18e99-118">Çalışma zamanı başlangıç kodunun, çalışma zamanı sürümünü belirlemede kayıt defterini arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="18e99-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="18e99-119">safemode özniteliği</span><span class="sxs-lookup"><span data-stu-id="18e99-119">safemode attribute</span></span>

|<span data-ttu-id="18e99-120">Değer</span><span class="sxs-lookup"><span data-stu-id="18e99-120">Value</span></span>|<span data-ttu-id="18e99-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18e99-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="18e99-122">Çalışma zamanı başlangıç kodu kayıt defterine bakar.</span><span class="sxs-lookup"><span data-stu-id="18e99-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="18e99-123">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="18e99-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="18e99-124">Çalışma zamanı başlangıç kodu kayıt defterinde görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="18e99-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="18e99-125">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="18e99-125">Child elements</span></span>

<span data-ttu-id="18e99-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="18e99-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="18e99-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="18e99-127">Parent elements</span></span>

|<span data-ttu-id="18e99-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="18e99-128">Element</span></span>|<span data-ttu-id="18e99-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18e99-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="18e99-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="18e99-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="18e99-131">Öğesini içerir `<requiredRuntime>` .</span><span class="sxs-lookup"><span data-stu-id="18e99-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18e99-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18e99-132">Remarks</span></span>

 <span data-ttu-id="18e99-133">Yalnızca çalışma zamanının 1,0 sürümünü desteklemeye yönelik uygulamalar `<requiredRuntime>` öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18e99-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="18e99-134">Çalışma zamanının 1,1 veya sonraki bir sürümünü kullanarak oluşturulan uygulamalar `<supportedRuntime>` öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18e99-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="18e99-135">Yapılandırma dosyasını belirtmek için [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) işlevini kullanırsanız, `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18e99-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="18e99-136">`<supportedRuntime>` [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)kullandığınızda öğe yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="18e99-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="18e99-137">`version`Öznitelik dizesinin belirtilen .NET Framework sürümü için yükleme klasörü adıyla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="18e99-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="18e99-138">Bu dize yorumlanmadı.</span><span class="sxs-lookup"><span data-stu-id="18e99-138">This string is not interpreted.</span></span> <span data-ttu-id="18e99-139">Çalışma zamanı başlangıç kodu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmez; başlangıç kodu bir hata iletisi gösterir ve sonlandırılıyor.</span><span class="sxs-lookup"><span data-stu-id="18e99-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="18e99-140">Microsoft Internet Explorer 'da barındırılan bir uygulamanın başlangıç kodu, `<requiredRuntime>` öğesini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="18e99-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="18e99-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="18e99-141">Example</span></span>

<span data-ttu-id="18e99-142">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="18e99-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="18e99-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18e99-143">See also</span></span>

- [<span data-ttu-id="18e99-144">Başlangıç ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="18e99-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="18e99-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="18e99-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="18e99-146">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="18e99-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

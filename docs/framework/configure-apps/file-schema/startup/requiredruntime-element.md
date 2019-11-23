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
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697493"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="2c33f-102">\<requiredRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="2c33f-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="2c33f-103">Uygulamanın yalnızca ortak dil çalışma zamanının 1,0 sürümünü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="2c33f-104">Bu öğe kullanımdan kaldırılmıştır ve artık kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c33f-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="2c33f-105">Bunun yerine [`supportedRuntime`](supportedruntime-element.md) öğesi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c33f-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="2c33f-106"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="2c33f-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2c33f-107">&nbsp;&nbsp;[ **\<başlatma >** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c33f-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="2c33f-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="2c33f-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="2c33f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c33f-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c33f-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2c33f-110">Attributes and elements</span></span>

<span data-ttu-id="2c33f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c33f-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c33f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c33f-112">Attributes</span></span>

|<span data-ttu-id="2c33f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c33f-113">Attribute</span></span>|<span data-ttu-id="2c33f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c33f-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="2c33f-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2c33f-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2c33f-116">Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="2c33f-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="2c33f-117">Dize değeri, .NET Framework yükleme kökünün altında bulunan dizin adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c33f-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="2c33f-118">Dize değerinin içeriği ayrıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="2c33f-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="2c33f-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2c33f-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2c33f-120">Çalışma zamanı başlangıç kodunun, çalışma zamanı sürümünü belirlemede kayıt defterini arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="2c33f-121">safemode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2c33f-121">safemode attribute</span></span>

|<span data-ttu-id="2c33f-122">Değer</span><span class="sxs-lookup"><span data-stu-id="2c33f-122">Value</span></span>|<span data-ttu-id="2c33f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c33f-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2c33f-124">Çalışma zamanı başlangıç kodu kayıt defterine bakar.</span><span class="sxs-lookup"><span data-stu-id="2c33f-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="2c33f-125">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="2c33f-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="2c33f-126">Çalışma zamanı başlangıç kodu kayıt defterinde görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="2c33f-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2c33f-127">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2c33f-127">Child elements</span></span>

<span data-ttu-id="2c33f-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c33f-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2c33f-129">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2c33f-129">Parent elements</span></span>

|<span data-ttu-id="2c33f-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c33f-130">Element</span></span>|<span data-ttu-id="2c33f-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c33f-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2c33f-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2c33f-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="2c33f-133">`<requiredRuntime>` öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c33f-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c33f-134">Remarks</span></span>
 <span data-ttu-id="2c33f-135">Yalnızca çalışma zamanının 1,0 sürümünü desteklemek üzere oluşturulan uygulamalar `<requiredRuntime>` öğesini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c33f-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="2c33f-136">Çalışma zamanının 1,1 veya sonraki bir sürümünü kullanarak oluşturulan uygulamaların `<supportedRuntime>` öğesini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="2c33f-137">Yapılandırma dosyasını belirtmek için [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) işlevini kullanırsanız, çalışma zamanının tüm sürümleri için `<requiredRuntime>` öğesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="2c33f-138">[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)kullandığınızda `<supportedRuntime>` öğesi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2c33f-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="2c33f-139">`version` öznitelik dizesi, .NET Framework belirtilen sürümü için yükleme klasörü adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="2c33f-140">Bu dize yorumlanmadı.</span><span class="sxs-lookup"><span data-stu-id="2c33f-140">This string is not interpreted.</span></span> <span data-ttu-id="2c33f-141">Çalışma zamanı başlangıç kodu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmez; başlangıç kodu bir hata iletisi gösterir ve sonlandırılıyor.</span><span class="sxs-lookup"><span data-stu-id="2c33f-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="2c33f-142">Microsoft Internet Explorer 'da barındırılan bir uygulama için başlangıç kodu `<requiredRuntime>` öğesini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="2c33f-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="2c33f-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c33f-143">Example</span></span>

<span data-ttu-id="2c33f-144">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümünün nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c33f-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2c33f-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c33f-145">See also</span></span>

- [<span data-ttu-id="2c33f-146">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2c33f-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2c33f-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="2c33f-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2c33f-148">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2c33f-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

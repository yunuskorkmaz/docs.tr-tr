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
ms.openlocfilehash: f5a9f99133c153401694372abaeea10a02e492e5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634186"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="117be-102">\<requiredRuntime > öğesi</span><span class="sxs-lookup"><span data-stu-id="117be-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="117be-103">Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="117be-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="117be-104">Bu öğe, kullanım dışı ve artık kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="117be-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="117be-105">[ `supportedRuntime` ](supportedruntime-element.md) Öğesi bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="117be-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

<span data-ttu-id="117be-106">\<Yapılandırma > \<başlangıç > \<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="117be-106">\<configuration> \<startup> \<requiredRuntime></span></span>

## <a name="syntax"></a><span data-ttu-id="117be-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="117be-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="117be-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="117be-108">Attributes and elements</span></span>

<span data-ttu-id="117be-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="117be-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="117be-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="117be-110">Attributes</span></span>

|<span data-ttu-id="117be-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="117be-111">Attribute</span></span>|<span data-ttu-id="117be-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="117be-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="117be-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="117be-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="117be-114">Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="117be-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="117be-115">Dize değeri, .NET Framework yükleme kökü altında bulunan dizin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="117be-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="117be-116">Dize değeri içeriğini çözümlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="117be-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="117be-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="117be-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="117be-118">Çalışma zamanı başlatma kodunu çalışma zamanı sürümünü belirlemek için kayıt defterini arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="117be-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="117be-119">safemode özniteliği</span><span class="sxs-lookup"><span data-stu-id="117be-119">safemode attribute</span></span>

|<span data-ttu-id="117be-120">Değer</span><span class="sxs-lookup"><span data-stu-id="117be-120">Value</span></span>|<span data-ttu-id="117be-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="117be-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="117be-122">Çalışma zamanı başlatma kodunu kayıt defterinde arar.</span><span class="sxs-lookup"><span data-stu-id="117be-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="117be-123">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="117be-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="117be-124">Çalışma zamanı başlatma kodunu kayıt defterinde aramaz.</span><span class="sxs-lookup"><span data-stu-id="117be-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="117be-125">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="117be-125">Child elements</span></span>

<span data-ttu-id="117be-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="117be-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="117be-127">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="117be-127">Parent elements</span></span>

|<span data-ttu-id="117be-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="117be-128">Element</span></span>|<span data-ttu-id="117be-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="117be-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="117be-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="117be-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="117be-131">İçeren `<requiredRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="117be-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="117be-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="117be-132">Remarks</span></span>
 <span data-ttu-id="117be-133">Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır `<requiredRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="117be-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="117be-134">Sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan uygulamalar kullanmalıdır `<supportedRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="117be-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="117be-135">Kullanırsanız [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyasını belirtmek için işlev, kullanmanız gereken `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesi.</span><span class="sxs-lookup"><span data-stu-id="117be-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="117be-136">`<supportedRuntime>` Öğesi yok sayıldı kullandığınızda [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="117be-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="117be-137">`version` Öznitelik dizesini belirtilen .NET Framework sürümü için yükleme klasör adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="117be-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="117be-138">Bu dize yorumlanmaz.</span><span class="sxs-lookup"><span data-stu-id="117be-138">This string is not interpreted.</span></span> <span data-ttu-id="117be-139">Çalışma zamanı başlatma kodunu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmedi; Başlangıç kodu, hata iletisi gösterir ve sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="117be-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="117be-140">Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar `<requiredRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="117be-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="117be-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="117be-141">Example</span></span>

<span data-ttu-id="117be-142">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="117be-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="117be-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="117be-143">See also</span></span>

- [<span data-ttu-id="117be-144">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="117be-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="117be-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="117be-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="117be-146">Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="117be-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

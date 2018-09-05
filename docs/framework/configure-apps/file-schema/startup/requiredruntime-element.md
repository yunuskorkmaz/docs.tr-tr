---
title: '&lt;requiredRuntime&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac1e1f7bc36d8d2b12b99de2794bb0ba31ddbd7a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518653"
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="90e99-102">&lt;requiredRuntime&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="90e99-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="90e99-103">Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="90e99-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="90e99-104">Bu öğe, kullanım dışı ve artık kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90e99-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="90e99-105">[ `supportedRuntime` ](supportedruntime-element.md) Öğesi bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90e99-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="90e99-106">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="90e99-106">\<configuration></span></span>  
<span data-ttu-id="90e99-107">\<Başlangıç ></span><span class="sxs-lookup"><span data-stu-id="90e99-107">\<startup></span></span>  
<span data-ttu-id="90e99-108">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="90e99-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e99-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90e99-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90e99-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="90e99-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90e99-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="90e99-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90e99-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="90e99-112">Attributes</span></span>  
  
|<span data-ttu-id="90e99-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="90e99-113">Attribute</span></span>|<span data-ttu-id="90e99-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e99-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="90e99-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="90e99-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="90e99-116">Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="90e99-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="90e99-117">Dize değeri, .NET Framework yükleme kökü altında bulunan dizin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="90e99-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="90e99-118">Dize değeri içeriğini çözümlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="90e99-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="90e99-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="90e99-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="90e99-120">Çalışma zamanı başlatma kodunu çalışma zamanı sürümünü belirlemek için kayıt defterini arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90e99-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="90e99-121">safemode özniteliği</span><span class="sxs-lookup"><span data-stu-id="90e99-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="90e99-122">Değer</span><span class="sxs-lookup"><span data-stu-id="90e99-122">Value</span></span>|<span data-ttu-id="90e99-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e99-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="90e99-124">Çalışma zamanı başlatma kodunu kayıt defterinde arar.</span><span class="sxs-lookup"><span data-stu-id="90e99-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="90e99-125">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="90e99-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="90e99-126">Çalışma zamanı başlatma kodunu kayıt defterinde aramaz.</span><span class="sxs-lookup"><span data-stu-id="90e99-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90e99-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="90e99-127">Child Elements</span></span>  
 <span data-ttu-id="90e99-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="90e99-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90e99-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="90e99-129">Parent Elements</span></span>  
  
|<span data-ttu-id="90e99-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="90e99-130">Element</span></span>|<span data-ttu-id="90e99-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e99-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="90e99-132">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="90e99-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="90e99-133">İçeren `<requiredRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="90e99-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90e99-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90e99-134">Remarks</span></span>  
 <span data-ttu-id="90e99-135">Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır `<requiredRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="90e99-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="90e99-136">Sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan uygulamalar kullanmalıdır `<supportedRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="90e99-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e99-137">Kullanırsanız [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyasını belirtmek için işlev, kullanmanız gereken `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesi.</span><span class="sxs-lookup"><span data-stu-id="90e99-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="90e99-138">`<supportedRuntime>` Öğesi yok sayıldı kullandığınızda [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="90e99-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="90e99-139">`version` Öznitelik dizesini belirtilen .NET Framework sürümü için yükleme klasör adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="90e99-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="90e99-140">Bu dize yorumlanmaz.</span><span class="sxs-lookup"><span data-stu-id="90e99-140">This string is not interpreted.</span></span> <span data-ttu-id="90e99-141">Çalışma zamanı başlatma kodunu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmedi; Başlangıç kodu, hata iletisi gösterir ve sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="90e99-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e99-142">Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar `<requiredRuntime>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="90e99-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90e99-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="90e99-143">Example</span></span>  
 <span data-ttu-id="90e99-144">Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e99-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90e99-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90e99-145">See Also</span></span>  
 [<span data-ttu-id="90e99-146">Başlangıç Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="90e99-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="90e99-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="90e99-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="90e99-148">\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme</span><span class="sxs-lookup"><span data-stu-id="90e99-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)

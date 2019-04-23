---
title: <etwEnable> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ba411114bfb853e06c83adb42713d43f1452d9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135076"
---
# <a name="etwenable-element"></a><span data-ttu-id="64879-102">\<etwEnable > öğesi</span><span class="sxs-lookup"><span data-stu-id="64879-102">\<etwEnable> Element</span></span>
<span data-ttu-id="64879-103">Olay İzleme (ETW) Windows için ortak dil çalışma zamanı olayları için etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64879-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="64879-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="64879-104">\<configuration> Element</span></span>  
<span data-ttu-id="64879-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="64879-105">\<runtime> Element</span></span>  
<span data-ttu-id="64879-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="64879-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64879-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64879-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64879-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="64879-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64879-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64879-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64879-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="64879-110">Attributes</span></span>  
  
|<span data-ttu-id="64879-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="64879-111">Attribute</span></span>|<span data-ttu-id="64879-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64879-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64879-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="64879-113">enabled</span></span>|<span data-ttu-id="64879-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="64879-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="64879-115">ETW etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64879-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="64879-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="64879-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="64879-117">Değer</span><span class="sxs-lookup"><span data-stu-id="64879-117">Value</span></span>|<span data-ttu-id="64879-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64879-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64879-119">true</span><span class="sxs-lookup"><span data-stu-id="64879-119">true</span></span>|<span data-ttu-id="64879-120">ETW etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="64879-120">Enable ETW.</span></span> <span data-ttu-id="64879-121">Bu Windows Vista ve Windows Server 2008 işletim sistemlerinin başlayarak Windows sürümleri için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="64879-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="64879-122">false</span><span class="sxs-lookup"><span data-stu-id="64879-122">false</span></span>|<span data-ttu-id="64879-123">ETW devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="64879-123">Disable ETW.</span></span> <span data-ttu-id="64879-124">Önceki Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="64879-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64879-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="64879-125">Child Elements</span></span>  
 <span data-ttu-id="64879-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="64879-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64879-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="64879-127">Parent Elements</span></span>  
  
|<span data-ttu-id="64879-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="64879-128">Element</span></span>|<span data-ttu-id="64879-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64879-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="64879-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="64879-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="64879-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="64879-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64879-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64879-132">Remarks</span></span>  
 <span data-ttu-id="64879-133">ETW, Windows Vista ile başlayarak, varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="64879-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="64879-134">ETW bir uygulama için devre dışı bırakmak için bu öğeyi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="64879-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="64879-135">Önceki Windows sürümlerinde, bir uygulama için ETW etkinleştirmek için bu öğeyi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="64879-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64879-136">ETW, etkin veya genel olarak bir sunucuda, kayıt defteri ayarını kullanarak devre dışı.</span><span class="sxs-lookup"><span data-stu-id="64879-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="64879-137">Bkz: [.NET Framework günlük kaydını denetleme](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="64879-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64879-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="64879-138">Example</span></span>  
 <span data-ttu-id="64879-139">Aşağıdaki örnek bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64879-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64879-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64879-140">See also</span></span>

- [<span data-ttu-id="64879-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="64879-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="64879-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="64879-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="64879-143">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="64879-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)

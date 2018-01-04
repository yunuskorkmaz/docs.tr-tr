---
title: "&lt;etwEnable&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d94d49fcb2c395de5172a730923dbe42f67cf35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="ed596-102">&lt;etwEnable&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="ed596-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="ed596-103">Olay izleme için ortak dil çalışma zamanı olayları Windows (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed596-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="ed596-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="ed596-104">\<configuration> Element</span></span>  
<span data-ttu-id="ed596-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="ed596-105">\<runtime> Element</span></span>  
<span data-ttu-id="ed596-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="ed596-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed596-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed596-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed596-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed596-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ed596-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed596-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed596-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed596-110">Attributes</span></span>  
  
|<span data-ttu-id="ed596-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed596-111">Attribute</span></span>|<span data-ttu-id="ed596-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed596-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed596-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="ed596-113">enabled</span></span>|<span data-ttu-id="ed596-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ed596-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ed596-115">ETW etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed596-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ed596-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed596-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="ed596-117">Değer</span><span class="sxs-lookup"><span data-stu-id="ed596-117">Value</span></span>|<span data-ttu-id="ed596-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed596-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed596-119">true</span><span class="sxs-lookup"><span data-stu-id="ed596-119">true</span></span>|<span data-ttu-id="ed596-120">ETW etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ed596-120">Enable ETW.</span></span> <span data-ttu-id="ed596-121">Windows Vista ve Windows Server 2008 işletim sistemleri ile başlayan Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="ed596-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="ed596-122">false</span><span class="sxs-lookup"><span data-stu-id="ed596-122">false</span></span>|<span data-ttu-id="ed596-123">ETW devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="ed596-123">Disable ETW.</span></span> <span data-ttu-id="ed596-124">Önceki Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="ed596-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed596-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed596-125">Child Elements</span></span>  
 <span data-ttu-id="ed596-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed596-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed596-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed596-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ed596-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed596-128">Element</span></span>|<span data-ttu-id="ed596-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed596-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ed596-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ed596-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ed596-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ed596-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed596-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed596-132">Remarks</span></span>  
 <span data-ttu-id="ed596-133">Windows Vista ile başlayarak, ETW varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="ed596-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="ed596-134">ETW bir uygulama için devre dışı bırakmak için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed596-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="ed596-135">Önceki Windows sürümlerinde bu öğe için bir uygulama ETW etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed596-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed596-136">ETW etkin veya genel bir sunucuda, bir kayıt defteri ayarını kullanarak devre dışı.</span><span class="sxs-lookup"><span data-stu-id="ed596-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="ed596-137">Bkz: [.NET Framework günlük kaydını denetleme](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ed596-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed596-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed596-138">Example</span></span>  
 <span data-ttu-id="ed596-139">Aşağıdaki örnek, bir uygulama ETW izlemeyi etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed596-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed596-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed596-140">See Also</span></span>  
 [<span data-ttu-id="ed596-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ed596-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ed596-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ed596-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ed596-143">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="ed596-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)

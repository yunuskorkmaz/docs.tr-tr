---
title: <etwEnable> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3510cbf0a63a8031669bb7a819a8b3c7321aaea4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920773"
---
# <a name="etwenable-element"></a><span data-ttu-id="79784-102">\<etwEnable > öğesi</span><span class="sxs-lookup"><span data-stu-id="79784-102">\<etwEnable> Element</span></span>
<span data-ttu-id="79784-103">Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79784-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="79784-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="79784-104">\<configuration> Element</span></span>  
<span data-ttu-id="79784-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="79784-105">\<runtime> Element</span></span>  
<span data-ttu-id="79784-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="79784-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79784-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79784-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79784-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79784-108">Attributes and Elements</span></span>  
 <span data-ttu-id="79784-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79784-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79784-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79784-110">Attributes</span></span>  
  
|<span data-ttu-id="79784-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79784-111">Attribute</span></span>|<span data-ttu-id="79784-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79784-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79784-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="79784-113">enabled</span></span>|<span data-ttu-id="79784-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="79784-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="79784-115">ETW 'nin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79784-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="79784-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79784-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="79784-117">Değer</span><span class="sxs-lookup"><span data-stu-id="79784-117">Value</span></span>|<span data-ttu-id="79784-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79784-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="79784-119">true</span><span class="sxs-lookup"><span data-stu-id="79784-119">true</span></span>|<span data-ttu-id="79784-120">ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="79784-120">Enable ETW.</span></span> <span data-ttu-id="79784-121">Windows Vista ve Windows Server 2008 işletim sistemleriyle başlayan Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="79784-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="79784-122">false</span><span class="sxs-lookup"><span data-stu-id="79784-122">false</span></span>|<span data-ttu-id="79784-123">ETW 'yi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="79784-123">Disable ETW.</span></span> <span data-ttu-id="79784-124">Bu, Windows 'un önceki sürümleri için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="79784-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79784-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79784-125">Child Elements</span></span>  
 <span data-ttu-id="79784-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="79784-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79784-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79784-127">Parent Elements</span></span>  
  
|<span data-ttu-id="79784-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="79784-128">Element</span></span>|<span data-ttu-id="79784-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79784-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="79784-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="79784-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="79784-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="79784-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79784-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79784-132">Remarks</span></span>  
 <span data-ttu-id="79784-133">Windows Vista ile başlayarak ETW varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="79784-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="79784-134">Bir uygulama için ETW 'yi devre dışı bırakmak için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="79784-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="79784-135">Windows 'un önceki sürümlerinde bu öğeyi kullanarak bir uygulama için ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="79784-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79784-136">ETW, bir kayıt defteri ayarı kullanılarak bir sunucuda küresel olarak etkinleştirilebilir veya devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="79784-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="79784-137">Bkz. [.NET Framework günlüğünü denetleme](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="79784-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79784-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="79784-138">Example</span></span>  
 <span data-ttu-id="79784-139">Aşağıdaki örnekte, bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="79784-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79784-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79784-140">See also</span></span>

- [<span data-ttu-id="79784-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="79784-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="79784-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="79784-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="79784-143">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="79784-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)

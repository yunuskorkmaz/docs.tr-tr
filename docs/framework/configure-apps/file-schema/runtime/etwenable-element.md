---
title: <etwEnable> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117391"
---
# <a name="etwenable-element"></a><span data-ttu-id="09e67-102">\<etwEnable > öğesi</span><span class="sxs-lookup"><span data-stu-id="09e67-102">\<etwEnable> Element</span></span>
<span data-ttu-id="09e67-103">Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="09e67-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
<span data-ttu-id="09e67-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="09e67-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09e67-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="09e67-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="09e67-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<etwEnabled >**</span><span class="sxs-lookup"><span data-stu-id="09e67-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e67-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09e67-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09e67-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e67-108">Attributes and Elements</span></span>  
 <span data-ttu-id="09e67-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="09e67-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09e67-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="09e67-110">Attributes</span></span>  
  
|<span data-ttu-id="09e67-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="09e67-111">Attribute</span></span>|<span data-ttu-id="09e67-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e67-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09e67-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="09e67-113">enabled</span></span>|<span data-ttu-id="09e67-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="09e67-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="09e67-115">ETW 'nin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="09e67-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="09e67-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="09e67-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="09e67-117">Değer</span><span class="sxs-lookup"><span data-stu-id="09e67-117">Value</span></span>|<span data-ttu-id="09e67-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e67-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="09e67-119">true</span><span class="sxs-lookup"><span data-stu-id="09e67-119">true</span></span>|<span data-ttu-id="09e67-120">ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="09e67-120">Enable ETW.</span></span> <span data-ttu-id="09e67-121">Windows Vista ve Windows Server 2008 işletim sistemleriyle başlayan Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="09e67-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="09e67-122">false</span><span class="sxs-lookup"><span data-stu-id="09e67-122">false</span></span>|<span data-ttu-id="09e67-123">ETW 'yi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="09e67-123">Disable ETW.</span></span> <span data-ttu-id="09e67-124">Bu, Windows 'un önceki sürümleri için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="09e67-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09e67-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e67-125">Child Elements</span></span>  
 <span data-ttu-id="09e67-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="09e67-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09e67-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e67-127">Parent Elements</span></span>  
  
|<span data-ttu-id="09e67-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="09e67-128">Element</span></span>|<span data-ttu-id="09e67-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e67-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="09e67-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="09e67-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="09e67-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="09e67-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09e67-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09e67-132">Remarks</span></span>  
 <span data-ttu-id="09e67-133">Windows Vista ile başlayarak ETW varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="09e67-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="09e67-134">Bir uygulama için ETW 'yi devre dışı bırakmak için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="09e67-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="09e67-135">Windows 'un önceki sürümlerinde bu öğeyi kullanarak bir uygulama için ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="09e67-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09e67-136">ETW, bir kayıt defteri ayarı kullanılarak bir sunucuda küresel olarak etkinleştirilebilir veya devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="09e67-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="09e67-137">Bkz. [.NET Framework günlüğünü denetleme](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="09e67-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e67-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="09e67-138">Example</span></span>  
 <span data-ttu-id="09e67-139">Aşağıdaki örnekte, bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="09e67-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09e67-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09e67-140">See also</span></span>

- [<span data-ttu-id="09e67-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="09e67-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="09e67-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="09e67-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="09e67-143">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="09e67-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)

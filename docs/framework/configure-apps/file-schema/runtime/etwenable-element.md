---
description: 'Daha fazla bilgi edinin: <etwEnable> öğesi'
title: <etwEnable> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 224784f47d15788ded41a5756e1d179a5a25907b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787051"
---
# <a name="etwenable-element"></a><span data-ttu-id="367f4-103">\<etwEnable> Öğesi</span><span class="sxs-lookup"><span data-stu-id="367f4-103">\<etwEnable> Element</span></span>

<span data-ttu-id="367f4-104">Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="367f4-104">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="367f4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="367f4-105">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="367f4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="367f4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="367f4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="367f4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="367f4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="367f4-108">Attributes</span></span>  
  
|<span data-ttu-id="367f4-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="367f4-109">Attribute</span></span>|<span data-ttu-id="367f4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="367f4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="367f4-111">enabled</span><span class="sxs-lookup"><span data-stu-id="367f4-111">enabled</span></span>|<span data-ttu-id="367f4-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="367f4-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="367f4-113">ETW 'nin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="367f4-113">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="367f4-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="367f4-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="367f4-115">Değer</span><span class="sxs-lookup"><span data-stu-id="367f4-115">Value</span></span>|<span data-ttu-id="367f4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="367f4-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="367f4-117">true</span><span class="sxs-lookup"><span data-stu-id="367f4-117">true</span></span>|<span data-ttu-id="367f4-118">ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="367f4-118">Enable ETW.</span></span> <span data-ttu-id="367f4-119">Windows Vista ve Windows Server 2008 işletim sistemleriyle başlayan Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="367f4-119">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="367f4-120">yanlış</span><span class="sxs-lookup"><span data-stu-id="367f4-120">false</span></span>|<span data-ttu-id="367f4-121">ETW 'yi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="367f4-121">Disable ETW.</span></span> <span data-ttu-id="367f4-122">Bu, Windows 'un önceki sürümleri için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="367f4-122">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="367f4-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="367f4-123">Child Elements</span></span>  

 <span data-ttu-id="367f4-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="367f4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="367f4-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="367f4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="367f4-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="367f4-126">Element</span></span>|<span data-ttu-id="367f4-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="367f4-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="367f4-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="367f4-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="367f4-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="367f4-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="367f4-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="367f4-130">Remarks</span></span>  

 <span data-ttu-id="367f4-131">Windows Vista ile başlayarak ETW varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="367f4-131">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="367f4-132">Bir uygulama için ETW 'yi devre dışı bırakmak için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="367f4-132">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="367f4-133">Windows 'un önceki sürümlerinde bu öğeyi kullanarak bir uygulama için ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="367f4-133">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="367f4-134">ETW, bir kayıt defteri ayarı kullanılarak bir sunucuda küresel olarak etkinleştirilebilir veya devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="367f4-134">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="367f4-135">Bkz. [.NET Framework günlüğünü denetleme](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="367f4-135">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="367f4-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="367f4-136">Example</span></span>  

 <span data-ttu-id="367f4-137">Aşağıdaki örnekte, bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="367f4-137">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="367f4-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="367f4-138">See also</span></span>

- [<span data-ttu-id="367f4-139">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="367f4-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="367f4-140">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="367f4-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="367f4-141">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="367f4-141">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)

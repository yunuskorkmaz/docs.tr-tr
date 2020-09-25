---
title: <etwEnable> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 1c3e42dfbc2c27841ed065e90bad24575e4fb2b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178274"
---
# <a name="etwenable-element"></a><span data-ttu-id="05b75-102">\<etwEnable> Öğesi</span><span class="sxs-lookup"><span data-stu-id="05b75-102">\<etwEnable> Element</span></span>

<span data-ttu-id="05b75-103">Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="05b75-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="05b75-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="05b75-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05b75-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05b75-105">Attributes and Elements</span></span>  

 <span data-ttu-id="05b75-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05b75-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05b75-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05b75-107">Attributes</span></span>  
  
|<span data-ttu-id="05b75-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="05b75-108">Attribute</span></span>|<span data-ttu-id="05b75-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05b75-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05b75-110">enabled</span><span class="sxs-lookup"><span data-stu-id="05b75-110">enabled</span></span>|<span data-ttu-id="05b75-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="05b75-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="05b75-112">ETW 'nin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="05b75-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="05b75-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="05b75-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="05b75-114">Değer</span><span class="sxs-lookup"><span data-stu-id="05b75-114">Value</span></span>|<span data-ttu-id="05b75-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05b75-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05b75-116">true</span><span class="sxs-lookup"><span data-stu-id="05b75-116">true</span></span>|<span data-ttu-id="05b75-117">ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="05b75-117">Enable ETW.</span></span> <span data-ttu-id="05b75-118">Windows Vista ve Windows Server 2008 işletim sistemleriyle başlayan Windows sürümleri için varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="05b75-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="05b75-119">yanlış</span><span class="sxs-lookup"><span data-stu-id="05b75-119">false</span></span>|<span data-ttu-id="05b75-120">ETW 'yi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="05b75-120">Disable ETW.</span></span> <span data-ttu-id="05b75-121">Bu, Windows 'un önceki sürümleri için varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05b75-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05b75-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05b75-122">Child Elements</span></span>  

 <span data-ttu-id="05b75-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="05b75-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05b75-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05b75-124">Parent Elements</span></span>  
  
|<span data-ttu-id="05b75-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="05b75-125">Element</span></span>|<span data-ttu-id="05b75-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05b75-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05b75-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="05b75-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="05b75-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="05b75-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05b75-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05b75-129">Remarks</span></span>  

 <span data-ttu-id="05b75-130">Windows Vista ile başlayarak ETW varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="05b75-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="05b75-131">Bir uygulama için ETW 'yi devre dışı bırakmak için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="05b75-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="05b75-132">Windows 'un önceki sürümlerinde bu öğeyi kullanarak bir uygulama için ETW 'yi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="05b75-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05b75-133">ETW, bir kayıt defteri ayarı kullanılarak bir sunucuda küresel olarak etkinleştirilebilir veya devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="05b75-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="05b75-134">Bkz. [.NET Framework günlüğünü denetleme](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="05b75-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b75-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="05b75-135">Example</span></span>  

 <span data-ttu-id="05b75-136">Aşağıdaki örnekte, bir uygulama için ETW izlemenin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05b75-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05b75-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05b75-137">See also</span></span>

- [<span data-ttu-id="05b75-138">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="05b75-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="05b75-139">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="05b75-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="05b75-140">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="05b75-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)

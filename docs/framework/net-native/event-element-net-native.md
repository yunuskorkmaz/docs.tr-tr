---
description: 'Daha fazla bilgi edinin: <Event> öğesi (.NET Native)'
title: <Event> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 16ef4376e5953da514598bd7cdcbe0c196ee4da5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747887"
---
# <a name="event-element-net-native"></a><span data-ttu-id="059d3-103">\<Event> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="059d3-103">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="059d3-104">Bir olaya çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="059d3-104">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059d3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="059d3-105">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="059d3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="059d3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="059d3-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="059d3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="059d3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="059d3-108">Attributes</span></span>  
  
|<span data-ttu-id="059d3-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="059d3-109">Attribute</span></span>|<span data-ttu-id="059d3-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="059d3-110">Attribute type</span></span>|<span data-ttu-id="059d3-111">Description</span><span class="sxs-lookup"><span data-stu-id="059d3-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="059d3-112">Genel</span><span class="sxs-lookup"><span data-stu-id="059d3-112">General</span></span>|<span data-ttu-id="059d3-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="059d3-113">Required attribute.</span></span> <span data-ttu-id="059d3-114">Olay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="059d3-114">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="059d3-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="059d3-115">Reflection</span></span>|<span data-ttu-id="059d3-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="059d3-116">Optional attribute.</span></span> <span data-ttu-id="059d3-117">Olay hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="059d3-117">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="059d3-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="059d3-118">Reflection</span></span>|<span data-ttu-id="059d3-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="059d3-119">Optional attribute.</span></span> <span data-ttu-id="059d3-120">Dinamik programlamayı etkinleştirmek için olaya çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="059d3-120">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="059d3-121">Bu ilke, bir olayın çalışma zamanında dinamik olarak işlenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="059d3-121">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="059d3-122">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="059d3-122">Name attribute</span></span>  
  
|<span data-ttu-id="059d3-123">Değer</span><span class="sxs-lookup"><span data-stu-id="059d3-123">Value</span></span>|<span data-ttu-id="059d3-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="059d3-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="059d3-125">*method_name*</span><span class="sxs-lookup"><span data-stu-id="059d3-125">*method_name*</span></span>|<span data-ttu-id="059d3-126">Olay adı.</span><span class="sxs-lookup"><span data-stu-id="059d3-126">The event name.</span></span> <span data-ttu-id="059d3-127">Olayın türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="059d3-127">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="059d3-128">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="059d3-128">All other attributes</span></span>  
  
|<span data-ttu-id="059d3-129">Değer</span><span class="sxs-lookup"><span data-stu-id="059d3-129">Value</span></span>|<span data-ttu-id="059d3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="059d3-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="059d3-131">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="059d3-131">*policy_setting*</span></span>|<span data-ttu-id="059d3-132">Olay için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="059d3-132">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="059d3-133">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="059d3-133">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="059d3-134">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="059d3-134">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="059d3-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="059d3-135">Child Elements</span></span>  

 <span data-ttu-id="059d3-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="059d3-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="059d3-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="059d3-137">Parent Elements</span></span>  
  
|<span data-ttu-id="059d3-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="059d3-138">Element</span></span>|<span data-ttu-id="059d3-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="059d3-139">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="059d3-140">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="059d3-140">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="059d3-141">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="059d3-141">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="059d3-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="059d3-142">Remarks</span></span>  

 <span data-ttu-id="059d3-143">Bir olayın İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="059d3-143">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059d3-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="059d3-144">See also</span></span>

- [<span data-ttu-id="059d3-145">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="059d3-145">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="059d3-146">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="059d3-146">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="059d3-147">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="059d3-147">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

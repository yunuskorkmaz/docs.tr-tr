---
title: <Event> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: b1cf2239e58839c5026bc375ba04568227881bdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288105"
---
# <a name="event-element-net-native"></a><span data-ttu-id="e62b0-102">\<Event> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e62b0-102">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="e62b0-103">Bir olaya çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="e62b0-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e62b0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e62b0-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e62b0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e62b0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e62b0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e62b0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e62b0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e62b0-107">Attributes</span></span>  
  
|<span data-ttu-id="e62b0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e62b0-108">Attribute</span></span>|<span data-ttu-id="e62b0-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="e62b0-109">Attribute type</span></span>|<span data-ttu-id="e62b0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e62b0-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e62b0-111">Genel</span><span class="sxs-lookup"><span data-stu-id="e62b0-111">General</span></span>|<span data-ttu-id="e62b0-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e62b0-112">Required attribute.</span></span> <span data-ttu-id="e62b0-113">Olay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e62b0-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="e62b0-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e62b0-114">Reflection</span></span>|<span data-ttu-id="e62b0-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e62b0-115">Optional attribute.</span></span> <span data-ttu-id="e62b0-116">Olay hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="e62b0-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e62b0-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e62b0-117">Reflection</span></span>|<span data-ttu-id="e62b0-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e62b0-118">Optional attribute.</span></span> <span data-ttu-id="e62b0-119">Dinamik programlamayı etkinleştirmek için olaya çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e62b0-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="e62b0-120">Bu ilke, bir olayın çalışma zamanında dinamik olarak işlenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e62b0-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e62b0-121">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="e62b0-121">Name attribute</span></span>  
  
|<span data-ttu-id="e62b0-122">Değer</span><span class="sxs-lookup"><span data-stu-id="e62b0-122">Value</span></span>|<span data-ttu-id="e62b0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e62b0-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e62b0-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="e62b0-124">*method_name*</span></span>|<span data-ttu-id="e62b0-125">Olay adı.</span><span class="sxs-lookup"><span data-stu-id="e62b0-125">The event name.</span></span> <span data-ttu-id="e62b0-126">Olayın türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="e62b0-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e62b0-127">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e62b0-127">All other attributes</span></span>  
  
|<span data-ttu-id="e62b0-128">Değer</span><span class="sxs-lookup"><span data-stu-id="e62b0-128">Value</span></span>|<span data-ttu-id="e62b0-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e62b0-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e62b0-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e62b0-130">*policy_setting*</span></span>|<span data-ttu-id="e62b0-131">Olay için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="e62b0-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="e62b0-132">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="e62b0-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e62b0-133">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e62b0-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e62b0-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e62b0-134">Child Elements</span></span>  

 <span data-ttu-id="e62b0-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="e62b0-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e62b0-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e62b0-136">Parent Elements</span></span>  
  
|<span data-ttu-id="e62b0-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="e62b0-137">Element</span></span>|<span data-ttu-id="e62b0-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e62b0-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="e62b0-139">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="e62b0-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e62b0-140">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="e62b0-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e62b0-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e62b0-141">Remarks</span></span>  

 <span data-ttu-id="e62b0-142">Bir olayın İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="e62b0-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e62b0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e62b0-143">See also</span></span>

- [<span data-ttu-id="e62b0-144">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e62b0-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e62b0-145">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="e62b0-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e62b0-146">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="e62b0-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

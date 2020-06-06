---
title: <Event>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181034"
---
# <a name="event-element-net-native"></a><span data-ttu-id="af291-102">\<Event>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="af291-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="af291-103">Bir olaya çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af291-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af291-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af291-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af291-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="af291-105">Attributes and Elements</span></span>  
 <span data-ttu-id="af291-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af291-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af291-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="af291-107">Attributes</span></span>  
  
|<span data-ttu-id="af291-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="af291-108">Attribute</span></span>|<span data-ttu-id="af291-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="af291-109">Attribute type</span></span>|<span data-ttu-id="af291-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af291-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="af291-111">Genel</span><span class="sxs-lookup"><span data-stu-id="af291-111">General</span></span>|<span data-ttu-id="af291-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="af291-112">Required attribute.</span></span> <span data-ttu-id="af291-113">Olay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="af291-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="af291-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="af291-114">Reflection</span></span>|<span data-ttu-id="af291-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="af291-115">Optional attribute.</span></span> <span data-ttu-id="af291-116">Olay hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="af291-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="af291-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="af291-117">Reflection</span></span>|<span data-ttu-id="af291-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="af291-118">Optional attribute.</span></span> <span data-ttu-id="af291-119">Dinamik programlamayı etkinleştirmek için olaya çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="af291-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="af291-120">Bu ilke, bir olayın çalışma zamanında dinamik olarak işlenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="af291-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="af291-121">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="af291-121">Name attribute</span></span>  
  
|<span data-ttu-id="af291-122">Değer</span><span class="sxs-lookup"><span data-stu-id="af291-122">Value</span></span>|<span data-ttu-id="af291-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af291-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="af291-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="af291-124">*method_name*</span></span>|<span data-ttu-id="af291-125">Olay adı.</span><span class="sxs-lookup"><span data-stu-id="af291-125">The event name.</span></span> <span data-ttu-id="af291-126">Olayın türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="af291-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="af291-127">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="af291-127">All other attributes</span></span>  
  
|<span data-ttu-id="af291-128">Değer</span><span class="sxs-lookup"><span data-stu-id="af291-128">Value</span></span>|<span data-ttu-id="af291-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af291-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="af291-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="af291-130">*policy_setting*</span></span>|<span data-ttu-id="af291-131">Olay için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="af291-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="af291-132">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="af291-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="af291-133">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="af291-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af291-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="af291-134">Child Elements</span></span>  
 <span data-ttu-id="af291-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="af291-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af291-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="af291-136">Parent Elements</span></span>  
  
|<span data-ttu-id="af291-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="af291-137">Element</span></span>|<span data-ttu-id="af291-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af291-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="af291-139">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="af291-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="af291-140">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="af291-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af291-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af291-141">Remarks</span></span>  
 <span data-ttu-id="af291-142">Bir olayın İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="af291-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af291-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af291-143">See also</span></span>

- [<span data-ttu-id="af291-144">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="af291-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="af291-145">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="af291-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="af291-146">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="af291-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

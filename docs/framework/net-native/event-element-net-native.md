---
title: <Event>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181034"
---
# <a name="event-element-net-native"></a><span data-ttu-id="1ba0f-102">\<Olay> Elemanı (.NET Yerli)</span><span class="sxs-lookup"><span data-stu-id="1ba0f-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="1ba0f-103">Bir olay için çalışma zamanı yansıtma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ba0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba0f-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ba0f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ba0f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1ba0f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ba0f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ba0f-107">Attributes</span></span>  
  
|<span data-ttu-id="1ba0f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1ba0f-108">Attribute</span></span>|<span data-ttu-id="1ba0f-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="1ba0f-109">Attribute type</span></span>|<span data-ttu-id="1ba0f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba0f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1ba0f-111">Genel</span><span class="sxs-lookup"><span data-stu-id="1ba0f-111">General</span></span>|<span data-ttu-id="1ba0f-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-112">Required attribute.</span></span> <span data-ttu-id="1ba0f-113">Olay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="1ba0f-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1ba0f-114">Reflection</span></span>|<span data-ttu-id="1ba0f-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-115">Optional attribute.</span></span> <span data-ttu-id="1ba0f-116">Olay hakkında bilgi için sorgulamayı veya olayı sayısallandırmayı denetler, ancak çalışma zamanında dinamik erişim emmez.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="1ba0f-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1ba0f-117">Reflection</span></span>|<span data-ttu-id="1ba0f-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-118">Optional attribute.</span></span> <span data-ttu-id="1ba0f-119">Dinamik programlamayı etkinleştirmek için etkinliğe çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="1ba0f-120">Bu ilke, bir olayın çalışma zamanında dinamik olarak ele alınabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1ba0f-121">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="1ba0f-121">Name attribute</span></span>  
  
|<span data-ttu-id="1ba0f-122">Değer</span><span class="sxs-lookup"><span data-stu-id="1ba0f-122">Value</span></span>|<span data-ttu-id="1ba0f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba0f-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ba0f-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="1ba0f-124">*method_name*</span></span>|<span data-ttu-id="1ba0f-125">Olay adı.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-125">The event name.</span></span> <span data-ttu-id="1ba0f-126">Olayın türü ana [ \<Type>](type-element-net-native.md) veya [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1ba0f-127">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ba0f-127">All other attributes</span></span>  
  
|<span data-ttu-id="1ba0f-128">Değer</span><span class="sxs-lookup"><span data-stu-id="1ba0f-128">Value</span></span>|<span data-ttu-id="1ba0f-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba0f-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ba0f-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="1ba0f-130">*policy_setting*</span></span>|<span data-ttu-id="1ba0f-131">Olay için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="1ba0f-132">Olası değerler `Auto` `Excluded`, `Included`, `Required`, ve .</span><span class="sxs-lookup"><span data-stu-id="1ba0f-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="1ba0f-133">Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ba0f-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ba0f-134">Child Elements</span></span>  
 <span data-ttu-id="1ba0f-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ba0f-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ba0f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="1ba0f-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="1ba0f-137">Element</span></span>|<span data-ttu-id="1ba0f-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba0f-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ba0f-139">\<Tip></span><span class="sxs-lookup"><span data-stu-id="1ba0f-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="1ba0f-140">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="1ba0f-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="1ba0f-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="1ba0f-142">Yapılı genel bir türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ba0f-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ba0f-143">Remarks</span></span>  
 <span data-ttu-id="1ba0f-144">Bir olayın ilkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba0f-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba0f-145">See also</span></span>

- [<span data-ttu-id="1ba0f-146">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1ba0f-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1ba0f-147">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="1ba0f-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="1ba0f-148">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="1ba0f-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

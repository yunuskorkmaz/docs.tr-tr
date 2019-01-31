---
title: <Event> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d778ca30aa29ba883552f97e061fb1dde8d73e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287591"
---
# <a name="event-element-net-native"></a><span data-ttu-id="a0532-102">\<Event > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="a0532-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="a0532-103">Çalışma zamanı yansıma ilkesini bir olay için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a0532-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0532-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0532-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0532-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0532-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a0532-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0532-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0532-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0532-107">Attributes</span></span>  
  
|<span data-ttu-id="a0532-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0532-108">Attribute</span></span>|<span data-ttu-id="a0532-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="a0532-109">Attribute type</span></span>|<span data-ttu-id="a0532-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0532-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a0532-111">Genel</span><span class="sxs-lookup"><span data-stu-id="a0532-111">General</span></span>|<span data-ttu-id="a0532-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0532-112">Required attribute.</span></span> <span data-ttu-id="a0532-113">Olay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0532-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="a0532-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a0532-114">Reflection</span></span>|<span data-ttu-id="a0532-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0532-115">Optional attribute.</span></span> <span data-ttu-id="a0532-116">Hakkında bilgi için sorgulama veya olay numaralandırma kontrol eder, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a0532-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="a0532-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a0532-117">Reflection</span></span>|<span data-ttu-id="a0532-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a0532-118">Optional attribute.</span></span> <span data-ttu-id="a0532-119">Programlama. olay dinamik etkinleştirmek için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="a0532-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="a0532-120">Bu ilke, bir olay çalışma zamanında dinamik olarak işlenebilen sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0532-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a0532-121">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="a0532-121">Name attribute</span></span>  
  
|<span data-ttu-id="a0532-122">Değer</span><span class="sxs-lookup"><span data-stu-id="a0532-122">Value</span></span>|<span data-ttu-id="a0532-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0532-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0532-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="a0532-124">*method_name*</span></span>|<span data-ttu-id="a0532-125">Olay adı.</span><span class="sxs-lookup"><span data-stu-id="a0532-125">The event name.</span></span> <span data-ttu-id="a0532-126">Olay türü, üst öğe tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0532-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a0532-127">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0532-127">All other attributes</span></span>  
  
|<span data-ttu-id="a0532-128">Değer</span><span class="sxs-lookup"><span data-stu-id="a0532-128">Value</span></span>|<span data-ttu-id="a0532-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0532-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0532-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a0532-130">*policy_setting*</span></span>|<span data-ttu-id="a0532-131">Bu ilke türü olayı için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="a0532-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="a0532-132">Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="a0532-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="a0532-133">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a0532-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0532-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0532-134">Child Elements</span></span>  
 <span data-ttu-id="a0532-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0532-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0532-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0532-136">Parent Elements</span></span>  
  
|<span data-ttu-id="a0532-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0532-137">Element</span></span>|<span data-ttu-id="a0532-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0532-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0532-139">\<türü ></span><span class="sxs-lookup"><span data-stu-id="a0532-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="a0532-140">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a0532-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="a0532-141">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="a0532-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="a0532-142">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a0532-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0532-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0532-143">Remarks</span></span>  
 <span data-ttu-id="a0532-144">Bir olayın ilke açıkça tanımlı değilse, kendi üst öğenin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="a0532-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0532-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0532-145">See also</span></span>
- [<span data-ttu-id="a0532-146">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a0532-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a0532-147">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0532-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="a0532-148">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="a0532-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

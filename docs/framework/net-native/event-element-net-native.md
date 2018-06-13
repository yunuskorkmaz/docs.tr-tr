---
title: '&lt;Event&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7ccf013398420dbeb7918f99baa922aa1bc89db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395560"
---
# <a name="lteventgt-element-net-native"></a><span data-ttu-id="fd5d7-102">&lt;Event&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="fd5d7-102">&lt;Event&gt; Element (.NET Native)</span></span>
<span data-ttu-id="fd5d7-103">Çalışma zamanı yansıma ilke, bir olay için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd5d7-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd5d7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd5d7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd5d7-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd5d7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd5d7-107">Attributes</span></span>  
  
|<span data-ttu-id="fd5d7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd5d7-108">Attribute</span></span>|<span data-ttu-id="fd5d7-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="fd5d7-109">Attribute type</span></span>|<span data-ttu-id="fd5d7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd5d7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="fd5d7-111">Genel</span><span class="sxs-lookup"><span data-stu-id="fd5d7-111">General</span></span>|<span data-ttu-id="fd5d7-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-112">Required attribute.</span></span> <span data-ttu-id="fd5d7-113">Olay adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="fd5d7-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="fd5d7-114">Reflection</span></span>|<span data-ttu-id="fd5d7-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-115">Optional attribute.</span></span> <span data-ttu-id="fd5d7-116">Hakkında bilgi için sorgulama veya olay numaralandırma kontrol eder, ancak herhangi bir dinamik erişim çalışma zamanında etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="fd5d7-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="fd5d7-117">Reflection</span></span>|<span data-ttu-id="fd5d7-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-118">Optional attribute.</span></span> <span data-ttu-id="fd5d7-119">Programlama dinamik etkinleştirmek için olay çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="fd5d7-120">Bu ilke, bir olayı çalışma zamanında dinamik olarak işlenebilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="fd5d7-121">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="fd5d7-121">Name attribute</span></span>  
  
|<span data-ttu-id="fd5d7-122">Değer</span><span class="sxs-lookup"><span data-stu-id="fd5d7-122">Value</span></span>|<span data-ttu-id="fd5d7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd5d7-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd5d7-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="fd5d7-124">*method_name*</span></span>|<span data-ttu-id="fd5d7-125">Olay adı.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-125">The event name.</span></span> <span data-ttu-id="fd5d7-126">Olay türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="fd5d7-127">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="fd5d7-127">All other attributes</span></span>  
  
|<span data-ttu-id="fd5d7-128">Değer</span><span class="sxs-lookup"><span data-stu-id="fd5d7-128">Value</span></span>|<span data-ttu-id="fd5d7-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd5d7-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd5d7-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="fd5d7-130">*policy_setting*</span></span>|<span data-ttu-id="fd5d7-131">Bu ilke türü olayı için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="fd5d7-132">Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="fd5d7-133">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="fd5d7-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd5d7-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd5d7-134">Child Elements</span></span>  
 <span data-ttu-id="fd5d7-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd5d7-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd5d7-136">Parent Elements</span></span>  
  
|<span data-ttu-id="fd5d7-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd5d7-137">Element</span></span>|<span data-ttu-id="fd5d7-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd5d7-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd5d7-139">\<türü ></span><span class="sxs-lookup"><span data-stu-id="fd5d7-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="fd5d7-140">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="fd5d7-141">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="fd5d7-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="fd5d7-142">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd5d7-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd5d7-143">Remarks</span></span>  
 <span data-ttu-id="fd5d7-144">Bir olayın İlkesi açıkça tanımlanmazsa, kendi üst öğesi, çalışma zamanı İlkesi devralır.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5d7-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd5d7-145">See Also</span></span>  
 [<span data-ttu-id="fd5d7-146">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fd5d7-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="fd5d7-147">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="fd5d7-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="fd5d7-148">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="fd5d7-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

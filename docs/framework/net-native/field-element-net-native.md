---
title: <Field> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4a062e060e7b367f0d56b3633238de74ae8ed88
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281677"
---
# <a name="field-element-net-native"></a><span data-ttu-id="9934a-102">\<Alan > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="9934a-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="9934a-103">Bir alan çalışma zamanı yansıma ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="9934a-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9934a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9934a-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9934a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9934a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9934a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9934a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9934a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9934a-107">Attributes</span></span>  
  
|<span data-ttu-id="9934a-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9934a-108">Attribute</span></span>|<span data-ttu-id="9934a-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="9934a-109">Attribute type</span></span>|<span data-ttu-id="9934a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9934a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9934a-111">Genel</span><span class="sxs-lookup"><span data-stu-id="9934a-111">General</span></span>|<span data-ttu-id="9934a-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9934a-112">Required attribute.</span></span> <span data-ttu-id="9934a-113">Alanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9934a-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="9934a-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9934a-114">Reflection</span></span>|<span data-ttu-id="9934a-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9934a-115">Optional attribute.</span></span> <span data-ttu-id="9934a-116">Hakkında bilgi için sorgulama veya alan numaralandırma denetler, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9934a-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="9934a-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9934a-117">Reflection</span></span>|<span data-ttu-id="9934a-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9934a-118">Optional attribute.</span></span> <span data-ttu-id="9934a-119">Programlama. alanın dinamik etkinleştirmek için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="9934a-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="9934a-120">Bu ilke, bir alan ayarlanabilir veya çalışma zamanında dinamik olarak alınan olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9934a-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="9934a-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9934a-121">Serialization</span></span>|<span data-ttu-id="9934a-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9934a-122">Optional attribute.</span></span> <span data-ttu-id="9934a-123">Tür örnekleri kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serileştirilecek veya veri bağlama için kullanılmak üzere etkinleştirmek için bir alan için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="9934a-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9934a-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="9934a-124">Name attribute</span></span>  
  
|<span data-ttu-id="9934a-125">Değer</span><span class="sxs-lookup"><span data-stu-id="9934a-125">Value</span></span>|<span data-ttu-id="9934a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9934a-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9934a-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="9934a-127">*method_name*</span></span>|<span data-ttu-id="9934a-128">Alan adı.</span><span class="sxs-lookup"><span data-stu-id="9934a-128">The field name.</span></span> <span data-ttu-id="9934a-129">Üst öğe tarafından tanımlanan alan türünü [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="9934a-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9934a-130">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9934a-130">All other attributes</span></span>  
  
|<span data-ttu-id="9934a-131">Değer</span><span class="sxs-lookup"><span data-stu-id="9934a-131">Value</span></span>|<span data-ttu-id="9934a-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9934a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9934a-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9934a-133">*policy_setting*</span></span>|<span data-ttu-id="9934a-134">Alan için bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="9934a-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="9934a-135">Olası değerler `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="9934a-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="9934a-136">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9934a-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9934a-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9934a-137">Child Elements</span></span>  
 <span data-ttu-id="9934a-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="9934a-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9934a-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9934a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="9934a-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="9934a-140">Element</span></span>|<span data-ttu-id="9934a-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9934a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9934a-142">\<türü ></span><span class="sxs-lookup"><span data-stu-id="9934a-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="9934a-143">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9934a-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="9934a-144">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="9934a-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="9934a-145">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9934a-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9934a-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9934a-146">Remarks</span></span>  
 <span data-ttu-id="9934a-147">Alan İlkesi açıkça tanımlı değilse, kendi üst öğenin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="9934a-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9934a-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9934a-148">See also</span></span>
- [<span data-ttu-id="9934a-149">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="9934a-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="9934a-150">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9934a-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9934a-151">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="9934a-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

---
description: 'Daha fazla bilgi edinin: <Field> öğesi (.NET Native)'
title: <Field> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 1f8c8b6720fb90bdc5855da7b17694253bbb7629
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747848"
---
# <a name="field-element-net-native"></a><span data-ttu-id="9a5e4-103">\<Field> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="9a5e4-103">\<Field> Element (.NET Native)</span></span>

<span data-ttu-id="9a5e4-104">Çalışma zamanı yansıtma ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-104">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a5e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9a5e4-105">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a5e4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a5e4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9a5e4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a5e4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a5e4-108">Attributes</span></span>  
  
|<span data-ttu-id="9a5e4-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9a5e4-109">Attribute</span></span>|<span data-ttu-id="9a5e4-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="9a5e4-110">Attribute type</span></span>|<span data-ttu-id="9a5e4-111">Description</span><span class="sxs-lookup"><span data-stu-id="9a5e4-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9a5e4-112">Genel</span><span class="sxs-lookup"><span data-stu-id="9a5e4-112">General</span></span>|<span data-ttu-id="9a5e4-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-113">Required attribute.</span></span> <span data-ttu-id="9a5e4-114">Alan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-114">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="9a5e4-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9a5e4-115">Reflection</span></span>|<span data-ttu-id="9a5e4-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-116">Optional attribute.</span></span> <span data-ttu-id="9a5e4-117">Alan hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-117">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="9a5e4-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9a5e4-118">Reflection</span></span>|<span data-ttu-id="9a5e4-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-119">Optional attribute.</span></span> <span data-ttu-id="9a5e4-120">Dinamik programlamayı etkinleştirmek için alana çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-120">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="9a5e4-121">Bu ilke, bir alanın çalışma zamanında ayarlanamayacağını veya dinamik olarak alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-121">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="9a5e4-122">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9a5e4-122">Serialization</span></span>|<span data-ttu-id="9a5e4-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-123">Optional attribute.</span></span> <span data-ttu-id="9a5e4-124">Tür örneklerinin, Newtonsoft JSON serileştirici veya veri bağlama için kullanılması gibi kitaplıklar tarafından serileştirilmesi için bir alana çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-124">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9a5e4-125">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="9a5e4-125">Name attribute</span></span>  
  
|<span data-ttu-id="9a5e4-126">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5e4-126">Value</span></span>|<span data-ttu-id="9a5e4-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a5e4-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9a5e4-128">*method_name*</span><span class="sxs-lookup"><span data-stu-id="9a5e4-128">*method_name*</span></span>|<span data-ttu-id="9a5e4-129">Alan adı.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-129">The field name.</span></span> <span data-ttu-id="9a5e4-130">Alanın türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="9a5e4-130">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9a5e4-131">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a5e4-131">All other attributes</span></span>  
  
|<span data-ttu-id="9a5e4-132">Değer</span><span class="sxs-lookup"><span data-stu-id="9a5e4-132">Value</span></span>|<span data-ttu-id="9a5e4-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a5e4-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9a5e4-134">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9a5e4-134">*policy_setting*</span></span>|<span data-ttu-id="9a5e4-135">Alanı için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-135">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="9a5e4-136">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="9a5e4-136">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="9a5e4-137">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9a5e4-137">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a5e4-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a5e4-138">Child Elements</span></span>  

 <span data-ttu-id="9a5e4-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a5e4-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a5e4-140">Parent Elements</span></span>  
  
|<span data-ttu-id="9a5e4-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a5e4-141">Element</span></span>|<span data-ttu-id="9a5e4-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a5e4-142">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="9a5e4-143">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-143">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="9a5e4-144">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-144">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a5e4-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a5e4-145">Remarks</span></span>  

 <span data-ttu-id="9a5e4-146">Bir alanın İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-146">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5e4-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a5e4-147">See also</span></span>

- [<span data-ttu-id="9a5e4-148">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="9a5e4-148">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9a5e4-149">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9a5e4-149">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9a5e4-150">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="9a5e4-150">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

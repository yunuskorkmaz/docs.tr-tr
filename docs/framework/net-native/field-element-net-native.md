---
title: <Field>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128413"
---
# <a name="field-element-net-native"></a><span data-ttu-id="7bb0a-102">\<Field>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7bb0a-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="7bb0a-103">Çalışma zamanı yansıtma ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bb0a-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bb0a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bb0a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7bb0a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bb0a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bb0a-107">Attributes</span></span>  
  
|<span data-ttu-id="7bb0a-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7bb0a-108">Attribute</span></span>|<span data-ttu-id="7bb0a-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="7bb0a-109">Attribute type</span></span>|<span data-ttu-id="7bb0a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb0a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7bb0a-111">Genel</span><span class="sxs-lookup"><span data-stu-id="7bb0a-111">General</span></span>|<span data-ttu-id="7bb0a-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-112">Required attribute.</span></span> <span data-ttu-id="7bb0a-113">Alan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="7bb0a-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="7bb0a-114">Reflection</span></span>|<span data-ttu-id="7bb0a-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-115">Optional attribute.</span></span> <span data-ttu-id="7bb0a-116">Alan hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="7bb0a-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="7bb0a-117">Reflection</span></span>|<span data-ttu-id="7bb0a-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-118">Optional attribute.</span></span> <span data-ttu-id="7bb0a-119">Dinamik programlamayı etkinleştirmek için alana çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="7bb0a-120">Bu ilke, bir alanın çalışma zamanında ayarlanamayacağını veya dinamik olarak alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="7bb0a-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="7bb0a-121">Serialization</span></span>|<span data-ttu-id="7bb0a-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-122">Optional attribute.</span></span> <span data-ttu-id="7bb0a-123">Tür örneklerinin, Newtonsoft JSON serileştirici veya veri bağlama için kullanılması gibi kitaplıklar tarafından serileştirilmesi için bir alana çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7bb0a-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="7bb0a-124">Name attribute</span></span>  
  
|<span data-ttu-id="7bb0a-125">Değer</span><span class="sxs-lookup"><span data-stu-id="7bb0a-125">Value</span></span>|<span data-ttu-id="7bb0a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb0a-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7bb0a-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="7bb0a-127">*method_name*</span></span>|<span data-ttu-id="7bb0a-128">Alan adı.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-128">The field name.</span></span> <span data-ttu-id="7bb0a-129">Alanın türü üst [\<Type>](type-element-net-native.md) veya öğe tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="7bb0a-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7bb0a-130">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bb0a-130">All other attributes</span></span>  
  
|<span data-ttu-id="7bb0a-131">Değer</span><span class="sxs-lookup"><span data-stu-id="7bb0a-131">Value</span></span>|<span data-ttu-id="7bb0a-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb0a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7bb0a-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7bb0a-133">*policy_setting*</span></span>|<span data-ttu-id="7bb0a-134">Alanı için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="7bb0a-135">Olası değerler şunlardır,, `Auto` `Excluded` `Included` ve `Required` .</span><span class="sxs-lookup"><span data-stu-id="7bb0a-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="7bb0a-136">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7bb0a-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bb0a-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bb0a-137">Child Elements</span></span>  
 <span data-ttu-id="7bb0a-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bb0a-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bb0a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="7bb0a-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="7bb0a-140">Element</span></span>|<span data-ttu-id="7bb0a-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb0a-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="7bb0a-142">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="7bb0a-143">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb0a-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bb0a-144">Remarks</span></span>  
 <span data-ttu-id="7bb0a-145">Bir alanın İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-145">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb0a-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb0a-146">See also</span></span>

- [<span data-ttu-id="7bb0a-147">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="7bb0a-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="7bb0a-148">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7bb0a-148">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7bb0a-149">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="7bb0a-149">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

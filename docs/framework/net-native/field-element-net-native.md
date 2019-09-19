---
title: <Field>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dfb6a07f9733ab1a01a1ce9917c6a4bb4ce793b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049772"
---
# <a name="field-element-net-native"></a><span data-ttu-id="d5338-102">\<Alan > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="d5338-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="d5338-103">Çalışma zamanı yansıtma ilkesini bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="d5338-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5338-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5338-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5338-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5338-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d5338-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d5338-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5338-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5338-107">Attributes</span></span>  
  
|<span data-ttu-id="d5338-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d5338-108">Attribute</span></span>|<span data-ttu-id="d5338-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="d5338-109">Attribute type</span></span>|<span data-ttu-id="d5338-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5338-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="d5338-111">Genel</span><span class="sxs-lookup"><span data-stu-id="d5338-111">General</span></span>|<span data-ttu-id="d5338-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d5338-112">Required attribute.</span></span> <span data-ttu-id="d5338-113">Alan adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5338-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="d5338-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d5338-114">Reflection</span></span>|<span data-ttu-id="d5338-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d5338-115">Optional attribute.</span></span> <span data-ttu-id="d5338-116">Alan hakkında bilgi sorgulamayı denetler, ancak çalışma zamanında herhangi bir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="d5338-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="d5338-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d5338-117">Reflection</span></span>|<span data-ttu-id="d5338-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d5338-118">Optional attribute.</span></span> <span data-ttu-id="d5338-119">Dinamik programlamayı etkinleştirmek için alana çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="d5338-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="d5338-120">Bu ilke, bir alanın çalışma zamanında ayarlanamayacağını veya dinamik olarak alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5338-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="d5338-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d5338-121">Serialization</span></span>|<span data-ttu-id="d5338-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d5338-122">Optional attribute.</span></span> <span data-ttu-id="d5338-123">Tür örneklerinin, Newtonsoft JSON serileştirici veya veri bağlama için kullanılması gibi kitaplıklar tarafından serileştirilmesi için bir alana çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="d5338-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="d5338-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="d5338-124">Name attribute</span></span>  
  
|<span data-ttu-id="d5338-125">Değer</span><span class="sxs-lookup"><span data-stu-id="d5338-125">Value</span></span>|<span data-ttu-id="d5338-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5338-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d5338-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="d5338-127">*method_name*</span></span>|<span data-ttu-id="d5338-128">Alan adı.</span><span class="sxs-lookup"><span data-stu-id="d5338-128">The field name.</span></span> <span data-ttu-id="d5338-129">Alanın türü, üst [ \<tür >](type-element-net-native.md) veya [ \<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d5338-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="d5338-130">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5338-130">All other attributes</span></span>  
  
|<span data-ttu-id="d5338-131">Değer</span><span class="sxs-lookup"><span data-stu-id="d5338-131">Value</span></span>|<span data-ttu-id="d5338-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5338-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d5338-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d5338-133">*policy_setting*</span></span>|<span data-ttu-id="d5338-134">Alanı için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="d5338-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="d5338-135">Olası değerler şunlardır `Auto` `Excluded` `Required`, ,ve.`Included`</span><span class="sxs-lookup"><span data-stu-id="d5338-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="d5338-136">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d5338-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5338-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5338-137">Child Elements</span></span>  
 <span data-ttu-id="d5338-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="d5338-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5338-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5338-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d5338-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5338-140">Element</span></span>|<span data-ttu-id="d5338-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5338-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5338-142">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="d5338-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="d5338-143">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="d5338-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="d5338-144">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="d5338-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="d5338-145">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="d5338-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5338-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5338-146">Remarks</span></span>  
 <span data-ttu-id="d5338-147">Bir alanın İlkesi açıkça tanımlanmamışsa, üst öğesinin çalışma zamanı ilkesini devralır.</span><span class="sxs-lookup"><span data-stu-id="d5338-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5338-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5338-148">See also</span></span>

- [<span data-ttu-id="d5338-149">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="d5338-149">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="d5338-150">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d5338-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="d5338-151">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="d5338-151">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

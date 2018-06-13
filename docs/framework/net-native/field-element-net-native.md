---
title: '&lt;Field&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b713eefa4f23aec34b5f55c0c3457381f54ef931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394627"
---
# <a name="ltfieldgt-element-net-native"></a><span data-ttu-id="39131-102">&lt;Field&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="39131-102">&lt;Field&gt; Element (.NET Native)</span></span>
<span data-ttu-id="39131-103">Çalışma zamanı yansıma İlkesi bir alana uygular.</span><span class="sxs-lookup"><span data-stu-id="39131-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39131-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39131-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39131-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39131-105">Attributes and Elements</span></span>  
 <span data-ttu-id="39131-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39131-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39131-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39131-107">Attributes</span></span>  
  
|<span data-ttu-id="39131-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39131-108">Attribute</span></span>|<span data-ttu-id="39131-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="39131-109">Attribute type</span></span>|<span data-ttu-id="39131-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39131-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="39131-111">Genel</span><span class="sxs-lookup"><span data-stu-id="39131-111">General</span></span>|<span data-ttu-id="39131-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39131-112">Required attribute.</span></span> <span data-ttu-id="39131-113">Alan adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="39131-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="39131-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="39131-114">Reflection</span></span>|<span data-ttu-id="39131-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39131-115">Optional attribute.</span></span> <span data-ttu-id="39131-116">Hakkında bilgi için sorgulama veya alanı numaralandırma kontrol eder, ancak herhangi bir dinamik erişim çalışma zamanında etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="39131-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="39131-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="39131-117">Reflection</span></span>|<span data-ttu-id="39131-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39131-118">Optional attribute.</span></span> <span data-ttu-id="39131-119">Programlama alanın dinamik etkinleştirmek için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="39131-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="39131-120">Bu ilke bir alan ayarlanabilir veya çalışma zamanında dinamik olarak alınan olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="39131-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="39131-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="39131-121">Serialization</span></span>|<span data-ttu-id="39131-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39131-122">Optional attribute.</span></span> <span data-ttu-id="39131-123">Bir alan türü örnekleri kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri hale veya veri bağlaması için kullanılmak üzere etkinleştirmek için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="39131-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="39131-124">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="39131-124">Name attribute</span></span>  
  
|<span data-ttu-id="39131-125">Değer</span><span class="sxs-lookup"><span data-stu-id="39131-125">Value</span></span>|<span data-ttu-id="39131-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39131-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39131-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="39131-127">*method_name*</span></span>|<span data-ttu-id="39131-128">Alan adı.</span><span class="sxs-lookup"><span data-stu-id="39131-128">The field name.</span></span> <span data-ttu-id="39131-129">Alanın türü üst tarafından tanımlanan [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) veya [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="39131-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="39131-130">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="39131-130">All other attributes</span></span>  
  
|<span data-ttu-id="39131-131">Değer</span><span class="sxs-lookup"><span data-stu-id="39131-131">Value</span></span>|<span data-ttu-id="39131-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39131-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39131-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="39131-133">*policy_setting*</span></span>|<span data-ttu-id="39131-134">Bu ilke türü için alan uygulamak için ayarı.</span><span class="sxs-lookup"><span data-stu-id="39131-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="39131-135">Olası değerler şunlardır: `Auto`, `Excluded`, `Included`, ve `Required`.</span><span class="sxs-lookup"><span data-stu-id="39131-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="39131-136">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="39131-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39131-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39131-137">Child Elements</span></span>  
 <span data-ttu-id="39131-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="39131-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39131-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39131-139">Parent Elements</span></span>  
  
|<span data-ttu-id="39131-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="39131-140">Element</span></span>|<span data-ttu-id="39131-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39131-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39131-142">\<türü ></span><span class="sxs-lookup"><span data-stu-id="39131-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="39131-143">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="39131-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="39131-144">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="39131-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="39131-145">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="39131-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39131-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39131-146">Remarks</span></span>  
 <span data-ttu-id="39131-147">Bir alanın İlkesi açıkça tanımlanmazsa, kendi üst öğesi, çalışma zamanı İlkesi devralır.</span><span class="sxs-lookup"><span data-stu-id="39131-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39131-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39131-148">See Also</span></span>  
 [<span data-ttu-id="39131-149">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="39131-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="39131-150">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="39131-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="39131-151">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="39131-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

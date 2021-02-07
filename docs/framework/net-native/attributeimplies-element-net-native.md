---
description: 'Daha fazla bilgi edinin: <AttributeImplies> öğesi (.NET Native)'
title: <AttributeImplies> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 5af1f60f2c1e556281f2f1d392b1a046e52dd277
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747913"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="08406-103">\<AttributeImplies> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="08406-103">\<AttributeImplies> Element (.NET Native)</span></span>

<span data-ttu-id="08406-104">İçerilen özniteliğin uygulandığı kod öğeleri için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08406-104">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08406-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="08406-105">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08406-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="08406-106">Attributes and Elements</span></span>  

 <span data-ttu-id="08406-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08406-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08406-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08406-108">Attributes</span></span>  
  
|<span data-ttu-id="08406-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="08406-109">Attribute</span></span>|<span data-ttu-id="08406-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="08406-110">Attribute type</span></span>|<span data-ttu-id="08406-111">Description</span><span class="sxs-lookup"><span data-stu-id="08406-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="08406-112">Yansıma</span><span class="sxs-lookup"><span data-stu-id="08406-112">Reflection</span></span>|<span data-ttu-id="08406-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-113">Optional attribute.</span></span> <span data-ttu-id="08406-114">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="08406-114">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="08406-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="08406-115">Reflection</span></span>|<span data-ttu-id="08406-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-116">Optional attribute.</span></span> <span data-ttu-id="08406-117">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="08406-117">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="08406-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="08406-118">Reflection</span></span>|<span data-ttu-id="08406-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-119">Optional attribute.</span></span> <span data-ttu-id="08406-120">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="08406-120">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="08406-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="08406-121">Serialization</span></span>|<span data-ttu-id="08406-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-122">Optional attribute.</span></span> <span data-ttu-id="08406-123">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="08406-123">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="08406-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="08406-124">Serialization</span></span>|<span data-ttu-id="08406-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-125">Optional attribute.</span></span> <span data-ttu-id="08406-126">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08406-126">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="08406-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="08406-127">Serialization</span></span>|<span data-ttu-id="08406-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-128">Optional attribute.</span></span> <span data-ttu-id="08406-129">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08406-129">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="08406-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="08406-130">Serialization</span></span>|<span data-ttu-id="08406-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-131">Optional attribute.</span></span> <span data-ttu-id="08406-132">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08406-132">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="08406-133">Interop</span><span class="sxs-lookup"><span data-stu-id="08406-133">Interop</span></span>|<span data-ttu-id="08406-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-134">Optional attribute.</span></span> <span data-ttu-id="08406-135">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="08406-135">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="08406-136">Interop</span><span class="sxs-lookup"><span data-stu-id="08406-136">Interop</span></span>|<span data-ttu-id="08406-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-137">Optional attribute.</span></span> <span data-ttu-id="08406-138">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="08406-138">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="08406-139">Interop</span><span class="sxs-lookup"><span data-stu-id="08406-139">Interop</span></span>|<span data-ttu-id="08406-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08406-140">Optional attribute.</span></span> <span data-ttu-id="08406-141">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="08406-141">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="08406-142">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08406-142">All attributes</span></span>  
  
|<span data-ttu-id="08406-143">Değer</span><span class="sxs-lookup"><span data-stu-id="08406-143">Value</span></span>|<span data-ttu-id="08406-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08406-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08406-145">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="08406-145">*policy_setting*</span></span>|<span data-ttu-id="08406-146">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="08406-146">The setting to apply to this policy type.</span></span> <span data-ttu-id="08406-147">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="08406-147">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="08406-148">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="08406-148">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08406-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="08406-149">Child Elements</span></span>  

 <span data-ttu-id="08406-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="08406-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08406-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="08406-151">Parent Elements</span></span>  
  
|<span data-ttu-id="08406-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="08406-152">Element</span></span>|<span data-ttu-id="08406-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08406-153">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="08406-154">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="08406-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08406-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08406-155">Remarks</span></span>  

 <span data-ttu-id="08406-156">`<AttributeImplies>`Öğesi, kapsayan türü bir öznitelik (diğer bir deyişle, öğesinden türetilmiş bir sınıf) ise kullanılır <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08406-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="08406-157">Özniteliği belirli bir program öğesine uygulanırsa, öğesi tarafından tanımlanan ilke `<AttributeImplies>` Bu program öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="08406-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="08406-158">Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır, ancak en az bir tane bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08406-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08406-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08406-159">See also</span></span>

- [<span data-ttu-id="08406-160">\<Type> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="08406-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="08406-161">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="08406-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="08406-162">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="08406-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="08406-163">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="08406-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

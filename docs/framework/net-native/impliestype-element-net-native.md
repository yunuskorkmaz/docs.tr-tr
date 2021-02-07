---
description: 'Daha fazla bilgi edinin: <ImpliesType> öğesi (.NET Native)'
title: <ImpliesType> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 6476876f335788a276907fd2aef02d5623382699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747692"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="23ce1-103">\<ImpliesType> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="23ce1-103">\<ImpliesType> Element (.NET Native)</span></span>

<span data-ttu-id="23ce1-104">İlke kapsayan tür veya yönteme uygulanmışsa ilkeyi bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="23ce1-104">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ce1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23ce1-105">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23ce1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="23ce1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="23ce1-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="23ce1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23ce1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23ce1-108">Attributes</span></span>  
  
|<span data-ttu-id="23ce1-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="23ce1-109">Attribute</span></span>|<span data-ttu-id="23ce1-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="23ce1-110">Attribute type</span></span>|<span data-ttu-id="23ce1-111">Description</span><span class="sxs-lookup"><span data-stu-id="23ce1-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="23ce1-112">Genel</span><span class="sxs-lookup"><span data-stu-id="23ce1-112">General</span></span>|<span data-ttu-id="23ce1-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-113">Required attribute.</span></span> <span data-ttu-id="23ce1-114">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-114">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="23ce1-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="23ce1-115">Reflection</span></span>|<span data-ttu-id="23ce1-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-116">Optional attribute.</span></span> <span data-ttu-id="23ce1-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="23ce1-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="23ce1-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="23ce1-118">Reflection</span></span>|<span data-ttu-id="23ce1-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-119">Optional attribute.</span></span> <span data-ttu-id="23ce1-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="23ce1-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="23ce1-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="23ce1-121">Reflection</span></span>|<span data-ttu-id="23ce1-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-122">Optional attribute.</span></span> <span data-ttu-id="23ce1-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="23ce1-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="23ce1-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="23ce1-124">Serialization</span></span>|<span data-ttu-id="23ce1-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-125">Optional attribute.</span></span> <span data-ttu-id="23ce1-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="23ce1-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="23ce1-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="23ce1-127">Serialization</span></span>|<span data-ttu-id="23ce1-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-128">Optional attribute.</span></span> <span data-ttu-id="23ce1-129">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="23ce1-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="23ce1-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="23ce1-130">Serialization</span></span>|<span data-ttu-id="23ce1-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-131">Optional attribute.</span></span> <span data-ttu-id="23ce1-132">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="23ce1-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="23ce1-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="23ce1-133">Serialization</span></span>|<span data-ttu-id="23ce1-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-134">Optional attribute.</span></span> <span data-ttu-id="23ce1-135">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="23ce1-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="23ce1-136">Interop</span><span class="sxs-lookup"><span data-stu-id="23ce1-136">Interop</span></span>|<span data-ttu-id="23ce1-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-137">Optional attribute.</span></span> <span data-ttu-id="23ce1-138">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="23ce1-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="23ce1-139">Interop</span><span class="sxs-lookup"><span data-stu-id="23ce1-139">Interop</span></span>|<span data-ttu-id="23ce1-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-140">Optional attribute.</span></span> <span data-ttu-id="23ce1-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="23ce1-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="23ce1-142">Interop</span><span class="sxs-lookup"><span data-stu-id="23ce1-142">Interop</span></span>|<span data-ttu-id="23ce1-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="23ce1-143">Optional attribute.</span></span> <span data-ttu-id="23ce1-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="23ce1-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="23ce1-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="23ce1-145">Name attribute</span></span>  
  
|<span data-ttu-id="23ce1-146">Değer</span><span class="sxs-lookup"><span data-stu-id="23ce1-146">Value</span></span>|<span data-ttu-id="23ce1-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ce1-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ce1-148">*type_name*</span><span class="sxs-lookup"><span data-stu-id="23ce1-148">*type_name*</span></span>|<span data-ttu-id="23ce1-149">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="23ce1-149">The type name.</span></span> <span data-ttu-id="23ce1-150">Bu öğe tarafından temsil edilen tür, `<ImpliesType>` kapsayan öğesiyle aynı ad alanında bulunuyorsa `<Type>` *type_name* , ad alanı olmadan türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-150">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="23ce1-151">Aksi takdirde, *type_name* tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-151">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="23ce1-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23ce1-152">All other attributes</span></span>  
  
|<span data-ttu-id="23ce1-153">Değer</span><span class="sxs-lookup"><span data-stu-id="23ce1-153">Value</span></span>|<span data-ttu-id="23ce1-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ce1-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ce1-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="23ce1-155">*policy_setting*</span></span>|<span data-ttu-id="23ce1-156">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="23ce1-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="23ce1-157">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="23ce1-157">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="23ce1-158">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="23ce1-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23ce1-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="23ce1-159">Child Elements</span></span>  

 <span data-ttu-id="23ce1-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="23ce1-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23ce1-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="23ce1-161">Parent Elements</span></span>  
  
|<span data-ttu-id="23ce1-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="23ce1-162">Element</span></span>|<span data-ttu-id="23ce1-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ce1-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="23ce1-164">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="23ce1-164">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="23ce1-165">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="23ce1-165">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="23ce1-166">Bir yönteme yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="23ce1-166">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ce1-167">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23ce1-167">Remarks</span></span>  

 <span data-ttu-id="23ce1-168">`<ImpliesType>`Öğesi öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="23ce1-168">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="23ce1-169">Aşağıdaki senaryoyu ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="23ce1-169">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="23ce1-170">Bir yordamın bir tür üzerinde yansıtılması gerekiyorsa, ikinci bir tür üzerinde yansıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-170">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="23ce1-171">Statik analiz bunun gerekli olduğunu belirtmediği için, ikinci türün örtük olarak belirtilen örneklenmesi için meta veriler kullanılamaz durumda değildir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-171">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="23ce1-172">En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleriyle genel örneklemelerdir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-172">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="23ce1-173">`<ImpliesType>`Öğesi, kendi üst öğesi tarafından belirtilen türde bir yansıma gereksinimi, öğesi tarafından belirtilen türde yansıma gereksinimini ifade eden varsayımıyla tanımlanmıştır `<ImpliesType>` .</span><span class="sxs-lookup"><span data-stu-id="23ce1-173">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="23ce1-174">Örneğin, aşağıdaki yansıma yönergeleri iki tür için geçerlidir `Explicit<T>` ve `Implicit<T>` .</span><span class="sxs-lookup"><span data-stu-id="23ce1-174">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="23ce1-175">Bir örneklemesinin `Explicit` tanımlı bir ilke ayarı yoksa, bu yönergenin hiçbir etkisi yoktur `Dynamic` .</span><span class="sxs-lookup"><span data-stu-id="23ce1-175">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="23ce1-176">Örneğin, için bu durum,, için olan `Explicit<Int32>` `Implicit<Int32>` genel üyeleriyle birlikte oluşturulur ve meta verileri dinamik programlama için erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-176">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="23ce1-177">Aşağıda, en az bir seri hale getirici için geçerli olan gerçek dünyada bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-177">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="23ce1-178">Yönergeler, bir şey olarak yazılmış bir şeyi yansıtan gereksinimi yakalar ve `IList<`  `>` `List<`  `>` uygulama başına ek açıklama gerekmeden ilgili bir tür üzerinde yansıtma de içerir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-178">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="23ce1-179">`<ImpliesType>`Öğesi bir öğesi içinde de görünebilir `<Method>` , çünkü bazı durumlarda genel bir yöntemi örneklemede bir tür örneklemesi yansıtılıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23ce1-179">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="23ce1-180">Örneğin, `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` belirli bir kitaplığın, ilişkili ve türleriyle birlikte dinamik olarak erişebileceği genel bir yöntem düşünün <xref:System.Collections.Generic.List%601> <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="23ce1-180">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="23ce1-181">Bu, şöyle ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="23ce1-181">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23ce1-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23ce1-182">See also</span></span>

- [<span data-ttu-id="23ce1-183">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="23ce1-183">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="23ce1-184">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="23ce1-184">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="23ce1-185">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="23ce1-185">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

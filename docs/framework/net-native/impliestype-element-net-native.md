---
title: <ImpliesType>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181010"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="6c3fb-102">\<ImpliesType>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6c3fb-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="6c3fb-103">İlke kapsayan tür veya yönteme uygulanmışsa ilkeyi bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c3fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c3fb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c3fb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c3fb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6c3fb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c3fb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c3fb-107">Attributes</span></span>  
  
|<span data-ttu-id="6c3fb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c3fb-108">Attribute</span></span>|<span data-ttu-id="6c3fb-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="6c3fb-109">Attribute type</span></span>|<span data-ttu-id="6c3fb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c3fb-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6c3fb-111">Genel</span><span class="sxs-lookup"><span data-stu-id="6c3fb-111">General</span></span>|<span data-ttu-id="6c3fb-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-112">Required attribute.</span></span> <span data-ttu-id="6c3fb-113">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="6c3fb-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6c3fb-114">Reflection</span></span>|<span data-ttu-id="6c3fb-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-115">Optional attribute.</span></span> <span data-ttu-id="6c3fb-116">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6c3fb-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6c3fb-117">Reflection</span></span>|<span data-ttu-id="6c3fb-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-118">Optional attribute.</span></span> <span data-ttu-id="6c3fb-119">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6c3fb-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6c3fb-120">Reflection</span></span>|<span data-ttu-id="6c3fb-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-121">Optional attribute.</span></span> <span data-ttu-id="6c3fb-122">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6c3fb-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6c3fb-123">Serialization</span></span>|<span data-ttu-id="6c3fb-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-124">Optional attribute.</span></span> <span data-ttu-id="6c3fb-125">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6c3fb-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6c3fb-126">Serialization</span></span>|<span data-ttu-id="6c3fb-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-127">Optional attribute.</span></span> <span data-ttu-id="6c3fb-128">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6c3fb-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6c3fb-129">Serialization</span></span>|<span data-ttu-id="6c3fb-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-130">Optional attribute.</span></span> <span data-ttu-id="6c3fb-131">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6c3fb-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6c3fb-132">Serialization</span></span>|<span data-ttu-id="6c3fb-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-133">Optional attribute.</span></span> <span data-ttu-id="6c3fb-134">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6c3fb-135">Interop</span><span class="sxs-lookup"><span data-stu-id="6c3fb-135">Interop</span></span>|<span data-ttu-id="6c3fb-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-136">Optional attribute.</span></span> <span data-ttu-id="6c3fb-137">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6c3fb-138">Interop</span><span class="sxs-lookup"><span data-stu-id="6c3fb-138">Interop</span></span>|<span data-ttu-id="6c3fb-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-139">Optional attribute.</span></span> <span data-ttu-id="6c3fb-140">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6c3fb-141">Interop</span><span class="sxs-lookup"><span data-stu-id="6c3fb-141">Interop</span></span>|<span data-ttu-id="6c3fb-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-142">Optional attribute.</span></span> <span data-ttu-id="6c3fb-143">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6c3fb-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="6c3fb-144">Name attribute</span></span>  
  
|<span data-ttu-id="6c3fb-145">Değer</span><span class="sxs-lookup"><span data-stu-id="6c3fb-145">Value</span></span>|<span data-ttu-id="6c3fb-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c3fb-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6c3fb-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="6c3fb-147">*type_name*</span></span>|<span data-ttu-id="6c3fb-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-148">The type name.</span></span> <span data-ttu-id="6c3fb-149">Bu öğe tarafından temsil edilen tür, `<ImpliesType>` kapsayan öğesiyle aynı ad alanında bulunuyorsa `<Type>` *type_name* , ad alanı olmadan türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="6c3fb-150">Aksi takdirde, *type_name* tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6c3fb-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c3fb-151">All other attributes</span></span>  
  
|<span data-ttu-id="6c3fb-152">Değer</span><span class="sxs-lookup"><span data-stu-id="6c3fb-152">Value</span></span>|<span data-ttu-id="6c3fb-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c3fb-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6c3fb-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6c3fb-154">*policy_setting*</span></span>|<span data-ttu-id="6c3fb-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="6c3fb-156">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6c3fb-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6c3fb-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c3fb-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c3fb-158">Child Elements</span></span>  
 <span data-ttu-id="6c3fb-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c3fb-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c3fb-160">Parent Elements</span></span>  
  
|<span data-ttu-id="6c3fb-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c3fb-161">Element</span></span>|<span data-ttu-id="6c3fb-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c3fb-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="6c3fb-163">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-163">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="6c3fb-164">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="6c3fb-165">Bir yönteme yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-165">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c3fb-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c3fb-166">Remarks</span></span>  
 <span data-ttu-id="6c3fb-167">`<ImpliesType>`Öğesi öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-167">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="6c3fb-168">Aşağıdaki senaryoyu ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6c3fb-168">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="6c3fb-169">Bir yordamın bir tür üzerinde yansıtılması gerekiyorsa, ikinci bir tür üzerinde yansıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-169">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="6c3fb-170">Statik analiz bunun gerekli olduğunu belirtmediği için, ikinci türün örtük olarak belirtilen örneklenmesi için meta veriler kullanılamaz durumda değildir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-170">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="6c3fb-171">En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleriyle genel örneklemelerdir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-171">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="6c3fb-172">`<ImpliesType>`Öğesi, kendi üst öğesi tarafından belirtilen türde bir yansıma gereksinimi, öğesi tarafından belirtilen türde yansıma gereksinimini ifade eden varsayımıyla tanımlanmıştır `<ImpliesType>` .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-172">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="6c3fb-173">Örneğin, aşağıdaki yansıma yönergeleri iki tür için geçerlidir `Explicit<T>` ve `Implicit<T>` .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-173">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="6c3fb-174">Bir örneklemesinin `Explicit` tanımlı bir ilke ayarı yoksa, bu yönergenin hiçbir etkisi yoktur `Dynamic` .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-174">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="6c3fb-175">Örneğin, için bu durum,, için olan `Explicit<Int32>` `Implicit<Int32>` genel üyeleriyle birlikte oluşturulur ve meta verileri dinamik programlama için erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-175">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="6c3fb-176">Aşağıda, en az bir seri hale getirici için geçerli olan gerçek dünyada bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-176">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="6c3fb-177">Yönergeler, bir şey olarak yazılmış bir şeyi yansıtan gereksinimi yakalar ve `IList<` *something* `>` `List<` *something* `>` uygulama başına ek açıklama gerekmeden ilgili bir tür üzerinde yansıtma de içerir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-177">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="6c3fb-178">`<ImpliesType>`Öğesi bir öğesi içinde de görünebilir `<Method>` , çünkü bazı durumlarda genel bir yöntemi örneklemede bir tür örneklemesi yansıtılıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-178">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="6c3fb-179">Örneğin, `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` belirli bir kitaplığın, ilişkili ve türleriyle birlikte dinamik olarak erişebileceği genel bir yöntem düşünün <xref:System.Collections.Generic.List%601> <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="6c3fb-179">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="6c3fb-180">Bu, şöyle ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="6c3fb-180">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c3fb-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c3fb-181">See also</span></span>

- [<span data-ttu-id="6c3fb-182">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c3fb-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6c3fb-183">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6c3fb-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="6c3fb-184">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="6c3fb-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

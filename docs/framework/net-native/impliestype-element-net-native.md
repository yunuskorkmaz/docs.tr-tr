---
title: <ImpliesType>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10fa3a0ac04038bb686311a4d86c99442c0fcf26
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049670"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="1041d-102">\<Impliestype > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="1041d-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="1041d-103">İlke kapsayan tür veya yönteme uygulanmışsa ilkeyi bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="1041d-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1041d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1041d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1041d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1041d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1041d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1041d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1041d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1041d-107">Attributes</span></span>  
  
|<span data-ttu-id="1041d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1041d-108">Attribute</span></span>|<span data-ttu-id="1041d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="1041d-109">Attribute type</span></span>|<span data-ttu-id="1041d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1041d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1041d-111">Genel</span><span class="sxs-lookup"><span data-stu-id="1041d-111">General</span></span>|<span data-ttu-id="1041d-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-112">Required attribute.</span></span> <span data-ttu-id="1041d-113">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1041d-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="1041d-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1041d-114">Reflection</span></span>|<span data-ttu-id="1041d-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-115">Optional attribute.</span></span> <span data-ttu-id="1041d-116">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="1041d-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1041d-117">Reflection</span></span>|<span data-ttu-id="1041d-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-118">Optional attribute.</span></span> <span data-ttu-id="1041d-119">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="1041d-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="1041d-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="1041d-120">Reflection</span></span>|<span data-ttu-id="1041d-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-121">Optional attribute.</span></span> <span data-ttu-id="1041d-122">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="1041d-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1041d-123">Serialization</span></span>|<span data-ttu-id="1041d-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-124">Optional attribute.</span></span> <span data-ttu-id="1041d-125">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="1041d-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1041d-126">Serialization</span></span>|<span data-ttu-id="1041d-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-127">Optional attribute.</span></span> <span data-ttu-id="1041d-128"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="1041d-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1041d-129">Serialization</span></span>|<span data-ttu-id="1041d-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-130">Optional attribute.</span></span> <span data-ttu-id="1041d-131"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="1041d-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="1041d-132">Serialization</span></span>|<span data-ttu-id="1041d-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-133">Optional attribute.</span></span> <span data-ttu-id="1041d-134"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="1041d-135">Interop</span><span class="sxs-lookup"><span data-stu-id="1041d-135">Interop</span></span>|<span data-ttu-id="1041d-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-136">Optional attribute.</span></span> <span data-ttu-id="1041d-137">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="1041d-138">Interop</span><span class="sxs-lookup"><span data-stu-id="1041d-138">Interop</span></span>|<span data-ttu-id="1041d-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-139">Optional attribute.</span></span> <span data-ttu-id="1041d-140">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="1041d-141">Interop</span><span class="sxs-lookup"><span data-stu-id="1041d-141">Interop</span></span>|<span data-ttu-id="1041d-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1041d-142">Optional attribute.</span></span> <span data-ttu-id="1041d-143">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="1041d-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1041d-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="1041d-144">Name attribute</span></span>  
  
|<span data-ttu-id="1041d-145">Değer</span><span class="sxs-lookup"><span data-stu-id="1041d-145">Value</span></span>|<span data-ttu-id="1041d-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1041d-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1041d-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="1041d-147">*type_name*</span></span>|<span data-ttu-id="1041d-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="1041d-148">The type name.</span></span> <span data-ttu-id="1041d-149">Bu `<ImpliesType>` öğe tarafından temsil edilen tür, kapsayan `<Type>` öğesiyle aynı ad alanında bulunuyorsa, *type_name* ad alanı olmadan türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1041d-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="1041d-150">Aksi halde, *type_name* tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1041d-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1041d-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1041d-151">All other attributes</span></span>  
  
|<span data-ttu-id="1041d-152">Değer</span><span class="sxs-lookup"><span data-stu-id="1041d-152">Value</span></span>|<span data-ttu-id="1041d-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1041d-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1041d-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="1041d-154">*policy_setting*</span></span>|<span data-ttu-id="1041d-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="1041d-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="1041d-156">Olası değerler şunlardır `All` `Auto` ,,`Excluded`,,,, ve`Required All`. `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="1041d-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="1041d-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="1041d-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1041d-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1041d-158">Child Elements</span></span>  
 <span data-ttu-id="1041d-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="1041d-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1041d-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1041d-160">Parent Elements</span></span>  
  
|<span data-ttu-id="1041d-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="1041d-161">Element</span></span>|<span data-ttu-id="1041d-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1041d-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1041d-163">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="1041d-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="1041d-164">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="1041d-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="1041d-165">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="1041d-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="1041d-166">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="1041d-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="1041d-167">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="1041d-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="1041d-168">Bir yönteme yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="1041d-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1041d-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1041d-169">Remarks</span></span>  
 <span data-ttu-id="1041d-170">`<ImpliesType>` Öğesi öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1041d-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="1041d-171">Aşağıdaki senaryoyu ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1041d-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="1041d-172">Bir yordamın bir tür üzerinde yansıtılması gerekiyorsa, ikinci bir tür üzerinde yansıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1041d-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="1041d-173">Statik analiz bunun gerekli olduğunu belirtmediği için, ikinci türün örtük olarak belirtilen örneklenmesi için meta veriler kullanılamaz durumda değildir.</span><span class="sxs-lookup"><span data-stu-id="1041d-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="1041d-174">En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleriyle genel örneklemelerdir.</span><span class="sxs-lookup"><span data-stu-id="1041d-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="1041d-175">Öğesi, kendi üst öğesi tarafından belirtilen türde bir yansıma gereksinimi, `<ImpliesType>` öğesi tarafından belirtilen türde yansıma gereksinimini ifade eden varsayımıyla tanımlanmıştır. `<ImpliesType>`</span><span class="sxs-lookup"><span data-stu-id="1041d-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="1041d-176">Örneğin, aşağıdaki yansıma yönergeleri iki tür `Explicit<T>` için geçerlidir ve. `Implicit<T>`</span><span class="sxs-lookup"><span data-stu-id="1041d-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="1041d-177">Bir örneklemesinin `Explicit` tanımlı `Dynamic` bir ilke ayarı yoksa, bu yönergenin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1041d-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="1041d-178">Örneğin, için bu durum,, `Explicit<Int32>` `Implicit<Int32>` için olan genel üyeleriyle birlikte oluşturulur ve meta verileri dinamik programlama için erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="1041d-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="1041d-179">Aşağıda, en az bir seri hale getirici için geçerli olan gerçek dünyada bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1041d-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="1041d-180">Yönergeler `IList<`, *bir şey* `>` olarak yazılmış bir şeyi yansıtan gereksinimi yakalar ve bunlara gerek duymadan ilgili `List<` *bir* `>` tür üzerinde yansıtma Uygulama başına ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="1041d-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="1041d-181">`<ImpliesType>` Öğesi bir`<Method>` öğesi içinde de görünebilir, çünkü bazı durumlarda genel bir yöntemi örneklemede bir tür örneklemesi yansıtılıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1041d-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="1041d-182">Örneğin, belirli bir kitaplığın, ilişkili `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleriyle birlikte dinamik olarak erişebileceği genel bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="1041d-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="1041d-183">Bu, şöyle ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="1041d-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1041d-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1041d-184">See also</span></span>

- [<span data-ttu-id="1041d-185">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1041d-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1041d-186">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="1041d-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="1041d-187">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="1041d-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

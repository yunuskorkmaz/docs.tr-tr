---
title: <ImpliesType> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 2f0ce1a1587e190627212cba07db298c12f4b30e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128387"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="bb1b7-102">\<ımpliestype > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="bb1b7-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="bb1b7-103">İlke kapsayan tür veya yönteme uygulanmışsa ilkeyi bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb1b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb1b7-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb1b7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb1b7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bb1b7-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb1b7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb1b7-107">Attributes</span></span>  
  
|<span data-ttu-id="bb1b7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bb1b7-108">Attribute</span></span>|<span data-ttu-id="bb1b7-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="bb1b7-109">Attribute type</span></span>|<span data-ttu-id="bb1b7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb1b7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="bb1b7-111">Genel</span><span class="sxs-lookup"><span data-stu-id="bb1b7-111">General</span></span>|<span data-ttu-id="bb1b7-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-112">Required attribute.</span></span> <span data-ttu-id="bb1b7-113">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="bb1b7-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="bb1b7-114">Reflection</span></span>|<span data-ttu-id="bb1b7-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-115">Optional attribute.</span></span> <span data-ttu-id="bb1b7-116">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="bb1b7-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="bb1b7-117">Reflection</span></span>|<span data-ttu-id="bb1b7-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-118">Optional attribute.</span></span> <span data-ttu-id="bb1b7-119">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="bb1b7-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="bb1b7-120">Reflection</span></span>|<span data-ttu-id="bb1b7-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-121">Optional attribute.</span></span> <span data-ttu-id="bb1b7-122">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="bb1b7-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bb1b7-123">Serialization</span></span>|<span data-ttu-id="bb1b7-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-124">Optional attribute.</span></span> <span data-ttu-id="bb1b7-125">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="bb1b7-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bb1b7-126">Serialization</span></span>|<span data-ttu-id="bb1b7-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-127">Optional attribute.</span></span> <span data-ttu-id="bb1b7-128"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="bb1b7-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bb1b7-129">Serialization</span></span>|<span data-ttu-id="bb1b7-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-130">Optional attribute.</span></span> <span data-ttu-id="bb1b7-131"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="bb1b7-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bb1b7-132">Serialization</span></span>|<span data-ttu-id="bb1b7-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-133">Optional attribute.</span></span> <span data-ttu-id="bb1b7-134"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="bb1b7-135">Interop</span><span class="sxs-lookup"><span data-stu-id="bb1b7-135">Interop</span></span>|<span data-ttu-id="bb1b7-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-136">Optional attribute.</span></span> <span data-ttu-id="bb1b7-137">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="bb1b7-138">Interop</span><span class="sxs-lookup"><span data-stu-id="bb1b7-138">Interop</span></span>|<span data-ttu-id="bb1b7-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-139">Optional attribute.</span></span> <span data-ttu-id="bb1b7-140">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="bb1b7-141">Interop</span><span class="sxs-lookup"><span data-stu-id="bb1b7-141">Interop</span></span>|<span data-ttu-id="bb1b7-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-142">Optional attribute.</span></span> <span data-ttu-id="bb1b7-143">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="bb1b7-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="bb1b7-144">Name attribute</span></span>  
  
|<span data-ttu-id="bb1b7-145">Değer</span><span class="sxs-lookup"><span data-stu-id="bb1b7-145">Value</span></span>|<span data-ttu-id="bb1b7-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb1b7-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bb1b7-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="bb1b7-147">*type_name*</span></span>|<span data-ttu-id="bb1b7-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-148">The type name.</span></span> <span data-ttu-id="bb1b7-149">Bu `<ImpliesType>` öğesi tarafından temsil edilen tür, kendisini içeren `<Type>` öğesiyle aynı ad alanında bulunuyorsa, *type_name* ad alanı olmadan türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="bb1b7-150">Aksi halde, *type_name* tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="bb1b7-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb1b7-151">All other attributes</span></span>  
  
|<span data-ttu-id="bb1b7-152">Değer</span><span class="sxs-lookup"><span data-stu-id="bb1b7-152">Value</span></span>|<span data-ttu-id="bb1b7-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb1b7-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bb1b7-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="bb1b7-154">*policy_setting*</span></span>|<span data-ttu-id="bb1b7-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="bb1b7-156">Olası değerler şunlardır `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="bb1b7-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="bb1b7-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb1b7-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb1b7-158">Child Elements</span></span>  
 <span data-ttu-id="bb1b7-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb1b7-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb1b7-160">Parent Elements</span></span>  
  
|<span data-ttu-id="bb1b7-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb1b7-161">Element</span></span>|<span data-ttu-id="bb1b7-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb1b7-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb1b7-163">\<türü ></span><span class="sxs-lookup"><span data-stu-id="bb1b7-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="bb1b7-164">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="bb1b7-165">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="bb1b7-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="bb1b7-166">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="bb1b7-167">\<yöntemi ></span><span class="sxs-lookup"><span data-stu-id="bb1b7-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="bb1b7-168">Bir yönteme yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb1b7-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb1b7-169">Remarks</span></span>  
 <span data-ttu-id="bb1b7-170">`<ImpliesType>` öğesi öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="bb1b7-171">Aşağıdaki senaryoyu ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="bb1b7-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="bb1b7-172">Bir yordamın bir tür üzerinde yansıtılması gerekiyorsa, ikinci bir tür üzerinde yansıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="bb1b7-173">Statik analiz bunun gerekli olduğunu belirtmediği için, ikinci türün örtük olarak belirtilen örneklenmesi için meta veriler kullanılamaz durumda değildir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="bb1b7-174">En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleriyle genel örneklemelerdir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="bb1b7-175">`<ImpliesType>` öğesi, kendi üst öğesi tarafından belirtilen türde yansıma için ihtiyacı olan ve `<ImpliesType>` öğesi tarafından belirtilen türde yansıma gereksinimini ifade eden varsayımıyla tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="bb1b7-176">Örneğin, aşağıdaki yansıma yönergeleri iki tür için geçerlidir `Explicit<T>` ve `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="bb1b7-177">`Explicit` örneklemesinin tanımlanmış bir `Dynamic` ilkesi ayarı yoksa, bu yönergenin etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="bb1b7-178">Örneğin, bu durum `Explicit<Int32>`için ise, `Implicit<Int32>` ortak üyeleri kök olarak oluşturulur ve meta verileri dinamik programlama için erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="bb1b7-179">Aşağıda, en az bir seri hale getirici için geçerli olan gerçek dünyada bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="bb1b7-180">Yönergeler *`IList<`olarak yazılmış bir şeyi yansıtan* gereksinimi yakalar`>` aynı zamanda ilgili `List<`herhangi bir uygulama için gerekli olmadan`>` *bir* tür üzerinde yansıtılıyor ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="bb1b7-181">`<ImpliesType>` öğesi, bir `<Method>` öğesi içinde de görünebilir, çünkü bazı durumlarda genel bir yöntemi örneklemede bir tür örneklemesi yansıtılıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="bb1b7-182">Örneğin, belirli bir kitaplığın ilişkili <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleriyle birlikte dinamik olarak erişdiğinin `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` genel bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="bb1b7-183">Bu, şöyle ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="bb1b7-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb1b7-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1b7-184">See also</span></span>

- [<span data-ttu-id="bb1b7-185">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bb1b7-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="bb1b7-186">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="bb1b7-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="bb1b7-187">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="bb1b7-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

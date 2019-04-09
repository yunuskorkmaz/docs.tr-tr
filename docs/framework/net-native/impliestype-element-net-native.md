---
title: <ImpliesType> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef238a2cb852ecd7fa3f0e2dbe4048ff03a4139
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080884"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="396e1-102">\<Impliestype > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="396e1-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="396e1-103">Bu ilke kapsayan tür veya yöntem uygulanmışsa, ilke bir türe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="396e1-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="396e1-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="396e1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="396e1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="396e1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="396e1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="396e1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="396e1-107">Attributes</span></span>  
  
|<span data-ttu-id="396e1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="396e1-108">Attribute</span></span>|<span data-ttu-id="396e1-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="396e1-109">Attribute type</span></span>|<span data-ttu-id="396e1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="396e1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="396e1-111">Genel</span><span class="sxs-lookup"><span data-stu-id="396e1-111">General</span></span>|<span data-ttu-id="396e1-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-112">Required attribute.</span></span> <span data-ttu-id="396e1-113">Tür adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="396e1-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="396e1-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="396e1-114">Reflection</span></span>|<span data-ttu-id="396e1-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-115">Optional attribute.</span></span> <span data-ttu-id="396e1-116">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="396e1-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="396e1-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="396e1-117">Reflection</span></span>|<span data-ttu-id="396e1-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-118">Optional attribute.</span></span> <span data-ttu-id="396e1-119">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="396e1-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="396e1-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="396e1-120">Reflection</span></span>|<span data-ttu-id="396e1-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-121">Optional attribute.</span></span> <span data-ttu-id="396e1-122">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="396e1-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="396e1-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="396e1-123">Serialization</span></span>|<span data-ttu-id="396e1-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-124">Optional attribute.</span></span> <span data-ttu-id="396e1-125">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="396e1-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="396e1-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="396e1-126">Serialization</span></span>|<span data-ttu-id="396e1-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-127">Optional attribute.</span></span> <span data-ttu-id="396e1-128">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="396e1-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="396e1-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="396e1-129">Serialization</span></span>|<span data-ttu-id="396e1-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-130">Optional attribute.</span></span> <span data-ttu-id="396e1-131">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="396e1-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="396e1-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="396e1-132">Serialization</span></span>|<span data-ttu-id="396e1-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-133">Optional attribute.</span></span> <span data-ttu-id="396e1-134">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="396e1-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="396e1-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="396e1-135">Interop</span></span>|<span data-ttu-id="396e1-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-136">Optional attribute.</span></span> <span data-ttu-id="396e1-137">Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi</span><span class="sxs-lookup"><span data-stu-id="396e1-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="396e1-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="396e1-138">Interop</span></span>|<span data-ttu-id="396e1-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-139">Optional attribute.</span></span> <span data-ttu-id="396e1-140">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="396e1-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="396e1-141">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="396e1-141">Interop</span></span>|<span data-ttu-id="396e1-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="396e1-142">Optional attribute.</span></span> <span data-ttu-id="396e1-143">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="396e1-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="396e1-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="396e1-144">Name attribute</span></span>  
  
|<span data-ttu-id="396e1-145">Değer</span><span class="sxs-lookup"><span data-stu-id="396e1-145">Value</span></span>|<span data-ttu-id="396e1-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="396e1-146">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="396e1-147">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="396e1-147">type_name</span></span>*|<span data-ttu-id="396e1-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="396e1-148">The type name.</span></span> <span data-ttu-id="396e1-149">Türü bu tarafından temsil edilen varsa `<ImpliesType>` öğe kapsayıcı olarak aynı ad alanında bulunan `<Type>` öğesi *type_name* kendi ad alanı olmayan bir türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="396e1-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="396e1-150">Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="396e1-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="396e1-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="396e1-151">All other attributes</span></span>  
  
|<span data-ttu-id="396e1-152">Değer</span><span class="sxs-lookup"><span data-stu-id="396e1-152">Value</span></span>|<span data-ttu-id="396e1-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="396e1-153">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="396e1-154">policy_setting</span><span class="sxs-lookup"><span data-stu-id="396e1-154">policy_setting</span></span>*|<span data-ttu-id="396e1-155">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="396e1-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="396e1-156">Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="396e1-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="396e1-157">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="396e1-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="396e1-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="396e1-158">Child Elements</span></span>  
 <span data-ttu-id="396e1-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="396e1-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="396e1-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="396e1-160">Parent Elements</span></span>  
  
|<span data-ttu-id="396e1-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="396e1-161">Element</span></span>|<span data-ttu-id="396e1-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="396e1-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="396e1-163">\<türü ></span><span class="sxs-lookup"><span data-stu-id="396e1-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="396e1-164">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="396e1-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="396e1-165">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="396e1-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="396e1-166">Yansıma ilkesini, oluşturulmuş bir genel türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="396e1-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="396e1-167">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="396e1-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="396e1-168">Yansıma ilkesini bir yönteme uygulanır.</span><span class="sxs-lookup"><span data-stu-id="396e1-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="396e1-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="396e1-169">Remarks</span></span>  
 <span data-ttu-id="396e1-170">`<ImpliesType>` Öğesi kitaplığı tarafından kullanılmak üzere öncelikli olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="396e1-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="396e1-171">Bunu aşağıdaki senaryoyu ele alır:</span><span class="sxs-lookup"><span data-stu-id="396e1-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="396e1-172">Bir yordam bir yola yansıtacak şekilde gerekiyorsa, ikinci bir türde yansıtacak şekilde mutlaka gerekir.</span><span class="sxs-lookup"><span data-stu-id="396e1-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="396e1-173">İkinci tür örtük örneklemesi için meta veriler, aksi takdirde statik analiz gerekli olduğunu göstermez için kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="396e1-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="396e1-174">En yaygın olarak, iki tür paylaşılan tür bağımsız değişkenleri ile genel örnek oluşturma ' dir.</span><span class="sxs-lookup"><span data-stu-id="396e1-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="396e1-175">`<ImpliesType>` Öğesi kendi üst öğesi tarafından belirtilen tür yansıma gereksinimini tarafından belirtilen tür yansıma gereksinimini gelir birlikte tanımlandı `<ImpliesType>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="396e1-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="396e1-176">Örneğin, aşağıdaki yansıma yönergelerini iki türleri için geçerli `Explicit<T>` ve `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="396e1-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="396e1-177">Bu yönerge sürece hiçbir etkisi olmaz örneklemesi `Explicit` tanımlanan sahip `Dynamic` ilke ayarı.</span><span class="sxs-lookup"><span data-stu-id="396e1-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="396e1-178">Örneğin, bu durum ise, `Explicit<Int32>`, `Implicit<Int32>` kendi genel örneği üyeler kök erişim izni verilmiş ve bunların meta verilerini dinamik programlama için erişilebilir hale getirdik.</span><span class="sxs-lookup"><span data-stu-id="396e1-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="396e1-179">En az bir seri hale getirici için geçerlidir, gerçek bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="396e1-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="396e1-180">Üzerinde bir yansıtma olarak belirlenmiş olan gereksinim yönergeleri yakalama `IList<` *bir şey* `>` ayrıca ilgili yansıtan içerir `List<` *bir şey* `>` herhangi bir uygulama başına ek açıklama gerektirmeden türü.</span><span class="sxs-lookup"><span data-stu-id="396e1-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="396e1-181">`<ImpliesType>` Öğesi içinde de görünebilir bir `<Method>` öğesi, bazı durumlarda bir genel yöntem örnekleme yansıtan bir tür örneği oluşturmada gösterdiğinden.</span><span class="sxs-lookup"><span data-stu-id="396e1-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="396e1-182">Örneğin, bir genel yöntem Imagine `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` belirli bir kitaplık dinamik olarak ilişkili birlikte erişecek <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleri.</span><span class="sxs-lookup"><span data-stu-id="396e1-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="396e1-183">Bu olarak ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="396e1-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="396e1-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="396e1-184">See also</span></span>

- [<span data-ttu-id="396e1-185">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="396e1-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="396e1-186">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="396e1-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="396e1-187">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="396e1-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

---
title: "&lt;ImpliesType&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90e079b593ed124da79f5f87b5189d199bc4572a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltimpliestypegt-element-net-native"></a><span data-ttu-id="655a8-102">&lt;ImpliesType&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="655a8-102">&lt;ImpliesType&gt; Element (.NET Native)</span></span>
<span data-ttu-id="655a8-103">Bu ilkeyi içeren türü veya yöntemi uygulanmışsa, ilkeyi bir türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="655a8-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="655a8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="655a8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="655a8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="655a8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="655a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="655a8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="655a8-107">Attributes</span></span>  
  
|<span data-ttu-id="655a8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="655a8-108">Attribute</span></span>|<span data-ttu-id="655a8-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="655a8-109">Attribute type</span></span>|<span data-ttu-id="655a8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="655a8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="655a8-111">Genel</span><span class="sxs-lookup"><span data-stu-id="655a8-111">General</span></span>|<span data-ttu-id="655a8-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-112">Required attribute.</span></span> <span data-ttu-id="655a8-113">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="655a8-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="655a8-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="655a8-114">Reflection</span></span>|<span data-ttu-id="655a8-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-115">Optional attribute.</span></span> <span data-ttu-id="655a8-116">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="655a8-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="655a8-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="655a8-117">Reflection</span></span>|<span data-ttu-id="655a8-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-118">Optional attribute.</span></span> <span data-ttu-id="655a8-119">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="655a8-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="655a8-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="655a8-120">Reflection</span></span>|<span data-ttu-id="655a8-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-121">Optional attribute.</span></span> <span data-ttu-id="655a8-122">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="655a8-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="655a8-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="655a8-123">Serialization</span></span>|<span data-ttu-id="655a8-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-124">Optional attribute.</span></span> <span data-ttu-id="655a8-125">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="655a8-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="655a8-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="655a8-126">Serialization</span></span>|<span data-ttu-id="655a8-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-127">Optional attribute.</span></span> <span data-ttu-id="655a8-128">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="655a8-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="655a8-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="655a8-129">Serialization</span></span>|<span data-ttu-id="655a8-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-130">Optional attribute.</span></span> <span data-ttu-id="655a8-131">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="655a8-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="655a8-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="655a8-132">Serialization</span></span>|<span data-ttu-id="655a8-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-133">Optional attribute.</span></span> <span data-ttu-id="655a8-134">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="655a8-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="655a8-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="655a8-135">Interop</span></span>|<span data-ttu-id="655a8-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-136">Optional attribute.</span></span> <span data-ttu-id="655a8-137">Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi</span><span class="sxs-lookup"><span data-stu-id="655a8-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="655a8-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="655a8-138">Interop</span></span>|<span data-ttu-id="655a8-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-139">Optional attribute.</span></span> <span data-ttu-id="655a8-140">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="655a8-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="655a8-141">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="655a8-141">Interop</span></span>|<span data-ttu-id="655a8-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="655a8-142">Optional attribute.</span></span> <span data-ttu-id="655a8-143">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="655a8-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="655a8-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="655a8-144">Name attribute</span></span>  
  
|<span data-ttu-id="655a8-145">Değer</span><span class="sxs-lookup"><span data-stu-id="655a8-145">Value</span></span>|<span data-ttu-id="655a8-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="655a8-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="655a8-147">*TYPE_NAME*</span><span class="sxs-lookup"><span data-stu-id="655a8-147">*type_name*</span></span>|<span data-ttu-id="655a8-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="655a8-148">The type name.</span></span> <span data-ttu-id="655a8-149">Türü bu tarafından temsil edilen varsa `<ImpliesType>` öğesi kendi içeren olarak aynı ad bulunduğu `<Type>` öğesi, *type_name* kendi ad olmadan türünün adı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="655a8-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="655a8-150">Aksi takdirde, *type_name* tam olarak nitelenmiş tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="655a8-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="655a8-151">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="655a8-151">All other attributes</span></span>  
  
|<span data-ttu-id="655a8-152">Değer</span><span class="sxs-lookup"><span data-stu-id="655a8-152">Value</span></span>|<span data-ttu-id="655a8-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="655a8-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="655a8-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="655a8-154">*policy_setting*</span></span>|<span data-ttu-id="655a8-155">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="655a8-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="655a8-156">Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="655a8-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="655a8-157">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="655a8-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="655a8-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="655a8-158">Child Elements</span></span>  
 <span data-ttu-id="655a8-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="655a8-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="655a8-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="655a8-160">Parent Elements</span></span>  
  
|<span data-ttu-id="655a8-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="655a8-161">Element</span></span>|<span data-ttu-id="655a8-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="655a8-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="655a8-163">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="655a8-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="655a8-164">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="655a8-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="655a8-165">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="655a8-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="655a8-166">Yansıma İlkesi, yapılandırılmış bir genel tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="655a8-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="655a8-167">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="655a8-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="655a8-168">Yansıma ilke için bir yöntem uygulanır.</span><span class="sxs-lookup"><span data-stu-id="655a8-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655a8-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="655a8-169">Remarks</span></span>  
 <span data-ttu-id="655a8-170">`<ImpliesType>` Öğesi kitaplıkları tarafından kullanılmak üzere öncelikle amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="655a8-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="655a8-171">Bunu aşağıdaki senaryoyu ele alır:</span><span class="sxs-lookup"><span data-stu-id="655a8-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="655a8-172">Bir yordam bir yola yansıtmak gerekirse, ikinci bir türde yansıtacak şekilde mutlaka gerekir.</span><span class="sxs-lookup"><span data-stu-id="655a8-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="655a8-173">Dolaylı oluşturmada ikinci türü için meta veriler, aksi takdirde statik çözümleme gerekli olduğunu göstermez için kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="655a8-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="655a8-174">En yaygın olarak, iki genel örneklemesi paylaşılan tür bağımsız değişkenleri ile türleridir.</span><span class="sxs-lookup"><span data-stu-id="655a8-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="655a8-175">`<ImpliesType>` Öğesi kendi üst öğesi tarafından belirtilen tür yansıma gereksinimini tarafından belirtilen tür yansıma gereksinimini gelir varsayım ile tanımlanmıştı `<ImpliesType>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="655a8-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="655a8-176">Örneğin, aşağıdaki yansıma yönergeleri iki türleri için geçerli `Explicit<T>` ve `Implicit<T>`.</span><span class="sxs-lookup"><span data-stu-id="655a8-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="655a8-177">Bu yönerge sürece etkisi yoktur, bir örnek oluşturma `Explicit` tanımlanan sahip `Dynamic` ilke ayarı.</span><span class="sxs-lookup"><span data-stu-id="655a8-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="655a8-178">Örneğin, bu durum ise `Explicit<Int32>`, `Implicit<Int32>` ile kendi ortak örneği üyeleri kökü ve bunların meta verilerini dinamik programlama için erişilebilir hale.</span><span class="sxs-lookup"><span data-stu-id="655a8-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="655a8-179">En az bir seri hale getirici geçerlidir gerçek örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="655a8-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="655a8-180">Yönergeleri şeye yansıtma olarak yazılan gereksinim yakalama `IList<` *bir şey* `>` de karşılık gelen üzerinde yansıtma içerir `List<` *bir şey* `>` tüm uygulama başına ek açıklama gerektirmeden türü.</span><span class="sxs-lookup"><span data-stu-id="655a8-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="655a8-181">`<ImpliesType>` Öğesi içinde de görüntülenebilir bir `<Method>` öğesi, bazı durumlarda genel yöntem başlatmasını türü örnek oluşturma üzerinde yansıtma gösterdiğinden.</span><span class="sxs-lookup"><span data-stu-id="655a8-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="655a8-182">Örneğin, bir genel yöntem düşünün `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` belirli bir kitaplık dinamik olarak ilişkili birlikte erişecek <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleri.</span><span class="sxs-lookup"><span data-stu-id="655a8-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="655a8-183">Bu olarak ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="655a8-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="655a8-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="655a8-184">See Also</span></span>  
 [<span data-ttu-id="655a8-185">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="655a8-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="655a8-186">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="655a8-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="655a8-187">Çalışma zamanı yönerge İlkesi ayarları</span><span class="sxs-lookup"><span data-stu-id="655a8-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

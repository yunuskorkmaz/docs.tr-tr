---
title: <ImpliesType>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181010"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="b281d-102">\<ImpliesType> Öğesi (.NET Yerli)</span><span class="sxs-lookup"><span data-stu-id="b281d-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="b281d-103">Bu ilke, içeren tür veya yönteme uygulanmışsa, bir türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="b281d-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b281d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b281d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b281d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b281d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b281d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b281d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b281d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b281d-107">Attributes</span></span>  
  
|<span data-ttu-id="b281d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b281d-108">Attribute</span></span>|<span data-ttu-id="b281d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="b281d-109">Attribute type</span></span>|<span data-ttu-id="b281d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b281d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="b281d-111">Genel</span><span class="sxs-lookup"><span data-stu-id="b281d-111">General</span></span>|<span data-ttu-id="b281d-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-112">Required attribute.</span></span> <span data-ttu-id="b281d-113">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b281d-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="b281d-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b281d-114">Reflection</span></span>|<span data-ttu-id="b281d-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-115">Optional attribute.</span></span> <span data-ttu-id="b281d-116">Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b281d-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b281d-117">Reflection</span></span>|<span data-ttu-id="b281d-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-118">Optional attribute.</span></span> <span data-ttu-id="b281d-119">Program öğeleri hakkında bilgi için sorgu denetimleri, ancak herhangi bir çalışma zamanı erişim etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="b281d-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b281d-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b281d-120">Reflection</span></span>|<span data-ttu-id="b281d-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-121">Optional attribute.</span></span> <span data-ttu-id="b281d-122">Dinamik programlamayı etkinleştirmek için oluşturucular, yöntemler, alanlar, özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b281d-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b281d-123">Serialization</span></span>|<span data-ttu-id="b281d-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-124">Optional attribute.</span></span> <span data-ttu-id="b281d-125">Newtonsoft JSON serileştiricisi gibi kitaplıklar tarafından seri hale getirilecek ve deserialized türü örnekleri etkinleştirmek için, yapıcılar, alanlar ve özelliklere çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b281d-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b281d-126">Serialization</span></span>|<span data-ttu-id="b281d-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-127">Optional attribute.</span></span> <span data-ttu-id="b281d-128">Sınıfı kullanan serileştirme ilkesini <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b281d-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b281d-129">Serialization</span></span>|<span data-ttu-id="b281d-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-130">Optional attribute.</span></span> <span data-ttu-id="b281d-131">Sınıfı kullanan JSON serileştirme <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b281d-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b281d-132">Serialization</span></span>|<span data-ttu-id="b281d-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-133">Optional attribute.</span></span> <span data-ttu-id="b281d-134">Sınıfı kullanan XML serileştirme <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b281d-135">Interop</span><span class="sxs-lookup"><span data-stu-id="b281d-135">Interop</span></span>|<span data-ttu-id="b281d-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-136">Optional attribute.</span></span> <span data-ttu-id="b281d-137">Başvuru türlerini Windows Runtime ve COM'a göre mareşalleme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b281d-138">Interop</span><span class="sxs-lookup"><span data-stu-id="b281d-138">Interop</span></span>|<span data-ttu-id="b281d-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-139">Optional attribute.</span></span> <span data-ttu-id="b281d-140">Temsilci türlerini işlev işaretçisi olarak yerel koda göre işaretetmek için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b281d-141">Interop</span><span class="sxs-lookup"><span data-stu-id="b281d-141">Interop</span></span>|<span data-ttu-id="b281d-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b281d-142">Optional attribute.</span></span> <span data-ttu-id="b281d-143">Değer türlerini yerel koda göre mareşalleştirmek için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="b281d-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="b281d-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="b281d-144">Name attribute</span></span>  
  
|<span data-ttu-id="b281d-145">Değer</span><span class="sxs-lookup"><span data-stu-id="b281d-145">Value</span></span>|<span data-ttu-id="b281d-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b281d-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b281d-147">*Type_name*</span><span class="sxs-lookup"><span data-stu-id="b281d-147">*type_name*</span></span>|<span data-ttu-id="b281d-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="b281d-148">The type name.</span></span> <span data-ttu-id="b281d-149">Bu `<ImpliesType>` öğe tarafından temsil edilen tür, içerdiği `<Type>` öğeyle aynı ad alanında bulunuyorsa, *type_name* ad alanı olmadan türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b281d-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="b281d-150">Aksi takdirde, *type_name* tam nitelikli tür adı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="b281d-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="b281d-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b281d-151">All other attributes</span></span>  
  
|<span data-ttu-id="b281d-152">Değer</span><span class="sxs-lookup"><span data-stu-id="b281d-152">Value</span></span>|<span data-ttu-id="b281d-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b281d-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b281d-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b281d-154">*policy_setting*</span></span>|<span data-ttu-id="b281d-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="b281d-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="b281d-156">Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="b281d-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b281d-157">Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b281d-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b281d-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b281d-158">Child Elements</span></span>  
 <span data-ttu-id="b281d-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="b281d-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b281d-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b281d-160">Parent Elements</span></span>  
  
|<span data-ttu-id="b281d-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="b281d-161">Element</span></span>|<span data-ttu-id="b281d-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b281d-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b281d-163">\<Tip></span><span class="sxs-lookup"><span data-stu-id="b281d-163">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="b281d-164">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="b281d-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="b281d-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="b281d-165">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b281d-166">Yapılı genel bir türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b281d-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="b281d-167">\<Yöntem></span><span class="sxs-lookup"><span data-stu-id="b281d-167">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="b281d-168">Yansıma ilkesini bir yönteme uygular.</span><span class="sxs-lookup"><span data-stu-id="b281d-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b281d-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b281d-169">Remarks</span></span>  
 <span data-ttu-id="b281d-170">Öğe `<ImpliesType>` öncelikle kitaplıklar tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b281d-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="b281d-171">Aşağıdaki senaryoyu ele alar:</span><span class="sxs-lookup"><span data-stu-id="b281d-171">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="b281d-172">Bir yordamın bir türe yansıması gerekiyorsa, mutlaka ikinci bir türe yansıtması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b281d-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="b281d-173">Statik çözümleme gerekli olduğunu göstermez, çünkü ikinci türün zımni anlık için meta veriler, aksi takdirde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b281d-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="b281d-174">En sık, iki tür paylaşılan türü bağımsız değişkenleri ile genel anlık vardır.</span><span class="sxs-lookup"><span data-stu-id="b281d-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="b281d-175">Öğe, `<ImpliesType>` üst öğesi tarafından belirtilen türüzerinde yansıma `<ImpliesType>` gereksiniminin, öğe tarafından belirtilen türüzerinde yansıma gereksinimi anlamına geldiği varsayımıyla tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b281d-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="b281d-176">Örneğin, aşağıdaki yansıma yönergeleri iki tür `Explicit<T>` için `Implicit<T>`geçerlidir ve .</span><span class="sxs-lookup"><span data-stu-id="b281d-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="b281d-177">Tanımlı `Explicit` `Dynamic` bir ilke ayarı anlık olmadığı sürece bu yönergenin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b281d-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="b281d-178">Örneğin, bu durumda `Explicit<Int32>`, `Implicit<Int32>` genel üyeleri köklü anında ve meta verileri dinamik programlama için erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="b281d-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="b281d-179">Aşağıda, en az bir serializer için geçerli olan gerçek dünya örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b281d-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="b281d-180">Yönergeler, `IList<`bir şey olarak yazılan *bir* `>` şeyi yansıtmanın, uygulama `List<`başına ek açıklama gerektirmeden ilgili *bir şey* `>` türünü yansıtmayı da içerdiği gereksinimini yakalar.</span><span class="sxs-lookup"><span data-stu-id="b281d-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="b281d-181">Bazı `<ImpliesType>` durumlarda genel bir `<Method>` yöntemin anlık olarak bir tür anlık yansıması anlamına gelir, çünkü öğe de bir öğe içinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="b281d-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="b281d-182">Örneğin, belirli bir `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` kitaplığın ilişkili <xref:System.Collections.Generic.List%601> ve <xref:System.Array> türleri ile birlikte dinamik olarak erişeceği genel bir yöntem düşünün.</span><span class="sxs-lookup"><span data-stu-id="b281d-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="b281d-183">Bu olarak ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="b281d-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b281d-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b281d-184">See also</span></span>

- [<span data-ttu-id="b281d-185">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b281d-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b281d-186">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="b281d-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="b281d-187">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="b281d-187">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

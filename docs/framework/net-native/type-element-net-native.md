---
title: <Type> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: e71df41c4a37206910d835ee85dc3d68b4cbad4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287715"
---
# <a name="type-element-net-native"></a><span data-ttu-id="b36be-102">\<Type> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b36be-102">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="b36be-103">Çalışma zamanı ilkesini sınıf veya yapı gibi belirli bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-103">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="b36be-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b36be-104">Syntax</span></span>

```xml
<Type Name="type_name"
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

## <a name="attributes-and-elements"></a><span data-ttu-id="b36be-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b36be-105">Attributes and Elements</span></span>

<span data-ttu-id="b36be-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b36be-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b36be-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b36be-107">Attributes</span></span>

|<span data-ttu-id="b36be-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b36be-108">Attribute</span></span>|<span data-ttu-id="b36be-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="b36be-109">Attribute type</span></span>|<span data-ttu-id="b36be-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36be-110">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="b36be-111">Genel</span><span class="sxs-lookup"><span data-stu-id="b36be-111">General</span></span>|<span data-ttu-id="b36be-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-112">Required attribute.</span></span> <span data-ttu-id="b36be-113">Tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b36be-113">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="b36be-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b36be-114">Reflection</span></span>|<span data-ttu-id="b36be-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-115">Optional attribute.</span></span> <span data-ttu-id="b36be-116">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="b36be-116">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="b36be-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b36be-117">Reflection</span></span>|<span data-ttu-id="b36be-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-118">Optional attribute.</span></span> <span data-ttu-id="b36be-119">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="b36be-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="b36be-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b36be-120">Reflection</span></span>|<span data-ttu-id="b36be-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-121">Optional attribute.</span></span> <span data-ttu-id="b36be-122">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="b36be-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="b36be-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b36be-123">Serialization</span></span>|<span data-ttu-id="b36be-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-124">Optional attribute.</span></span> <span data-ttu-id="b36be-125">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="b36be-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="b36be-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b36be-126">Serialization</span></span>|<span data-ttu-id="b36be-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-127">Optional attribute.</span></span> <span data-ttu-id="b36be-128">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b36be-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="b36be-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b36be-129">Serialization</span></span>|<span data-ttu-id="b36be-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-130">Optional attribute.</span></span> <span data-ttu-id="b36be-131">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b36be-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="b36be-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b36be-132">Serialization</span></span>|<span data-ttu-id="b36be-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-133">Optional attribute.</span></span> <span data-ttu-id="b36be-134">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b36be-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="b36be-135">Interop</span><span class="sxs-lookup"><span data-stu-id="b36be-135">Interop</span></span>|<span data-ttu-id="b36be-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-136">Optional attribute.</span></span> <span data-ttu-id="b36be-137">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b36be-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="b36be-138">Interop</span><span class="sxs-lookup"><span data-stu-id="b36be-138">Interop</span></span>|<span data-ttu-id="b36be-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-139">Optional attribute.</span></span> <span data-ttu-id="b36be-140">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b36be-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="b36be-141">Interop</span><span class="sxs-lookup"><span data-stu-id="b36be-141">Interop</span></span>|<span data-ttu-id="b36be-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b36be-142">Optional attribute.</span></span> <span data-ttu-id="b36be-143">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b36be-143">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="b36be-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="b36be-144">Name attribute</span></span>

|<span data-ttu-id="b36be-145">Değer</span><span class="sxs-lookup"><span data-stu-id="b36be-145">Value</span></span>|<span data-ttu-id="b36be-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36be-146">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="b36be-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="b36be-147">*type_name*</span></span>|<span data-ttu-id="b36be-148">Tür adı.</span><span class="sxs-lookup"><span data-stu-id="b36be-148">The type name.</span></span> <span data-ttu-id="b36be-149">Bu `<Type>` öğe bir [\<Namespace>](namespace-element-net-native.md) öğe ya da başka bir öğe alt öğesi ise `<Type>` , *type_name* ad alanı olmadan türün adını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b36be-149">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="b36be-150">Aksi takdirde, *type_name* tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="b36be-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="b36be-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b36be-151">All other attributes</span></span>

|<span data-ttu-id="b36be-152">Değer</span><span class="sxs-lookup"><span data-stu-id="b36be-152">Value</span></span>|<span data-ttu-id="b36be-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36be-153">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="b36be-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b36be-154">*policy_setting*</span></span>|<span data-ttu-id="b36be-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="b36be-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="b36be-156">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="b36be-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b36be-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b36be-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b36be-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b36be-158">Child Elements</span></span>

|<span data-ttu-id="b36be-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="b36be-159">Element</span></span>|<span data-ttu-id="b36be-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36be-160">Description</span></span>|
|-------------|-----------------|
|[\<AttributeImplies>](attributeimplies-element-net-native.md)|<span data-ttu-id="b36be-161">Kapsayan tür bir öznitelik ise, özniteliğin uygulandığı kod öğeleri için çalışma zamanı ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b36be-161">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="b36be-162">Bu türe ait bir olaya yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-162">Applies reflection policy to an event belonging to this type.</span></span>|
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="b36be-163">Bu türe ait olan bir alana yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-163">Applies reflection policy to a field belonging to this type.</span></span>|
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="b36be-164">İlkeyi genel bir türün parametre türüne uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-164">Applies policy to the parameter type of a generic type.</span></span>|
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="b36be-165">İlke, kapsayan öğe tarafından temsil edilen türe uygulanmışsa ilkeyi bir türe uygular `<Type>` .</span><span class="sxs-lookup"><span data-stu-id="b36be-165">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="b36be-166">Bu türe ait bir yönteme yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-166">Applies reflection policy to a method belonging to this type.</span></span>|
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="b36be-167">Bu türe ait oluşturulmuş bir genel metoda yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-167">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="b36be-168">Yansıma ilkesini bu türe ait olan bir özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-168">Applies reflection policy to a property belonging to this type.</span></span>|
|[\<Subtypes>](subtypes-element-net-native.md)|<span data-ttu-id="b36be-169">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-169">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="b36be-170">Yansıtma ilkesini iç içe bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-170">Applies reflection policy to a nested type.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b36be-171">Yansıma ilkesini oluşturulmuş genel bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-171">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b36be-172">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b36be-172">Parent Elements</span></span>

|<span data-ttu-id="b36be-173">Öğe</span><span class="sxs-lookup"><span data-stu-id="b36be-173">Element</span></span>|<span data-ttu-id="b36be-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b36be-174">Description</span></span>|
|-------------|-----------------|
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="b36be-175">Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="b36be-175">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="b36be-176">Belirtilen derlemedeki tüm türlere yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-176">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="b36be-177">Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b36be-177">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="b36be-178">Bir ad alanındaki tüm türlere yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-178">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="b36be-179">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-179">Applies reflection policy to a type and all its members.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b36be-180">Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-180">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b36be-181">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b36be-181">Remarks</span></span>

<span data-ttu-id="b36be-182">Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b36be-182">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="b36be-183">Hiçbiri yoksa, `<Type>` öğesi, alt türleri ayrı Üyeler için ilke tanımlayan bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="b36be-183">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="b36be-184">Bir `<Type>` öğe,, veya öğesinin alt öğesi ise, [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) `<Type>` [\<TypeInstantiation>](typeinstantiation-element-net-native.md) üst öğe tarafından tanımlanan ilke ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b36be-184">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="b36be-185">`<Type>`Genel türün bir öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="b36be-185">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="b36be-186">Oluşturulan genel türlerin ilkesi öğesi tarafından tanımlanır [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b36be-186">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="b36be-187">Tür genel bir tür ise, adı bir aksan işareti simgesiyle ( \` ) ve ardından Genel parametrelerin sayısı ile donatılmış olur.</span><span class="sxs-lookup"><span data-stu-id="b36be-187">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="b36be-188">Örneğin, `Name` `<Type>` sınıf için bir öğenin özniteliği <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> olarak görünür ``Name="System.Collections.Generic.List`1"`` .</span><span class="sxs-lookup"><span data-stu-id="b36be-188">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="b36be-189">Örnek</span><span class="sxs-lookup"><span data-stu-id="b36be-189">Example</span></span>

<span data-ttu-id="b36be-190">Aşağıdaki örnek, sınıfının alanları, özellikleri ve yöntemleri hakkındaki bilgileri göstermek için yansımayı kullanır <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b36be-190">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="b36be-191">Örnekteki değişken `b` bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimdir.</span><span class="sxs-lookup"><span data-stu-id="b36be-191">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="b36be-192">Örnek yalnızca tür bilgilerini aldığından meta verilerin kullanılabilirliği `Browse` ilke ayarıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b36be-192">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="b36be-193">Sınıfın meta verileri <xref:System.Collections.Generic.List%601> .NET Native araç zinciri tarafından otomatik olarak dahil edilmediğinden, örnek, istenen üye bilgilerini çalışma zamanında görüntüleyemez.</span><span class="sxs-lookup"><span data-stu-id="b36be-193">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="b36be-194">Gerekli meta verileri sağlamak için, aşağıdaki `<Type>` öğeyi çalışma zamanı yönergeleri dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b36be-194">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="b36be-195">Bir üst [<ad alanı \> ](namespace-element-net-native.md) öğesi sağladığımızda, öğesinde tam nitelikli bir tür adı sunduğumuz için unutmayın `<Type>` .</span><span class="sxs-lookup"><span data-stu-id="b36be-195">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="b36be-196">Örnek</span><span class="sxs-lookup"><span data-stu-id="b36be-196">Example</span></span>

 <span data-ttu-id="b36be-197">Aşağıdaki örnek, <xref:System.Reflection.PropertyInfo> özelliğini temsil eden bir nesneyi almak için yansıma kullanır <xref:System.String.Chars%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b36be-197">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b36be-198">Daha sonra yöntemi, <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> bir dizedeki yedinci karakterin değerini almak ve dizedeki tüm karakterleri göstermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b36be-198">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="b36be-199">Örnekteki değişken `b` bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimdir.</span><span class="sxs-lookup"><span data-stu-id="b36be-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="b36be-200">Nesnenin meta verileri <xref:System.String> kullanılabilir olmadığından, yöntem çağrısı, <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.NullReferenceException> .NET Native araç zinciri ile derlendikleri zaman çalışma zamanında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b36be-200">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="b36be-201">Özel durumu ortadan kaldırmak ve gerekli meta verileri sağlamak için, `<Type>` çalışma zamanı yönergeleri dosyasına aşağıdaki öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b36be-201">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="b36be-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b36be-202">See also</span></span>

- [<span data-ttu-id="b36be-203">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b36be-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b36be-204">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="b36be-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="b36be-205">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="b36be-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

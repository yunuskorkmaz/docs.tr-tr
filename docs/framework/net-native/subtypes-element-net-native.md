---
description: 'Daha fazla bilgi edinin: <Subtypes> öğesi (.NET Native)'
title: <Subtypes> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: d30bb482e784d912d3f5d61f688ed2b824e45f27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801962"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="74b6c-103">\<Subtypes> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="74b6c-103">\<Subtypes> Element (.NET Native)</span></span>

<span data-ttu-id="74b6c-104">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="74b6c-104">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b6c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="74b6c-105">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74b6c-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74b6c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="74b6c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74b6c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74b6c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74b6c-108">Attributes</span></span>  
  
|<span data-ttu-id="74b6c-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="74b6c-109">Attribute</span></span>|<span data-ttu-id="74b6c-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="74b6c-110">Attribute type</span></span>|<span data-ttu-id="74b6c-111">Description</span><span class="sxs-lookup"><span data-stu-id="74b6c-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="74b6c-112">Yansıma</span><span class="sxs-lookup"><span data-stu-id="74b6c-112">Reflection</span></span>|<span data-ttu-id="74b6c-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-113">Optional attribute.</span></span> <span data-ttu-id="74b6c-114">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="74b6c-114">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="74b6c-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="74b6c-115">Reflection</span></span>|<span data-ttu-id="74b6c-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-116">Optional attribute.</span></span> <span data-ttu-id="74b6c-117">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="74b6c-117">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="74b6c-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="74b6c-118">Reflection</span></span>|<span data-ttu-id="74b6c-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-119">Optional attribute.</span></span> <span data-ttu-id="74b6c-120">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="74b6c-120">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="74b6c-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="74b6c-121">Serialization</span></span>|<span data-ttu-id="74b6c-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-122">Optional attribute.</span></span> <span data-ttu-id="74b6c-123">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="74b6c-123">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="74b6c-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="74b6c-124">Serialization</span></span>|<span data-ttu-id="74b6c-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-125">Optional attribute.</span></span> <span data-ttu-id="74b6c-126">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74b6c-126">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="74b6c-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="74b6c-127">Serialization</span></span>|<span data-ttu-id="74b6c-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-128">Optional attribute.</span></span> <span data-ttu-id="74b6c-129">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74b6c-129">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="74b6c-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="74b6c-130">Serialization</span></span>|<span data-ttu-id="74b6c-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-131">Optional attribute.</span></span> <span data-ttu-id="74b6c-132">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74b6c-132">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="74b6c-133">Interop</span><span class="sxs-lookup"><span data-stu-id="74b6c-133">Interop</span></span>|<span data-ttu-id="74b6c-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-134">Optional attribute.</span></span> <span data-ttu-id="74b6c-135">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="74b6c-135">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="74b6c-136">Interop</span><span class="sxs-lookup"><span data-stu-id="74b6c-136">Interop</span></span>|<span data-ttu-id="74b6c-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-137">Optional attribute.</span></span> <span data-ttu-id="74b6c-138">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="74b6c-138">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="74b6c-139">Interop</span><span class="sxs-lookup"><span data-stu-id="74b6c-139">Interop</span></span>|<span data-ttu-id="74b6c-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="74b6c-140">Optional attribute.</span></span> <span data-ttu-id="74b6c-141">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="74b6c-141">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="74b6c-142">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74b6c-142">All attributes</span></span>  
  
|<span data-ttu-id="74b6c-143">Değer</span><span class="sxs-lookup"><span data-stu-id="74b6c-143">Value</span></span>|<span data-ttu-id="74b6c-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74b6c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="74b6c-145">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="74b6c-145">*policy_setting*</span></span>|<span data-ttu-id="74b6c-146">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="74b6c-146">The setting to apply to this policy type.</span></span> <span data-ttu-id="74b6c-147">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="74b6c-147">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="74b6c-148">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="74b6c-148">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74b6c-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74b6c-149">Child Elements</span></span>  

 <span data-ttu-id="74b6c-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="74b6c-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74b6c-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74b6c-151">Parent Elements</span></span>  
  
|<span data-ttu-id="74b6c-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="74b6c-152">Element</span></span>|<span data-ttu-id="74b6c-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74b6c-153">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="74b6c-154">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="74b6c-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74b6c-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74b6c-155">Remarks</span></span>  

 <span data-ttu-id="74b6c-156">`<Subtypes>`Öğesi, ilkeyi kapsayan türünün tüm alt türlerine uygular.</span><span class="sxs-lookup"><span data-stu-id="74b6c-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="74b6c-157">Türetilmiş türlere ve bunların temel sınıflarına farklı ilkeler uygulamak istediğinizde bunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="74b6c-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="74b6c-158">Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır, ancak en az bir tane bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74b6c-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74b6c-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="74b6c-159">Example</span></span>  

 <span data-ttu-id="74b6c-160">Aşağıdaki örnek adlı bir sınıfı ve adlı bir `BaseClass` alt sınıfı tanımlar `Derived1` .</span><span class="sxs-lookup"><span data-stu-id="74b6c-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="74b6c-161">Aşağıdaki kodda gösterildiği gibi, çalışma zamanı yönergeleri dosyası için ve ilkelerini açıkça ayarlar `Dynamic` `Activate` `BaseClass` `Excluded` .</span><span class="sxs-lookup"><span data-stu-id="74b6c-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="74b6c-162">Bu nedenle, türündeki nesneler `BaseClass` dinamik olarak veya sınıf oluşturucusuna çağrılar tarafından başlatılamaz `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="74b6c-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="74b6c-163">Ancak öğesi, `<Subtypes>` öğesinden türetilmiş sınıfların `BaseClass` dinamik olarak ve sınıf oluşturucularının çağrıları aracılığıyla oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="74b6c-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="74b6c-164">`<Subtypes>`Yönergesi nedeniyle, yöntemi çağırarak bir örneği dinamik olarak örnekleyen aşağıdaki kod, `Derived1` başarılı bir <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> şekilde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="74b6c-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="74b6c-165">Burada blok değişkeni, boş bir <xref:System.Windows.Controls.TextBlock> Windows Mağazası uygulamasındaki bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="74b6c-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="74b6c-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74b6c-166">See also</span></span>

- [<span data-ttu-id="74b6c-167">\<Type> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="74b6c-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="74b6c-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="74b6c-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="74b6c-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="74b6c-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="74b6c-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="74b6c-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

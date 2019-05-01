---
title: <Subtypes> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0ec1ed73148b319217a70cc3be99b486be2f8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866866"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="b55cb-102">\<Subtypes > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="b55cb-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="b55cb-103">Çalışma zamanı İlkesi kapsayan türden devralınan tüm sınıflar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b55cb-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b55cb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b55cb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b55cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b55cb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b55cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b55cb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b55cb-107">Attributes</span></span>  
  
|<span data-ttu-id="b55cb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b55cb-108">Attribute</span></span>|<span data-ttu-id="b55cb-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="b55cb-109">Attribute type</span></span>|<span data-ttu-id="b55cb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b55cb-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="b55cb-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b55cb-111">Reflection</span></span>|<span data-ttu-id="b55cb-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-112">Optional attribute.</span></span> <span data-ttu-id="b55cb-113">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="b55cb-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b55cb-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b55cb-114">Reflection</span></span>|<span data-ttu-id="b55cb-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-115">Optional attribute.</span></span> <span data-ttu-id="b55cb-116">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b55cb-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b55cb-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b55cb-117">Reflection</span></span>|<span data-ttu-id="b55cb-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-118">Optional attribute.</span></span> <span data-ttu-id="b55cb-119">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="b55cb-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b55cb-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b55cb-120">Serialization</span></span>|<span data-ttu-id="b55cb-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-121">Optional attribute.</span></span> <span data-ttu-id="b55cb-122">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="b55cb-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b55cb-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b55cb-123">Serialization</span></span>|<span data-ttu-id="b55cb-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-124">Optional attribute.</span></span> <span data-ttu-id="b55cb-125">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b55cb-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b55cb-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b55cb-126">Serialization</span></span>|<span data-ttu-id="b55cb-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-127">Optional attribute.</span></span> <span data-ttu-id="b55cb-128">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b55cb-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b55cb-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b55cb-129">Serialization</span></span>|<span data-ttu-id="b55cb-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-130">Optional attribute.</span></span> <span data-ttu-id="b55cb-131">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b55cb-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b55cb-132">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b55cb-132">Interop</span></span>|<span data-ttu-id="b55cb-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-133">Optional attribute.</span></span> <span data-ttu-id="b55cb-134">Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi</span><span class="sxs-lookup"><span data-stu-id="b55cb-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b55cb-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b55cb-135">Interop</span></span>|<span data-ttu-id="b55cb-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-136">Optional attribute.</span></span> <span data-ttu-id="b55cb-137">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="b55cb-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b55cb-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b55cb-138">Interop</span></span>|<span data-ttu-id="b55cb-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b55cb-139">Optional attribute.</span></span> <span data-ttu-id="b55cb-140">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="b55cb-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="b55cb-141">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b55cb-141">All attributes</span></span>  
  
|<span data-ttu-id="b55cb-142">Değer</span><span class="sxs-lookup"><span data-stu-id="b55cb-142">Value</span></span>|<span data-ttu-id="b55cb-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b55cb-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b55cb-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b55cb-144">*policy_setting*</span></span>|<span data-ttu-id="b55cb-145">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="b55cb-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="b55cb-146">Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="b55cb-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b55cb-147">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b55cb-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b55cb-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b55cb-148">Child Elements</span></span>  
 <span data-ttu-id="b55cb-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="b55cb-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b55cb-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b55cb-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b55cb-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="b55cb-151">Element</span></span>|<span data-ttu-id="b55cb-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b55cb-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b55cb-153">\<türü ></span><span class="sxs-lookup"><span data-stu-id="b55cb-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="b55cb-154">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b55cb-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b55cb-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b55cb-155">Remarks</span></span>  
 <span data-ttu-id="b55cb-156">`<Subtypes>` Öğesi, kapsayan türündeki tüm subtypes ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b55cb-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="b55cb-157">Türetilmiş türler ve temel sınıflarının işaretçilerine farklı ilkeleri uygulamak istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="b55cb-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="b55cb-158">En az biri mevcut olmalıdır ancak yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b55cb-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b55cb-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="b55cb-159">Example</span></span>  
 <span data-ttu-id="b55cb-160">Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` ve adlı bir alt `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="b55cb-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="b55cb-161">Aşağıdaki kodda gösterildiği gibi açıkça dosya ayarlar çalışma zamanı yönergeleri `Dynamic` ve `Activate` ilkelerini `BaseClass` için `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="b55cb-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="b55cb-162">Bu, nesne türü nedeniyle `BaseClass` dinamik olarak ya da çağrıların ne kadar başlatılamaz `BaseClass` sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="b55cb-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="b55cb-163">Ancak, `<Subtypes>` öğesi öğelerinden türetilen sınıfları sağlar `BaseClass` dinamik olarak ve sınıf oluşturucuları yapılan çağrılar aracılığıyla oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="b55cb-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="b55cb-164">Nedeniyle `<Subtypes>` yönergesi, örneğini oluşturan aşağıdaki kodu bir `Derived1` çağırarak dinamik olarak örneği <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> başarıyla yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="b55cb-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="b55cb-165">Bu blok değişken bir <xref:System.Windows.Controls.TextBlock> boş bir Windows Store uygulaması nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b55cb-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b55cb-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b55cb-166">See also</span></span>

- [<span data-ttu-id="b55cb-167">\<Türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="b55cb-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="b55cb-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b55cb-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b55cb-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="b55cb-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="b55cb-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="b55cb-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

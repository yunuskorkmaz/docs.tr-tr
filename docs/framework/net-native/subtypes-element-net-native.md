---
title: "&lt;Subtypes&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9609027d31e757af93f6a4401a784a68a53cfdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsubtypesgt-element-net-native"></a><span data-ttu-id="6a93d-102">&lt;Subtypes&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="6a93d-102">&lt;Subtypes&gt; Element (.NET Native)</span></span>
<span data-ttu-id="6a93d-103">Çalışma zamanı ilkesi içeren türünden devralınan tüm sınıflar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6a93d-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a93d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a93d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a93d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a93d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6a93d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a93d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a93d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a93d-107">Attributes</span></span>  
  
|<span data-ttu-id="6a93d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a93d-108">Attribute</span></span>|<span data-ttu-id="6a93d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="6a93d-109">Attribute type</span></span>|<span data-ttu-id="6a93d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a93d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="6a93d-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6a93d-111">Reflection</span></span>|<span data-ttu-id="6a93d-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-112">Optional attribute.</span></span> <span data-ttu-id="6a93d-113">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6a93d-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6a93d-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6a93d-114">Reflection</span></span>|<span data-ttu-id="6a93d-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-115">Optional attribute.</span></span> <span data-ttu-id="6a93d-116">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6a93d-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6a93d-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6a93d-117">Reflection</span></span>|<span data-ttu-id="6a93d-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-118">Optional attribute.</span></span> <span data-ttu-id="6a93d-119">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6a93d-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6a93d-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a93d-120">Serialization</span></span>|<span data-ttu-id="6a93d-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-121">Optional attribute.</span></span> <span data-ttu-id="6a93d-122">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="6a93d-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6a93d-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a93d-123">Serialization</span></span>|<span data-ttu-id="6a93d-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-124">Optional attribute.</span></span> <span data-ttu-id="6a93d-125">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a93d-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6a93d-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a93d-126">Serialization</span></span>|<span data-ttu-id="6a93d-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-127">Optional attribute.</span></span> <span data-ttu-id="6a93d-128">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a93d-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6a93d-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a93d-129">Serialization</span></span>|<span data-ttu-id="6a93d-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-130">Optional attribute.</span></span> <span data-ttu-id="6a93d-131">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a93d-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6a93d-132">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6a93d-132">Interop</span></span>|<span data-ttu-id="6a93d-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-133">Optional attribute.</span></span> <span data-ttu-id="6a93d-134">Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi</span><span class="sxs-lookup"><span data-stu-id="6a93d-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6a93d-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6a93d-135">Interop</span></span>|<span data-ttu-id="6a93d-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-136">Optional attribute.</span></span> <span data-ttu-id="6a93d-137">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="6a93d-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6a93d-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6a93d-138">Interop</span></span>|<span data-ttu-id="6a93d-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a93d-139">Optional attribute.</span></span> <span data-ttu-id="6a93d-140">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="6a93d-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="6a93d-141">Tüm öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="6a93d-141">All attributes</span></span>  
  
|<span data-ttu-id="6a93d-142">Değer</span><span class="sxs-lookup"><span data-stu-id="6a93d-142">Value</span></span>|<span data-ttu-id="6a93d-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a93d-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a93d-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6a93d-144">*policy_setting*</span></span>|<span data-ttu-id="6a93d-145">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="6a93d-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="6a93d-146">Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="6a93d-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6a93d-147">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6a93d-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a93d-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a93d-148">Child Elements</span></span>  
 <span data-ttu-id="6a93d-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a93d-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a93d-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a93d-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6a93d-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a93d-151">Element</span></span>|<span data-ttu-id="6a93d-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a93d-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a93d-153">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="6a93d-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6a93d-154">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6a93d-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a93d-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a93d-155">Remarks</span></span>  
 <span data-ttu-id="6a93d-156">`<Subtypes>` Öğesi türünü içeren tüm alt ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6a93d-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="6a93d-157">Türetilmiş türler ve temel sınıflarına farklı ilkeleri uygulamak istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a93d-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="6a93d-158">En az birinin mevcut olması gereken rağmen yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6a93d-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a93d-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a93d-159">Example</span></span>  
 <span data-ttu-id="6a93d-160">Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` ve adlı bir alt sınıfı `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="6a93d-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="6a93d-161">Aşağıdaki kodda gösterildiği gibi çalışma zamanı yönergeleri açıkça kümeleri dosya `Dynamic` ve `Activate` ilkelerini `BaseClass` için `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="6a93d-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="6a93d-162">Bu, nesne türü nedeniyle `BaseClass` dinamik olarak veya çağrıların ne kadar başlatılamaz `BaseClass` sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="6a93d-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="6a93d-163">Ancak, `<Subtypes>` öğesi türetilmiş sınıfları sağlar `BaseClass` dinamik olarak ve kendi sınıf oluşturucular çağrıları aracılığıyla örneğinin oluşturulması için.</span><span class="sxs-lookup"><span data-stu-id="6a93d-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="6a93d-164">Nedeniyle `<Subtypes>` yönergesi, başlatır aşağıdaki kod bir `Derived1` çağırarak dinamik olarak örneği <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> yöntemi başarıyla yürütür.</span><span class="sxs-lookup"><span data-stu-id="6a93d-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="6a93d-165">Burada bloğu değişkeni, bir <xref:System.Windows.Controls.TextBlock> boş bir Windows mağazası uygulaması nesne.</span><span class="sxs-lookup"><span data-stu-id="6a93d-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6a93d-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a93d-166">See Also</span></span>  
 [<span data-ttu-id="6a93d-167">\<Tür > öğesi</span><span class="sxs-lookup"><span data-stu-id="6a93d-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="6a93d-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6a93d-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="6a93d-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6a93d-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="6a93d-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="6a93d-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

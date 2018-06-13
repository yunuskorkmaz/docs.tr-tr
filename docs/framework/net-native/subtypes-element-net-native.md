---
title: '&lt;Subtypes&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f850ec24530dd9a7d80f826461cacd9c249dd0de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397994"
---
# <a name="ltsubtypesgt-element-net-native"></a><span data-ttu-id="25681-102">&lt;Subtypes&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="25681-102">&lt;Subtypes&gt; Element (.NET Native)</span></span>
<span data-ttu-id="25681-103">Çalışma zamanı ilkesi içeren türünden devralınan tüm sınıflar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25681-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25681-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25681-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25681-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25681-105">Attributes and Elements</span></span>  
 <span data-ttu-id="25681-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25681-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25681-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25681-107">Attributes</span></span>  
  
|<span data-ttu-id="25681-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="25681-108">Attribute</span></span>|<span data-ttu-id="25681-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="25681-109">Attribute type</span></span>|<span data-ttu-id="25681-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25681-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="25681-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="25681-111">Reflection</span></span>|<span data-ttu-id="25681-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-112">Optional attribute.</span></span> <span data-ttu-id="25681-113">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="25681-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="25681-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="25681-114">Reflection</span></span>|<span data-ttu-id="25681-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-115">Optional attribute.</span></span> <span data-ttu-id="25681-116">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="25681-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="25681-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="25681-117">Reflection</span></span>|<span data-ttu-id="25681-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-118">Optional attribute.</span></span> <span data-ttu-id="25681-119">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="25681-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="25681-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="25681-120">Serialization</span></span>|<span data-ttu-id="25681-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-121">Optional attribute.</span></span> <span data-ttu-id="25681-122">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="25681-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="25681-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="25681-123">Serialization</span></span>|<span data-ttu-id="25681-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-124">Optional attribute.</span></span> <span data-ttu-id="25681-125">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25681-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="25681-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="25681-126">Serialization</span></span>|<span data-ttu-id="25681-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-127">Optional attribute.</span></span> <span data-ttu-id="25681-128">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25681-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="25681-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="25681-129">Serialization</span></span>|<span data-ttu-id="25681-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-130">Optional attribute.</span></span> <span data-ttu-id="25681-131">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="25681-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="25681-132">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="25681-132">Interop</span></span>|<span data-ttu-id="25681-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-133">Optional attribute.</span></span> <span data-ttu-id="25681-134">Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi</span><span class="sxs-lookup"><span data-stu-id="25681-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="25681-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="25681-135">Interop</span></span>|<span data-ttu-id="25681-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-136">Optional attribute.</span></span> <span data-ttu-id="25681-137">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="25681-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="25681-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="25681-138">Interop</span></span>|<span data-ttu-id="25681-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25681-139">Optional attribute.</span></span> <span data-ttu-id="25681-140">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="25681-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="25681-141">Tüm öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="25681-141">All attributes</span></span>  
  
|<span data-ttu-id="25681-142">Değer</span><span class="sxs-lookup"><span data-stu-id="25681-142">Value</span></span>|<span data-ttu-id="25681-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25681-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="25681-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="25681-144">*policy_setting*</span></span>|<span data-ttu-id="25681-145">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="25681-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="25681-146">Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="25681-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="25681-147">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="25681-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25681-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25681-148">Child Elements</span></span>  
 <span data-ttu-id="25681-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="25681-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25681-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25681-150">Parent Elements</span></span>  
  
|<span data-ttu-id="25681-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="25681-151">Element</span></span>|<span data-ttu-id="25681-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25681-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25681-153">\<türü ></span><span class="sxs-lookup"><span data-stu-id="25681-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="25681-154">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25681-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25681-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25681-155">Remarks</span></span>  
 <span data-ttu-id="25681-156">`<Subtypes>` Öğesi türünü içeren tüm alt ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="25681-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="25681-157">Türetilmiş türler ve temel sınıflarına farklı ilkeleri uygulamak istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="25681-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="25681-158">En az birinin mevcut olması gereken rağmen yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="25681-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25681-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="25681-159">Example</span></span>  
 <span data-ttu-id="25681-160">Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` ve adlı bir alt sınıfı `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="25681-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="25681-161">Aşağıdaki kodda gösterildiği gibi çalışma zamanı yönergeleri açıkça kümeleri dosya `Dynamic` ve `Activate` ilkelerini `BaseClass` için `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="25681-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="25681-162">Bu, nesne türü nedeniyle `BaseClass` dinamik olarak veya çağrıların ne kadar başlatılamaz `BaseClass` sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="25681-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="25681-163">Ancak, `<Subtypes>` öğesi türetilmiş sınıfları sağlar `BaseClass` dinamik olarak ve kendi sınıf oluşturucular çağrıları aracılığıyla örneğinin oluşturulması için.</span><span class="sxs-lookup"><span data-stu-id="25681-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="25681-164">Nedeniyle `<Subtypes>` yönergesi, başlatır aşağıdaki kod bir `Derived1` çağırarak dinamik olarak örneği <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> yöntemi başarıyla yürütür.</span><span class="sxs-lookup"><span data-stu-id="25681-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="25681-165">Burada bloğu değişkeni, bir <xref:System.Windows.Controls.TextBlock> boş bir Windows mağazası uygulaması nesne.</span><span class="sxs-lookup"><span data-stu-id="25681-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="25681-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25681-166">See Also</span></span>  
 [<span data-ttu-id="25681-167">\<Tür > öğesi</span><span class="sxs-lookup"><span data-stu-id="25681-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="25681-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="25681-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="25681-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="25681-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="25681-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="25681-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

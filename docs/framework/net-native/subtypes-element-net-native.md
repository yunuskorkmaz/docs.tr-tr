---
title: <Subtypes>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180931"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="d51a8-102">\<Element> Alt Türleri (.NET Yerli)</span><span class="sxs-lookup"><span data-stu-id="d51a8-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="d51a8-103">İçerme türünden devralınan tüm sınıflara çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="d51a8-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d51a8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d51a8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d51a8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d51a8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d51a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d51a8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51a8-107">Attributes</span></span>  
  
|<span data-ttu-id="d51a8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d51a8-108">Attribute</span></span>|<span data-ttu-id="d51a8-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="d51a8-109">Attribute type</span></span>|<span data-ttu-id="d51a8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51a8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="d51a8-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d51a8-111">Reflection</span></span>|<span data-ttu-id="d51a8-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-112">Optional attribute.</span></span> <span data-ttu-id="d51a8-113">Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="d51a8-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d51a8-114">Reflection</span></span>|<span data-ttu-id="d51a8-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-115">Optional attribute.</span></span> <span data-ttu-id="d51a8-116">Program öğeleri hakkında bilgi için sorgu denetimleri, ancak herhangi bir çalışma zamanı erişim etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="d51a8-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="d51a8-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d51a8-117">Reflection</span></span>|<span data-ttu-id="d51a8-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-118">Optional attribute.</span></span> <span data-ttu-id="d51a8-119">Dinamik programlamayı etkinleştirmek için oluşturucular, yöntemler, alanlar, özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="d51a8-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d51a8-120">Serialization</span></span>|<span data-ttu-id="d51a8-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-121">Optional attribute.</span></span> <span data-ttu-id="d51a8-122">Newtonsoft JSON serileştiricisi gibi kitaplıklar tarafından seri hale getirilecek ve deserialized türü örnekleri etkinleştirmek için, yapıcılar, alanlar ve özelliklere çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="d51a8-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d51a8-123">Serialization</span></span>|<span data-ttu-id="d51a8-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-124">Optional attribute.</span></span> <span data-ttu-id="d51a8-125">Sınıfı kullanan serileştirme ilkesini <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="d51a8-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d51a8-126">Serialization</span></span>|<span data-ttu-id="d51a8-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-127">Optional attribute.</span></span> <span data-ttu-id="d51a8-128">Sınıfı kullanan JSON serileştirme <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="d51a8-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d51a8-129">Serialization</span></span>|<span data-ttu-id="d51a8-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-130">Optional attribute.</span></span> <span data-ttu-id="d51a8-131">Sınıfı kullanan XML serileştirme <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="d51a8-132">Interop</span><span class="sxs-lookup"><span data-stu-id="d51a8-132">Interop</span></span>|<span data-ttu-id="d51a8-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-133">Optional attribute.</span></span> <span data-ttu-id="d51a8-134">Başvuru türlerini Windows Runtime ve COM'a göre mareşalleme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="d51a8-135">Interop</span><span class="sxs-lookup"><span data-stu-id="d51a8-135">Interop</span></span>|<span data-ttu-id="d51a8-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-136">Optional attribute.</span></span> <span data-ttu-id="d51a8-137">Temsilci türlerini işlev işaretçisi olarak yerel koda göre işaretetmek için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="d51a8-138">Interop</span><span class="sxs-lookup"><span data-stu-id="d51a8-138">Interop</span></span>|<span data-ttu-id="d51a8-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51a8-139">Optional attribute.</span></span> <span data-ttu-id="d51a8-140">Değer türlerini yerel koda göre mareşalleştirmek için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="d51a8-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="d51a8-141">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51a8-141">All attributes</span></span>  
  
|<span data-ttu-id="d51a8-142">Değer</span><span class="sxs-lookup"><span data-stu-id="d51a8-142">Value</span></span>|<span data-ttu-id="d51a8-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51a8-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d51a8-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d51a8-144">*policy_setting*</span></span>|<span data-ttu-id="d51a8-145">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="d51a8-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="d51a8-146">Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="d51a8-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="d51a8-147">Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d51a8-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d51a8-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d51a8-148">Child Elements</span></span>  
 <span data-ttu-id="d51a8-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="d51a8-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d51a8-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d51a8-150">Parent Elements</span></span>  
  
|<span data-ttu-id="d51a8-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="d51a8-151">Element</span></span>|<span data-ttu-id="d51a8-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51a8-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d51a8-153">\<Tip></span><span class="sxs-lookup"><span data-stu-id="d51a8-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="d51a8-154">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="d51a8-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d51a8-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d51a8-155">Remarks</span></span>  
 <span data-ttu-id="d51a8-156">Öğe, `<Subtypes>` içerdiği türünün tüm alt türlerine ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="d51a8-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="d51a8-157">Türemiş türlere ve bunların temel sınıflarına farklı ilkeler uygulamak istediğinizde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d51a8-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="d51a8-158">Yansıma, serileştirme ve interop öznitelikleri isteğe bağlıdır, ancak en az birinin bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51a8-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d51a8-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="d51a8-159">Example</span></span>  
 <span data-ttu-id="d51a8-160">Aşağıdaki örnek, adlı `BaseClass` bir sınıf ve `Derived1`bir alt sınıf adlı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d51a8-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="d51a8-161">Aşağıdaki kodda gösterildiği gibi, çalışma zamanı yönergeleri dosyası `Dynamic` `Activate` açıkça ayarlar `BaseClass` `Excluded`ve ilkeleri için .</span><span class="sxs-lookup"><span data-stu-id="d51a8-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="d51a8-162">Bu nedenle, tür `BaseClass` nesneleri dinamik olarak veya `BaseClass` sınıf oluşturucuya yapılan çağrılarla anında alınamaz.</span><span class="sxs-lookup"><span data-stu-id="d51a8-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="d51a8-163">Ancak, `<Subtypes>` öğe, türetilen `BaseClass` sınıfların dinamik olarak anında ve sınıf yapıcılarına yapılan çağrılar yoluyla oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d51a8-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="d51a8-164">`<Subtypes>` Yönerge nedeniyle, <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> yöntemi çağırarak bir `Derived1` örneği dinamik olarak anında sağlayan aşağıdaki kod başarılı bir şekilde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d51a8-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="d51a8-165">Buradaki blok değişkeni <xref:System.Windows.Controls.TextBlock> boş bir Windows Mağazası uygulamasındaki bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="d51a8-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d51a8-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d51a8-166">See also</span></span>

- [<span data-ttu-id="d51a8-167">\<> Öğesi Yazın</span><span class="sxs-lookup"><span data-stu-id="d51a8-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="d51a8-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d51a8-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="d51a8-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="d51a8-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="d51a8-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="d51a8-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

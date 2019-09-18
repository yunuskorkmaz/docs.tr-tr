---
title: <Subtypes>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af1acc02b18c5b97ef66ccae9b70c1f5327bff4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049121"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="b0b96-102">\<Alt türler > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b0b96-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="b0b96-103">Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.</span><span class="sxs-lookup"><span data-stu-id="b0b96-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0b96-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0b96-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0b96-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b0b96-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0b96-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0b96-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0b96-107">Attributes</span></span>  
  
|<span data-ttu-id="b0b96-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0b96-108">Attribute</span></span>|<span data-ttu-id="b0b96-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="b0b96-109">Attribute type</span></span>|<span data-ttu-id="b0b96-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0b96-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="b0b96-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b0b96-111">Reflection</span></span>|<span data-ttu-id="b0b96-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-112">Optional attribute.</span></span> <span data-ttu-id="b0b96-113">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b0b96-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b0b96-114">Reflection</span></span>|<span data-ttu-id="b0b96-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-115">Optional attribute.</span></span> <span data-ttu-id="b0b96-116">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="b0b96-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b0b96-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="b0b96-117">Reflection</span></span>|<span data-ttu-id="b0b96-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-118">Optional attribute.</span></span> <span data-ttu-id="b0b96-119">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b0b96-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b0b96-120">Serialization</span></span>|<span data-ttu-id="b0b96-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-121">Optional attribute.</span></span> <span data-ttu-id="b0b96-122">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b0b96-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b0b96-123">Serialization</span></span>|<span data-ttu-id="b0b96-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-124">Optional attribute.</span></span> <span data-ttu-id="b0b96-125"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b0b96-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b0b96-126">Serialization</span></span>|<span data-ttu-id="b0b96-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-127">Optional attribute.</span></span> <span data-ttu-id="b0b96-128"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b0b96-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b0b96-129">Serialization</span></span>|<span data-ttu-id="b0b96-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-130">Optional attribute.</span></span> <span data-ttu-id="b0b96-131"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b0b96-132">Interop</span><span class="sxs-lookup"><span data-stu-id="b0b96-132">Interop</span></span>|<span data-ttu-id="b0b96-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-133">Optional attribute.</span></span> <span data-ttu-id="b0b96-134">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b0b96-135">Interop</span><span class="sxs-lookup"><span data-stu-id="b0b96-135">Interop</span></span>|<span data-ttu-id="b0b96-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-136">Optional attribute.</span></span> <span data-ttu-id="b0b96-137">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b0b96-138">Interop</span><span class="sxs-lookup"><span data-stu-id="b0b96-138">Interop</span></span>|<span data-ttu-id="b0b96-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b0b96-139">Optional attribute.</span></span> <span data-ttu-id="b0b96-140">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="b0b96-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="b0b96-141">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0b96-141">All attributes</span></span>  
  
|<span data-ttu-id="b0b96-142">Değer</span><span class="sxs-lookup"><span data-stu-id="b0b96-142">Value</span></span>|<span data-ttu-id="b0b96-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0b96-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0b96-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b0b96-144">*policy_setting*</span></span>|<span data-ttu-id="b0b96-145">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="b0b96-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="b0b96-146">Olası değerler şunlardır `All` `Auto` ,,`Excluded`,,,, ve`Required All`. `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="b0b96-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b0b96-147">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b0b96-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0b96-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0b96-148">Child Elements</span></span>  
 <span data-ttu-id="b0b96-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0b96-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0b96-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0b96-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b0b96-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0b96-151">Element</span></span>|<span data-ttu-id="b0b96-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0b96-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0b96-153">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="b0b96-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="b0b96-154">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="b0b96-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0b96-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0b96-155">Remarks</span></span>  
 <span data-ttu-id="b0b96-156">`<Subtypes>` Öğesi, ilkeyi kapsayan türünün tüm alt türlerine uygular.</span><span class="sxs-lookup"><span data-stu-id="b0b96-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="b0b96-157">Türetilmiş türlere ve bunların temel sınıflarına farklı ilkeler uygulamak istediğinizde bunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b0b96-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="b0b96-158">Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır, ancak en az bir tane bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0b96-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0b96-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0b96-159">Example</span></span>  
 <span data-ttu-id="b0b96-160">Aşağıdaki örnek adlı bir sınıfı `BaseClass` ve adlı bir `Derived1`alt sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0b96-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="b0b96-161">Aşağıdaki kodda gösterildiği gibi, çalışma zamanı yönergeleri dosyası `Dynamic` için ve `Activate` ilkelerini `BaseClass` `Excluded`açıkça ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b0b96-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="b0b96-162">Bu nedenle, türündeki `BaseClass` nesneler dinamik olarak veya `BaseClass` sınıf oluşturucusuna çağrılar tarafından başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="b0b96-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="b0b96-163">Ancak `<Subtypes>` öğesi, öğesinden `BaseClass` türetilmiş sınıfların dinamik olarak ve sınıf oluşturucularının çağrıları aracılığıyla oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0b96-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="b0b96-164">Yönergesi nedeniyle, <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> yöntemi çağırarak bir örneği dinamik olarak örnekleyen `Derived1` aşağıdaki kod, başarılı bir şekilde yürütülür. `<Subtypes>`</span><span class="sxs-lookup"><span data-stu-id="b0b96-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="b0b96-165">Burada blok değişkeni, boş bir <xref:System.Windows.Controls.TextBlock> Windows Mağazası uygulamasındaki bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="b0b96-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b0b96-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0b96-166">See also</span></span>

- [<span data-ttu-id="b0b96-167">\<> Öğesi yazın</span><span class="sxs-lookup"><span data-stu-id="b0b96-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="b0b96-168">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b0b96-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b0b96-169">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="b0b96-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="b0b96-170">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="b0b96-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

---
title: <AttributeImplies>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181059"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="f4806-102">\<Öznitelik> Öğe (.NET Yerli) Anlamına Gelir</span><span class="sxs-lookup"><span data-stu-id="f4806-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="f4806-103">İçerdeki öznitelik uygulanan kod öğeleri için ilke tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4806-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4806-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4806-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4806-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4806-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f4806-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4806-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4806-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4806-107">Attributes</span></span>  
  
|<span data-ttu-id="f4806-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f4806-108">Attribute</span></span>|<span data-ttu-id="f4806-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="f4806-109">Attribute type</span></span>|<span data-ttu-id="f4806-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4806-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="f4806-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="f4806-111">Reflection</span></span>|<span data-ttu-id="f4806-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-112">Optional attribute.</span></span> <span data-ttu-id="f4806-113">Örneklerin etkinleştirilmesini etkinleştirmek için çalışan zamanında kuruculara erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="f4806-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="f4806-114">Reflection</span></span>|<span data-ttu-id="f4806-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-115">Optional attribute.</span></span> <span data-ttu-id="f4806-116">Program öğeleri hakkında bilgi için sorgu denetimleri, ancak herhangi bir çalışma zamanı erişim etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f4806-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="f4806-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="f4806-117">Reflection</span></span>|<span data-ttu-id="f4806-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-118">Optional attribute.</span></span> <span data-ttu-id="f4806-119">Dinamik programlamayı etkinleştirmek için oluşturucular, yöntemler, alanlar, özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="f4806-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f4806-120">Serialization</span></span>|<span data-ttu-id="f4806-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-121">Optional attribute.</span></span> <span data-ttu-id="f4806-122">Newtonsoft JSON serileştiricisi gibi kitaplıklar tarafından seri hale getirilecek ve deserialized türü örnekleri etkinleştirmek için, yapıcılar, alanlar ve özelliklere çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="f4806-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f4806-123">Serialization</span></span>|<span data-ttu-id="f4806-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-124">Optional attribute.</span></span> <span data-ttu-id="f4806-125">Sınıfı kullanan serileştirme ilkesini <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="f4806-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f4806-126">Serialization</span></span>|<span data-ttu-id="f4806-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-127">Optional attribute.</span></span> <span data-ttu-id="f4806-128">Sınıfı kullanan JSON serileştirme <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="f4806-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f4806-129">Serialization</span></span>|<span data-ttu-id="f4806-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-130">Optional attribute.</span></span> <span data-ttu-id="f4806-131">Sınıfı kullanan XML serileştirme <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="f4806-132">Interop</span><span class="sxs-lookup"><span data-stu-id="f4806-132">Interop</span></span>|<span data-ttu-id="f4806-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-133">Optional attribute.</span></span> <span data-ttu-id="f4806-134">Başvuru türlerini Windows Runtime ve COM'a göre mareşalleme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="f4806-135">Interop</span><span class="sxs-lookup"><span data-stu-id="f4806-135">Interop</span></span>|<span data-ttu-id="f4806-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-136">Optional attribute.</span></span> <span data-ttu-id="f4806-137">Temsilci türlerini işlev işaretçisi olarak yerel koda göre işaretetmek için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="f4806-138">Interop</span><span class="sxs-lookup"><span data-stu-id="f4806-138">Interop</span></span>|<span data-ttu-id="f4806-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f4806-139">Optional attribute.</span></span> <span data-ttu-id="f4806-140">Değer türlerini yerel koda göre mareşalleştirmek için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="f4806-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="f4806-141">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4806-141">All attributes</span></span>  
  
|<span data-ttu-id="f4806-142">Değer</span><span class="sxs-lookup"><span data-stu-id="f4806-142">Value</span></span>|<span data-ttu-id="f4806-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4806-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4806-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f4806-144">*policy_setting*</span></span>|<span data-ttu-id="f4806-145">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="f4806-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="f4806-146">Olası değerler `All` `Auto`, `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="f4806-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="f4806-147">Daha fazla bilgi için [Runtime Yönergesi İlke Ayarları'na](runtime-directive-policy-settings.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f4806-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4806-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4806-148">Child Elements</span></span>  
 <span data-ttu-id="f4806-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4806-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4806-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4806-150">Parent Elements</span></span>  
  
|<span data-ttu-id="f4806-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="f4806-151">Element</span></span>|<span data-ttu-id="f4806-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4806-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4806-153">\<Tip></span><span class="sxs-lookup"><span data-stu-id="f4806-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="f4806-154">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="f4806-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4806-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4806-155">Remarks</span></span>  
 <span data-ttu-id="f4806-156">Öğe `<AttributeImplies>` türü bir öznitelik (yani, bir sınıf türetilmiş) <xref:System.Attribute?displayProperty=nameWithType>ise öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4806-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="f4806-157">Öznitelik belirli bir program öğesine uygulanırsa, `<AttributeImplies>` öğe tarafından tanımlanan ilke bu program öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f4806-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="f4806-158">Yansıma, serileştirme ve interop öznitelikleri isteğe bağlıdır, ancak en az birinin bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4806-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4806-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4806-159">See also</span></span>

- [<span data-ttu-id="f4806-160">\<> Öğesi Yazın</span><span class="sxs-lookup"><span data-stu-id="f4806-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="f4806-161">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f4806-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="f4806-162">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="f4806-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="f4806-163">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="f4806-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

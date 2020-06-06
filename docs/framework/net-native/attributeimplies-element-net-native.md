---
title: <AttributeImplies>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
ms.openlocfilehash: 2ab1fdc71bc43f61f69a0d9b7bea7acb35e14ea5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181059"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="62a19-102">\<AttributeImplies>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="62a19-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="62a19-103">İçerilen özniteliğin uygulandığı kod öğeleri için ilkeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62a19-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62a19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62a19-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62a19-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62a19-105">Attributes and Elements</span></span>  
 <span data-ttu-id="62a19-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62a19-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62a19-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62a19-107">Attributes</span></span>  
  
|<span data-ttu-id="62a19-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62a19-108">Attribute</span></span>|<span data-ttu-id="62a19-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="62a19-109">Attribute type</span></span>|<span data-ttu-id="62a19-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62a19-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="62a19-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="62a19-111">Reflection</span></span>|<span data-ttu-id="62a19-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-112">Optional attribute.</span></span> <span data-ttu-id="62a19-113">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="62a19-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="62a19-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="62a19-114">Reflection</span></span>|<span data-ttu-id="62a19-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-115">Optional attribute.</span></span> <span data-ttu-id="62a19-116">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="62a19-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="62a19-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="62a19-117">Reflection</span></span>|<span data-ttu-id="62a19-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-118">Optional attribute.</span></span> <span data-ttu-id="62a19-119">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="62a19-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="62a19-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="62a19-120">Serialization</span></span>|<span data-ttu-id="62a19-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-121">Optional attribute.</span></span> <span data-ttu-id="62a19-122">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="62a19-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="62a19-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="62a19-123">Serialization</span></span>|<span data-ttu-id="62a19-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-124">Optional attribute.</span></span> <span data-ttu-id="62a19-125">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="62a19-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="62a19-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="62a19-126">Serialization</span></span>|<span data-ttu-id="62a19-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-127">Optional attribute.</span></span> <span data-ttu-id="62a19-128">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="62a19-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="62a19-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="62a19-129">Serialization</span></span>|<span data-ttu-id="62a19-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-130">Optional attribute.</span></span> <span data-ttu-id="62a19-131">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="62a19-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="62a19-132">Interop</span><span class="sxs-lookup"><span data-stu-id="62a19-132">Interop</span></span>|<span data-ttu-id="62a19-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-133">Optional attribute.</span></span> <span data-ttu-id="62a19-134">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="62a19-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="62a19-135">Interop</span><span class="sxs-lookup"><span data-stu-id="62a19-135">Interop</span></span>|<span data-ttu-id="62a19-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-136">Optional attribute.</span></span> <span data-ttu-id="62a19-137">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="62a19-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="62a19-138">Interop</span><span class="sxs-lookup"><span data-stu-id="62a19-138">Interop</span></span>|<span data-ttu-id="62a19-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="62a19-139">Optional attribute.</span></span> <span data-ttu-id="62a19-140">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="62a19-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="62a19-141">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62a19-141">All attributes</span></span>  
  
|<span data-ttu-id="62a19-142">Değer</span><span class="sxs-lookup"><span data-stu-id="62a19-142">Value</span></span>|<span data-ttu-id="62a19-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62a19-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62a19-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="62a19-144">*policy_setting*</span></span>|<span data-ttu-id="62a19-145">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="62a19-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="62a19-146">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="62a19-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="62a19-147">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="62a19-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62a19-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62a19-148">Child Elements</span></span>  
 <span data-ttu-id="62a19-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="62a19-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62a19-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62a19-150">Parent Elements</span></span>  
  
|<span data-ttu-id="62a19-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="62a19-151">Element</span></span>|<span data-ttu-id="62a19-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62a19-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="62a19-153">Yansıma ilkesini bir türe ve tüm üyelerine uygular.</span><span class="sxs-lookup"><span data-stu-id="62a19-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62a19-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62a19-154">Remarks</span></span>  
 <span data-ttu-id="62a19-155">`<AttributeImplies>`Öğesi, kapsayan türü bir öznitelik (diğer bir deyişle, öğesinden türetilmiş bir sınıf) ise kullanılır <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="62a19-155">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="62a19-156">Özniteliği belirli bir program öğesine uygulanırsa, öğesi tarafından tanımlanan ilke `<AttributeImplies>` Bu program öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="62a19-156">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="62a19-157">Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır, ancak en az bir tane bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62a19-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a19-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62a19-158">See also</span></span>

- [<span data-ttu-id="62a19-159">\<Type>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="62a19-159">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="62a19-160">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="62a19-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="62a19-161">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="62a19-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="62a19-162">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="62a19-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)

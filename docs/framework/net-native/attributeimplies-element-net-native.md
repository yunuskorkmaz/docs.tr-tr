---
title: <AttributeImplies> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be5412e323b1c4930d7e17d09faa174885611884
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254983"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="53e46-102">\<Attributeımplies > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="53e46-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="53e46-103">Kod öğeleri içeren öznitelik uygulandığı ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="53e46-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53e46-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53e46-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="53e46-105">Attributes and Elements</span></span>  
 <span data-ttu-id="53e46-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53e46-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53e46-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="53e46-107">Attributes</span></span>  
  
|<span data-ttu-id="53e46-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="53e46-108">Attribute</span></span>|<span data-ttu-id="53e46-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="53e46-109">Attribute type</span></span>|<span data-ttu-id="53e46-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53e46-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="53e46-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="53e46-111">Reflection</span></span>|<span data-ttu-id="53e46-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-112">Optional attribute.</span></span> <span data-ttu-id="53e46-113">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="53e46-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="53e46-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="53e46-114">Reflection</span></span>|<span data-ttu-id="53e46-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-115">Optional attribute.</span></span> <span data-ttu-id="53e46-116">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="53e46-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="53e46-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="53e46-117">Reflection</span></span>|<span data-ttu-id="53e46-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-118">Optional attribute.</span></span> <span data-ttu-id="53e46-119">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="53e46-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="53e46-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="53e46-120">Serialization</span></span>|<span data-ttu-id="53e46-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-121">Optional attribute.</span></span> <span data-ttu-id="53e46-122">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="53e46-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="53e46-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="53e46-123">Serialization</span></span>|<span data-ttu-id="53e46-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-124">Optional attribute.</span></span> <span data-ttu-id="53e46-125">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e46-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="53e46-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="53e46-126">Serialization</span></span>|<span data-ttu-id="53e46-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-127">Optional attribute.</span></span> <span data-ttu-id="53e46-128">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e46-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="53e46-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="53e46-129">Serialization</span></span>|<span data-ttu-id="53e46-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-130">Optional attribute.</span></span> <span data-ttu-id="53e46-131">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53e46-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="53e46-132">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="53e46-132">Interop</span></span>|<span data-ttu-id="53e46-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-133">Optional attribute.</span></span> <span data-ttu-id="53e46-134">Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi</span><span class="sxs-lookup"><span data-stu-id="53e46-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="53e46-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="53e46-135">Interop</span></span>|<span data-ttu-id="53e46-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-136">Optional attribute.</span></span> <span data-ttu-id="53e46-137">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="53e46-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="53e46-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="53e46-138">Interop</span></span>|<span data-ttu-id="53e46-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53e46-139">Optional attribute.</span></span> <span data-ttu-id="53e46-140">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="53e46-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="53e46-141">Tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="53e46-141">All attributes</span></span>  
  
|<span data-ttu-id="53e46-142">Değer</span><span class="sxs-lookup"><span data-stu-id="53e46-142">Value</span></span>|<span data-ttu-id="53e46-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53e46-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="53e46-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="53e46-144">*policy_setting*</span></span>|<span data-ttu-id="53e46-145">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="53e46-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="53e46-146">Olası değerler `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="53e46-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="53e46-147">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="53e46-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53e46-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="53e46-148">Child Elements</span></span>  
 <span data-ttu-id="53e46-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="53e46-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53e46-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="53e46-150">Parent Elements</span></span>  
  
|<span data-ttu-id="53e46-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="53e46-151">Element</span></span>|<span data-ttu-id="53e46-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53e46-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53e46-153">\<türü ></span><span class="sxs-lookup"><span data-stu-id="53e46-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="53e46-154">Yansıma İlkesi, bir tür ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="53e46-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e46-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53e46-155">Remarks</span></span>  
 <span data-ttu-id="53e46-156">`<AttributeImplies>` Öğe türünü içeren bir öznitelik varsa kullanılır (öğesinden türetilmiş bir sınıf <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="53e46-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="53e46-157">Öznitelik belirli program öğesine uygulanırsa, ilke tarafından tanımlanan `<AttributeImplies>` öğesi bu program öğesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="53e46-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="53e46-158">En az biri mevcut olmalıdır ancak yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="53e46-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e46-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53e46-159">See also</span></span>
- [<span data-ttu-id="53e46-160">\<Türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="53e46-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="53e46-161">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="53e46-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="53e46-162">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="53e46-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="53e46-163">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="53e46-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

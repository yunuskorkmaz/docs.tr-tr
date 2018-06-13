---
title: '&lt;AttributeImplies&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 960ee5716b9760ab82628a8d21728cd6675e5215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395446"
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="6cdb3-102">&lt;AttributeImplies&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="6cdb3-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="6cdb3-103">İçeren öznitelik uygulandığı kod öğeleri için ilke tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdb3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cdb3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cdb3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6cdb3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6cdb3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cdb3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6cdb3-107">Attributes</span></span>  
  
|<span data-ttu-id="6cdb3-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6cdb3-108">Attribute</span></span>|<span data-ttu-id="6cdb3-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="6cdb3-109">Attribute type</span></span>|<span data-ttu-id="6cdb3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cdb3-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="6cdb3-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6cdb3-111">Reflection</span></span>|<span data-ttu-id="6cdb3-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-112">Optional attribute.</span></span> <span data-ttu-id="6cdb3-113">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6cdb3-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6cdb3-114">Reflection</span></span>|<span data-ttu-id="6cdb3-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-115">Optional attribute.</span></span> <span data-ttu-id="6cdb3-116">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6cdb3-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6cdb3-117">Reflection</span></span>|<span data-ttu-id="6cdb3-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-118">Optional attribute.</span></span> <span data-ttu-id="6cdb3-119">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6cdb3-120">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6cdb3-120">Serialization</span></span>|<span data-ttu-id="6cdb3-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-121">Optional attribute.</span></span> <span data-ttu-id="6cdb3-122">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6cdb3-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6cdb3-123">Serialization</span></span>|<span data-ttu-id="6cdb3-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-124">Optional attribute.</span></span> <span data-ttu-id="6cdb3-125">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6cdb3-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6cdb3-126">Serialization</span></span>|<span data-ttu-id="6cdb3-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-127">Optional attribute.</span></span> <span data-ttu-id="6cdb3-128">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6cdb3-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6cdb3-129">Serialization</span></span>|<span data-ttu-id="6cdb3-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-130">Optional attribute.</span></span> <span data-ttu-id="6cdb3-131">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6cdb3-132">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6cdb3-132">Interop</span></span>|<span data-ttu-id="6cdb3-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-133">Optional attribute.</span></span> <span data-ttu-id="6cdb3-134">Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi</span><span class="sxs-lookup"><span data-stu-id="6cdb3-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6cdb3-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6cdb3-135">Interop</span></span>|<span data-ttu-id="6cdb3-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-136">Optional attribute.</span></span> <span data-ttu-id="6cdb3-137">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6cdb3-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6cdb3-138">Interop</span></span>|<span data-ttu-id="6cdb3-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-139">Optional attribute.</span></span> <span data-ttu-id="6cdb3-140">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="6cdb3-141">Tüm öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="6cdb3-141">All attributes</span></span>  
  
|<span data-ttu-id="6cdb3-142">Değer</span><span class="sxs-lookup"><span data-stu-id="6cdb3-142">Value</span></span>|<span data-ttu-id="6cdb3-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cdb3-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cdb3-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6cdb3-144">*policy_setting*</span></span>|<span data-ttu-id="6cdb3-145">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="6cdb3-146">Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6cdb3-147">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6cdb3-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cdb3-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6cdb3-148">Child Elements</span></span>  
 <span data-ttu-id="6cdb3-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cdb3-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6cdb3-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6cdb3-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="6cdb3-151">Element</span></span>|<span data-ttu-id="6cdb3-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cdb3-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cdb3-153">\<türü ></span><span class="sxs-lookup"><span data-stu-id="6cdb3-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6cdb3-154">Yansıma ilke türü ve tüm üyeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cdb3-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cdb3-155">Remarks</span></span>  
 <span data-ttu-id="6cdb3-156">`<AttributeImplies>` Öğe türünü içeren bir öznitelik varsa kullanılır (öğesinden türetilmiş bir sınıf <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="6cdb3-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="6cdb3-157">Belirli bir program öğesi için öznitelik uyguladıysanız, ilke tarafından tanımlanan `<AttributeImplies>` öğesi, bir program öğesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="6cdb3-158">En az birinin mevcut olması gereken rağmen yansıma, seri hale getirme ve birlikte çalışma özniteliklerini tüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdb3-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cdb3-159">See Also</span></span>  
 [<span data-ttu-id="6cdb3-160">\<Tür > öğesi</span><span class="sxs-lookup"><span data-stu-id="6cdb3-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="6cdb3-161">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6cdb3-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="6cdb3-162">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6cdb3-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="6cdb3-163">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="6cdb3-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

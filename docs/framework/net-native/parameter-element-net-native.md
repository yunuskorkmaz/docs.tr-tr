---
title: <Parameter> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c18919a6c48c251138a3d5e88079d3383979ef1a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266409"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="e7cf5-102">\<Parametresi > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="e7cf5-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="e7cf5-103">Bir yönteme geçirilen bağımsız değişken türünü yansıma ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7cf5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7cf5-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7cf5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7cf5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e7cf5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7cf5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7cf5-107">Attributes</span></span>  
  
|<span data-ttu-id="e7cf5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7cf5-108">Attribute</span></span>|<span data-ttu-id="e7cf5-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="e7cf5-109">Attribute type</span></span>|<span data-ttu-id="e7cf5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7cf5-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e7cf5-111">Genel</span><span class="sxs-lookup"><span data-stu-id="e7cf5-111">General</span></span>|<span data-ttu-id="e7cf5-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-112">Required attribute.</span></span> <span data-ttu-id="e7cf5-113">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-113">The parameter name.</span></span> <span data-ttu-id="e7cf5-114">Örneğin, yöntem imzası için `String.CompareTo(Object value)`, değerini `Name` özniteliktir "value".</span><span class="sxs-lookup"><span data-stu-id="e7cf5-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="e7cf5-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e7cf5-115">Reflection</span></span>|<span data-ttu-id="e7cf5-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-116">Optional attribute.</span></span> <span data-ttu-id="e7cf5-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="e7cf5-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e7cf5-118">Reflection</span></span>|<span data-ttu-id="e7cf5-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-119">Optional attribute.</span></span> <span data-ttu-id="e7cf5-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="e7cf5-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e7cf5-121">Reflection</span></span>|<span data-ttu-id="e7cf5-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-122">Optional attribute.</span></span> <span data-ttu-id="e7cf5-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="e7cf5-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e7cf5-124">Serialization</span></span>|<span data-ttu-id="e7cf5-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-125">Optional attribute.</span></span> <span data-ttu-id="e7cf5-126">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="e7cf5-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e7cf5-127">Serialization</span></span>|<span data-ttu-id="e7cf5-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-128">Optional attribute.</span></span> <span data-ttu-id="e7cf5-129">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="e7cf5-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e7cf5-130">Serialization</span></span>|<span data-ttu-id="e7cf5-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-131">Optional attribute.</span></span> <span data-ttu-id="e7cf5-132">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="e7cf5-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e7cf5-133">Serialization</span></span>|<span data-ttu-id="e7cf5-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-134">Optional attribute.</span></span> <span data-ttu-id="e7cf5-135">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="e7cf5-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="e7cf5-136">Interop</span></span>|<span data-ttu-id="e7cf5-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-137">Optional attribute.</span></span> <span data-ttu-id="e7cf5-138">Denetim İlkesi WinRT ve COM başvuru türlerini hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7cf5-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="e7cf5-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="e7cf5-139">Interop</span></span>|<span data-ttu-id="e7cf5-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-140">Optional attribute.</span></span> <span data-ttu-id="e7cf5-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="e7cf5-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="e7cf5-142">Interop</span></span>|<span data-ttu-id="e7cf5-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-143">Optional attribute.</span></span> <span data-ttu-id="e7cf5-144">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e7cf5-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="e7cf5-145">Name attribute</span></span>  
  
|<span data-ttu-id="e7cf5-146">Değer</span><span class="sxs-lookup"><span data-stu-id="e7cf5-146">Value</span></span>|<span data-ttu-id="e7cf5-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7cf5-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e7cf5-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="e7cf5-148">*parameter_name*</span></span>|<span data-ttu-id="e7cf5-149">İlke uygulandığı yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="e7cf5-150">Örneğin, yöntem imzası için `String.CompareTo(Object value)`, değerini `Name` özniteliktir "value".</span><span class="sxs-lookup"><span data-stu-id="e7cf5-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e7cf5-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7cf5-151">All other attributes</span></span>  
  
|<span data-ttu-id="e7cf5-152">Değer</span><span class="sxs-lookup"><span data-stu-id="e7cf5-152">Value</span></span>|<span data-ttu-id="e7cf5-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7cf5-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e7cf5-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e7cf5-154">*policy_setting*</span></span>|<span data-ttu-id="e7cf5-155">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="e7cf5-156">Olası değerler `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e7cf5-157">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e7cf5-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7cf5-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7cf5-158">Child Elements</span></span>  
 <span data-ttu-id="e7cf5-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7cf5-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7cf5-160">Parent Elements</span></span>  
  
|<span data-ttu-id="e7cf5-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7cf5-161">Element</span></span>|<span data-ttu-id="e7cf5-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7cf5-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7cf5-163">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="e7cf5-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="e7cf5-164">Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7cf5-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7cf5-165">Remarks</span></span>  
 <span data-ttu-id="e7cf5-166">`<Parameter>` Öğesi alt öğesi olan [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) öğesi ve belirli bir yöntem parametresine ilkeyi uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="e7cf5-167">Belirli bir yöntem parametre adı yerine türüne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="e7cf5-168">Bir ilke türü gibi temsil eden en az bir öznitelik `Activate` veya `Dynamic`, mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cf5-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7cf5-169">See also</span></span>
- [<span data-ttu-id="e7cf5-170">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="e7cf5-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="e7cf5-171">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e7cf5-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e7cf5-172">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="e7cf5-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="e7cf5-173">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="e7cf5-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

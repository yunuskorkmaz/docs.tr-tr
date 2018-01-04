---
title: "&lt;Parameter&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 820c36abda104bbf748e5b3a7838f3c7715048e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt-element-net-native"></a><span data-ttu-id="8166b-102">&lt;Parameter&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="8166b-102">&lt;Parameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="8166b-103">Bir yönteme geçirilen bağımsız değişken türü yansıma ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8166b-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8166b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8166b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8166b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8166b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8166b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8166b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8166b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8166b-107">Attributes</span></span>  
  
|<span data-ttu-id="8166b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8166b-108">Attribute</span></span>|<span data-ttu-id="8166b-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="8166b-109">Attribute type</span></span>|<span data-ttu-id="8166b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8166b-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8166b-111">Genel</span><span class="sxs-lookup"><span data-stu-id="8166b-111">General</span></span>|<span data-ttu-id="8166b-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-112">Required attribute.</span></span> <span data-ttu-id="8166b-113">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="8166b-113">The parameter name.</span></span> <span data-ttu-id="8166b-114">Örneğin, yöntem imzası `String.CompareTo(Object value)`, değeri `Name` "value" bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="8166b-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="8166b-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8166b-115">Reflection</span></span>|<span data-ttu-id="8166b-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-116">Optional attribute.</span></span> <span data-ttu-id="8166b-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8166b-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8166b-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8166b-118">Reflection</span></span>|<span data-ttu-id="8166b-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-119">Optional attribute.</span></span> <span data-ttu-id="8166b-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8166b-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8166b-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8166b-121">Reflection</span></span>|<span data-ttu-id="8166b-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-122">Optional attribute.</span></span> <span data-ttu-id="8166b-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8166b-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8166b-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8166b-124">Serialization</span></span>|<span data-ttu-id="8166b-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-125">Optional attribute.</span></span> <span data-ttu-id="8166b-126">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="8166b-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8166b-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8166b-127">Serialization</span></span>|<span data-ttu-id="8166b-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-128">Optional attribute.</span></span> <span data-ttu-id="8166b-129">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8166b-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8166b-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8166b-130">Serialization</span></span>|<span data-ttu-id="8166b-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-131">Optional attribute.</span></span> <span data-ttu-id="8166b-132">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8166b-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8166b-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8166b-133">Serialization</span></span>|<span data-ttu-id="8166b-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-134">Optional attribute.</span></span> <span data-ttu-id="8166b-135">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8166b-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8166b-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8166b-136">Interop</span></span>|<span data-ttu-id="8166b-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-137">Optional attribute.</span></span> <span data-ttu-id="8166b-138">Başvuru türleri WinRT ve COM hazırlama için ilke denetler</span><span class="sxs-lookup"><span data-stu-id="8166b-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8166b-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8166b-139">Interop</span></span>|<span data-ttu-id="8166b-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-140">Optional attribute.</span></span> <span data-ttu-id="8166b-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="8166b-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8166b-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8166b-142">Interop</span></span>|<span data-ttu-id="8166b-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8166b-143">Optional attribute.</span></span> <span data-ttu-id="8166b-144">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="8166b-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8166b-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="8166b-145">Name attribute</span></span>  
  
|<span data-ttu-id="8166b-146">Değer</span><span class="sxs-lookup"><span data-stu-id="8166b-146">Value</span></span>|<span data-ttu-id="8166b-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8166b-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8166b-148">*parametre_adý*</span><span class="sxs-lookup"><span data-stu-id="8166b-148">*parameter_name*</span></span>|<span data-ttu-id="8166b-149">İlkesinin uygulandığı yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="8166b-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="8166b-150">Örneğin, yöntem imzası `String.CompareTo(Object value)`, değeri `Name` "value" bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="8166b-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8166b-151">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="8166b-151">All other attributes</span></span>  
  
|<span data-ttu-id="8166b-152">Değer</span><span class="sxs-lookup"><span data-stu-id="8166b-152">Value</span></span>|<span data-ttu-id="8166b-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8166b-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8166b-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8166b-154">*policy_setting*</span></span>|<span data-ttu-id="8166b-155">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="8166b-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="8166b-156">Olası değerler şunlardır: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="8166b-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8166b-157">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8166b-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8166b-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8166b-158">Child Elements</span></span>  
 <span data-ttu-id="8166b-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="8166b-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8166b-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8166b-160">Parent Elements</span></span>  
  
|<span data-ttu-id="8166b-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="8166b-161">Element</span></span>|<span data-ttu-id="8166b-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8166b-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8166b-163">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="8166b-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="8166b-164">Çalışma zamanı yansıma ilke oluşturucunun ya da yöntemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8166b-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8166b-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8166b-165">Remarks</span></span>  
 <span data-ttu-id="8166b-166">`<Parameter>` Bir alt öğedir [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) öğesi ve belirli yöntem parametresi ilkeyi uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8166b-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="8166b-167">Belirli yöntem parametresi adı yerine türüne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8166b-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="8166b-168">Bir ilke türü gibi temsil eden en az bir öznitelik `Activate` veya `Dynamic`, mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8166b-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8166b-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8166b-169">See Also</span></span>  
 [<span data-ttu-id="8166b-170">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="8166b-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="8166b-171">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8166b-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="8166b-172">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="8166b-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="8166b-173">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="8166b-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

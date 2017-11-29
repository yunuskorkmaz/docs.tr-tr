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
ms.openlocfilehash: f603f795682c7ea1f48e5d9356af6e0477246da1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparametergt-element-net-native"></a><span data-ttu-id="fae04-102">&lt;Parameter&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="fae04-102">&lt;Parameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="fae04-103">Bir yönteme geçirilen bağımsız değişken türü yansıma ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fae04-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fae04-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fae04-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fae04-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fae04-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fae04-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fae04-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fae04-107">Attributes</span></span>  
  
|<span data-ttu-id="fae04-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fae04-108">Attribute</span></span>|<span data-ttu-id="fae04-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="fae04-109">Attribute type</span></span>|<span data-ttu-id="fae04-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fae04-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="fae04-111">Genel</span><span class="sxs-lookup"><span data-stu-id="fae04-111">General</span></span>|<span data-ttu-id="fae04-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-112">Required attribute.</span></span> <span data-ttu-id="fae04-113">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="fae04-113">The parameter name.</span></span> <span data-ttu-id="fae04-114">Örneğin, yöntem imzası `String.CompareTo(Object value)`, değeri `Name` "value" bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="fae04-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="fae04-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="fae04-115">Reflection</span></span>|<span data-ttu-id="fae04-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-116">Optional attribute.</span></span> <span data-ttu-id="fae04-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="fae04-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="fae04-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="fae04-118">Reflection</span></span>|<span data-ttu-id="fae04-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-119">Optional attribute.</span></span> <span data-ttu-id="fae04-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fae04-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="fae04-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="fae04-121">Reflection</span></span>|<span data-ttu-id="fae04-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-122">Optional attribute.</span></span> <span data-ttu-id="fae04-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="fae04-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="fae04-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="fae04-124">Serialization</span></span>|<span data-ttu-id="fae04-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-125">Optional attribute.</span></span> <span data-ttu-id="fae04-126">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="fae04-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="fae04-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="fae04-127">Serialization</span></span>|<span data-ttu-id="fae04-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-128">Optional attribute.</span></span> <span data-ttu-id="fae04-129">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fae04-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="fae04-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="fae04-130">Serialization</span></span>|<span data-ttu-id="fae04-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-131">Optional attribute.</span></span> <span data-ttu-id="fae04-132">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fae04-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="fae04-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="fae04-133">Serialization</span></span>|<span data-ttu-id="fae04-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-134">Optional attribute.</span></span> <span data-ttu-id="fae04-135">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fae04-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="fae04-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="fae04-136">Interop</span></span>|<span data-ttu-id="fae04-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-137">Optional attribute.</span></span> <span data-ttu-id="fae04-138">Başvuru türleri WinRT ve COM hazırlama için ilke denetler</span><span class="sxs-lookup"><span data-stu-id="fae04-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="fae04-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="fae04-139">Interop</span></span>|<span data-ttu-id="fae04-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-140">Optional attribute.</span></span> <span data-ttu-id="fae04-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="fae04-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="fae04-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="fae04-142">Interop</span></span>|<span data-ttu-id="fae04-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fae04-143">Optional attribute.</span></span> <span data-ttu-id="fae04-144">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="fae04-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="fae04-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="fae04-145">Name attribute</span></span>  
  
|<span data-ttu-id="fae04-146">Değer</span><span class="sxs-lookup"><span data-stu-id="fae04-146">Value</span></span>|<span data-ttu-id="fae04-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fae04-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fae04-148">*parametre_adý*</span><span class="sxs-lookup"><span data-stu-id="fae04-148">*parameter_name*</span></span>|<span data-ttu-id="fae04-149">İlkesinin uygulandığı yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="fae04-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="fae04-150">Örneğin, yöntem imzası `String.CompareTo(Object value)`, değeri `Name` "value" bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="fae04-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="fae04-151">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="fae04-151">All other attributes</span></span>  
  
|<span data-ttu-id="fae04-152">Değer</span><span class="sxs-lookup"><span data-stu-id="fae04-152">Value</span></span>|<span data-ttu-id="fae04-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fae04-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fae04-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="fae04-154">*policy_setting*</span></span>|<span data-ttu-id="fae04-155">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="fae04-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="fae04-156">Olası değerler şunlardır: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="fae04-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="fae04-157">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="fae04-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fae04-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fae04-158">Child Elements</span></span>  
 <span data-ttu-id="fae04-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="fae04-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fae04-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fae04-160">Parent Elements</span></span>  
  
|<span data-ttu-id="fae04-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="fae04-161">Element</span></span>|<span data-ttu-id="fae04-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fae04-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fae04-163">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="fae04-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="fae04-164">Çalışma zamanı yansıma ilke oluşturucunun ya da yöntemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fae04-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fae04-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fae04-165">Remarks</span></span>  
 <span data-ttu-id="fae04-166">`<Parameter>` Bir alt öğedir [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) öğesi ve belirli yöntem parametresi ilkeyi uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fae04-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="fae04-167">Belirli yöntem parametresi adı yerine türüne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fae04-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="fae04-168">Bir ilke türü gibi temsil eden en az bir öznitelik `Activate` veya `Dynamic`, mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fae04-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae04-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fae04-169">See Also</span></span>  
 [<span data-ttu-id="fae04-170">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="fae04-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="fae04-171">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="fae04-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="fae04-172">Çalışma zamanı yönerge İlkesi ayarları</span><span class="sxs-lookup"><span data-stu-id="fae04-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="fae04-173">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="fae04-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

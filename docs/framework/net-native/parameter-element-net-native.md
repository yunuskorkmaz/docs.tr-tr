---
description: 'Daha fazla bilgi edinin: <Parameter> öğesi (.NET Native)'
title: <Parameter> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: 53b84027e8393e0a799d9652767d173c2787cd27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662799"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="9e42f-103">\<Parameter> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="9e42f-103">\<Parameter> Element (.NET Native)</span></span>

<span data-ttu-id="9e42f-104">Bir yönteme geçirilen bağımsız değişkenin türüne yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="9e42f-104">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e42f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e42f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e42f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e42f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9e42f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e42f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e42f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e42f-108">Attributes</span></span>  
  
|<span data-ttu-id="9e42f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9e42f-109">Attribute</span></span>|<span data-ttu-id="9e42f-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="9e42f-110">Attribute type</span></span>|<span data-ttu-id="9e42f-111">Description</span><span class="sxs-lookup"><span data-stu-id="9e42f-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9e42f-112">Genel</span><span class="sxs-lookup"><span data-stu-id="9e42f-112">General</span></span>|<span data-ttu-id="9e42f-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-113">Required attribute.</span></span> <span data-ttu-id="9e42f-114">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="9e42f-114">The parameter name.</span></span> <span data-ttu-id="9e42f-115">Örneğin, yöntem imzası için `String.CompareTo(Object value)` , `Name` özniteliği değeri "Value" olur.</span><span class="sxs-lookup"><span data-stu-id="9e42f-115">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="9e42f-116">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9e42f-116">Reflection</span></span>|<span data-ttu-id="9e42f-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-117">Optional attribute.</span></span> <span data-ttu-id="9e42f-118">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e42f-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="9e42f-119">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9e42f-119">Reflection</span></span>|<span data-ttu-id="9e42f-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-120">Optional attribute.</span></span> <span data-ttu-id="9e42f-121">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="9e42f-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="9e42f-122">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9e42f-122">Reflection</span></span>|<span data-ttu-id="9e42f-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-123">Optional attribute.</span></span> <span data-ttu-id="9e42f-124">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e42f-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="9e42f-125">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9e42f-125">Serialization</span></span>|<span data-ttu-id="9e42f-126">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-126">Optional attribute.</span></span> <span data-ttu-id="9e42f-127">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e42f-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="9e42f-128">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9e42f-128">Serialization</span></span>|<span data-ttu-id="9e42f-129">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-129">Optional attribute.</span></span> <span data-ttu-id="9e42f-130">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9e42f-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="9e42f-131">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9e42f-131">Serialization</span></span>|<span data-ttu-id="9e42f-132">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-132">Optional attribute.</span></span> <span data-ttu-id="9e42f-133">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9e42f-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="9e42f-134">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="9e42f-134">Serialization</span></span>|<span data-ttu-id="9e42f-135">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-135">Optional attribute.</span></span> <span data-ttu-id="9e42f-136">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9e42f-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="9e42f-137">Interop</span><span class="sxs-lookup"><span data-stu-id="9e42f-137">Interop</span></span>|<span data-ttu-id="9e42f-138">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-138">Optional attribute.</span></span> <span data-ttu-id="9e42f-139">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e42f-139">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="9e42f-140">Interop</span><span class="sxs-lookup"><span data-stu-id="9e42f-140">Interop</span></span>|<span data-ttu-id="9e42f-141">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-141">Optional attribute.</span></span> <span data-ttu-id="9e42f-142">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e42f-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="9e42f-143">Interop</span><span class="sxs-lookup"><span data-stu-id="9e42f-143">Interop</span></span>|<span data-ttu-id="9e42f-144">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9e42f-144">Optional attribute.</span></span> <span data-ttu-id="9e42f-145">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="9e42f-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9e42f-146">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="9e42f-146">Name attribute</span></span>  
  
|<span data-ttu-id="9e42f-147">Değer</span><span class="sxs-lookup"><span data-stu-id="9e42f-147">Value</span></span>|<span data-ttu-id="9e42f-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e42f-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9e42f-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="9e42f-149">*parameter_name*</span></span>|<span data-ttu-id="9e42f-150">İlkenin uygulandığı Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="9e42f-150">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="9e42f-151">Örneğin, yöntem imzası için `String.CompareTo(Object value)` , `Name` özniteliği değeri "Value" olur.</span><span class="sxs-lookup"><span data-stu-id="9e42f-151">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9e42f-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e42f-152">All other attributes</span></span>  
  
|<span data-ttu-id="9e42f-153">Değer</span><span class="sxs-lookup"><span data-stu-id="9e42f-153">Value</span></span>|<span data-ttu-id="9e42f-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e42f-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9e42f-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9e42f-155">*policy_setting*</span></span>|<span data-ttu-id="9e42f-156">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="9e42f-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="9e42f-157">Olası değerler şunlardır,,,, `All` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="9e42f-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="9e42f-158">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9e42f-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e42f-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e42f-159">Child Elements</span></span>  

 <span data-ttu-id="9e42f-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="9e42f-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e42f-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e42f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="9e42f-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e42f-162">Element</span></span>|<span data-ttu-id="9e42f-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e42f-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="9e42f-164">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="9e42f-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e42f-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e42f-165">Remarks</span></span>  

 <span data-ttu-id="9e42f-166">`<Parameter>`Öğesi öğesinin bir alt öğesidir [\<Method>](method-element-net-native.md) ve belirli bir yöntem parametresine ilke uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e42f-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="9e42f-167">Belirli yöntem parametresi, türüne göre değil, adıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9e42f-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="9e42f-168">Veya gibi bir ilke türünü temsil eden en az bir özniteliğin `Activate` mevcut olması `Dynamic` gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e42f-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e42f-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e42f-169">See also</span></span>

- [<span data-ttu-id="9e42f-170">\<Method> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="9e42f-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="9e42f-171">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e42f-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9e42f-172">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="9e42f-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="9e42f-173">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="9e42f-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

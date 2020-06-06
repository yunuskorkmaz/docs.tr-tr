---
title: <Parameter>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: c6dfc347d44a794ee8496c45ca879f9daab12b22
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128192"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="19b4b-102">\<Parameter>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="19b4b-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="19b4b-103">Bir yönteme geçirilen bağımsız değişkenin türüne yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="19b4b-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19b4b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19b4b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19b4b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="19b4b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19b4b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19b4b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19b4b-107">Attributes</span></span>  
  
|<span data-ttu-id="19b4b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19b4b-108">Attribute</span></span>|<span data-ttu-id="19b4b-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="19b4b-109">Attribute type</span></span>|<span data-ttu-id="19b4b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19b4b-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="19b4b-111">Genel</span><span class="sxs-lookup"><span data-stu-id="19b4b-111">General</span></span>|<span data-ttu-id="19b4b-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-112">Required attribute.</span></span> <span data-ttu-id="19b4b-113">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="19b4b-113">The parameter name.</span></span> <span data-ttu-id="19b4b-114">Örneğin, yöntem imzası için `String.CompareTo(Object value)` , `Name` özniteliği değeri "Value" olur.</span><span class="sxs-lookup"><span data-stu-id="19b4b-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="19b4b-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="19b4b-115">Reflection</span></span>|<span data-ttu-id="19b4b-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-116">Optional attribute.</span></span> <span data-ttu-id="19b4b-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="19b4b-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="19b4b-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="19b4b-118">Reflection</span></span>|<span data-ttu-id="19b4b-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-119">Optional attribute.</span></span> <span data-ttu-id="19b4b-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="19b4b-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="19b4b-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="19b4b-121">Reflection</span></span>|<span data-ttu-id="19b4b-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-122">Optional attribute.</span></span> <span data-ttu-id="19b4b-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="19b4b-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="19b4b-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="19b4b-124">Serialization</span></span>|<span data-ttu-id="19b4b-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-125">Optional attribute.</span></span> <span data-ttu-id="19b4b-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="19b4b-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="19b4b-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="19b4b-127">Serialization</span></span>|<span data-ttu-id="19b4b-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-128">Optional attribute.</span></span> <span data-ttu-id="19b4b-129">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="19b4b-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="19b4b-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="19b4b-130">Serialization</span></span>|<span data-ttu-id="19b4b-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-131">Optional attribute.</span></span> <span data-ttu-id="19b4b-132">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="19b4b-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="19b4b-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="19b4b-133">Serialization</span></span>|<span data-ttu-id="19b4b-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-134">Optional attribute.</span></span> <span data-ttu-id="19b4b-135">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="19b4b-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="19b4b-136">Interop</span><span class="sxs-lookup"><span data-stu-id="19b4b-136">Interop</span></span>|<span data-ttu-id="19b4b-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-137">Optional attribute.</span></span> <span data-ttu-id="19b4b-138">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="19b4b-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="19b4b-139">Interop</span><span class="sxs-lookup"><span data-stu-id="19b4b-139">Interop</span></span>|<span data-ttu-id="19b4b-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-140">Optional attribute.</span></span> <span data-ttu-id="19b4b-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="19b4b-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="19b4b-142">Interop</span><span class="sxs-lookup"><span data-stu-id="19b4b-142">Interop</span></span>|<span data-ttu-id="19b4b-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="19b4b-143">Optional attribute.</span></span> <span data-ttu-id="19b4b-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="19b4b-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="19b4b-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="19b4b-145">Name attribute</span></span>  
  
|<span data-ttu-id="19b4b-146">Değer</span><span class="sxs-lookup"><span data-stu-id="19b4b-146">Value</span></span>|<span data-ttu-id="19b4b-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19b4b-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19b4b-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="19b4b-148">*parameter_name*</span></span>|<span data-ttu-id="19b4b-149">İlkenin uygulandığı Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="19b4b-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="19b4b-150">Örneğin, yöntem imzası için `String.CompareTo(Object value)` , `Name` özniteliği değeri "Value" olur.</span><span class="sxs-lookup"><span data-stu-id="19b4b-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="19b4b-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19b4b-151">All other attributes</span></span>  
  
|<span data-ttu-id="19b4b-152">Değer</span><span class="sxs-lookup"><span data-stu-id="19b4b-152">Value</span></span>|<span data-ttu-id="19b4b-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19b4b-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19b4b-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="19b4b-154">*policy_setting*</span></span>|<span data-ttu-id="19b4b-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="19b4b-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="19b4b-156">Olası değerler şunlardır,,,, `All` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="19b4b-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="19b4b-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="19b4b-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19b4b-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19b4b-158">Child Elements</span></span>  
 <span data-ttu-id="19b4b-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="19b4b-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19b4b-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19b4b-160">Parent Elements</span></span>  
  
|<span data-ttu-id="19b4b-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="19b4b-161">Element</span></span>|<span data-ttu-id="19b4b-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19b4b-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="19b4b-163">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="19b4b-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19b4b-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19b4b-164">Remarks</span></span>  
 <span data-ttu-id="19b4b-165">`<Parameter>`Öğesi öğesinin bir alt öğesidir [\<Method>](method-element-net-native.md) ve belirli bir yöntem parametresine ilke uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19b4b-165">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="19b4b-166">Belirli yöntem parametresi, türüne göre değil, adıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="19b4b-166">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="19b4b-167">Veya gibi bir ilke türünü temsil eden en az bir özniteliğin `Activate` mevcut olması `Dynamic` gerekir.</span><span class="sxs-lookup"><span data-stu-id="19b4b-167">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b4b-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19b4b-168">See also</span></span>

- [<span data-ttu-id="19b4b-169">\<Method>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="19b4b-169">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="19b4b-170">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="19b4b-170">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="19b4b-171">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="19b4b-171">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="19b4b-172">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="19b4b-172">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

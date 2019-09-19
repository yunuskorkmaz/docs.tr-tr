---
title: <Parameter>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c9a462e75df535504d0e98c22c34c11ff7af7d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049342"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="07529-102">\<Parameter > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="07529-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="07529-103">Bir yönteme geçirilen bağımsız değişkenin türüne yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="07529-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07529-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07529-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07529-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="07529-105">Attributes and Elements</span></span>  
 <span data-ttu-id="07529-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07529-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07529-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07529-107">Attributes</span></span>  
  
|<span data-ttu-id="07529-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07529-108">Attribute</span></span>|<span data-ttu-id="07529-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="07529-109">Attribute type</span></span>|<span data-ttu-id="07529-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07529-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="07529-111">Genel</span><span class="sxs-lookup"><span data-stu-id="07529-111">General</span></span>|<span data-ttu-id="07529-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-112">Required attribute.</span></span> <span data-ttu-id="07529-113">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="07529-113">The parameter name.</span></span> <span data-ttu-id="07529-114">Örneğin, yöntem imzası `String.CompareTo(Object value)`için, `Name` özniteliği değeri "Value" olur.</span><span class="sxs-lookup"><span data-stu-id="07529-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="07529-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="07529-115">Reflection</span></span>|<span data-ttu-id="07529-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-116">Optional attribute.</span></span> <span data-ttu-id="07529-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="07529-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="07529-118">Reflection</span></span>|<span data-ttu-id="07529-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-119">Optional attribute.</span></span> <span data-ttu-id="07529-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="07529-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="07529-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="07529-121">Reflection</span></span>|<span data-ttu-id="07529-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-122">Optional attribute.</span></span> <span data-ttu-id="07529-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="07529-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07529-124">Serialization</span></span>|<span data-ttu-id="07529-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-125">Optional attribute.</span></span> <span data-ttu-id="07529-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="07529-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07529-127">Serialization</span></span>|<span data-ttu-id="07529-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-128">Optional attribute.</span></span> <span data-ttu-id="07529-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="07529-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07529-130">Serialization</span></span>|<span data-ttu-id="07529-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-131">Optional attribute.</span></span> <span data-ttu-id="07529-132"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> Sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="07529-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07529-133">Serialization</span></span>|<span data-ttu-id="07529-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-134">Optional attribute.</span></span> <span data-ttu-id="07529-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> Sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="07529-136">Interop</span><span class="sxs-lookup"><span data-stu-id="07529-136">Interop</span></span>|<span data-ttu-id="07529-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-137">Optional attribute.</span></span> <span data-ttu-id="07529-138">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="07529-139">Interop</span><span class="sxs-lookup"><span data-stu-id="07529-139">Interop</span></span>|<span data-ttu-id="07529-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-140">Optional attribute.</span></span> <span data-ttu-id="07529-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="07529-142">Interop</span><span class="sxs-lookup"><span data-stu-id="07529-142">Interop</span></span>|<span data-ttu-id="07529-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07529-143">Optional attribute.</span></span> <span data-ttu-id="07529-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="07529-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="07529-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="07529-145">Name attribute</span></span>  
  
|<span data-ttu-id="07529-146">Değer</span><span class="sxs-lookup"><span data-stu-id="07529-146">Value</span></span>|<span data-ttu-id="07529-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07529-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07529-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="07529-148">*parameter_name*</span></span>|<span data-ttu-id="07529-149">İlkenin uygulandığı Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="07529-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="07529-150">Örneğin, yöntem imzası `String.CompareTo(Object value)`için, `Name` özniteliği değeri "Value" olur.</span><span class="sxs-lookup"><span data-stu-id="07529-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="07529-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07529-151">All other attributes</span></span>  
  
|<span data-ttu-id="07529-152">Değer</span><span class="sxs-lookup"><span data-stu-id="07529-152">Value</span></span>|<span data-ttu-id="07529-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07529-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07529-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="07529-154">*policy_setting*</span></span>|<span data-ttu-id="07529-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="07529-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="07529-156">Olası değerler şunlardır `All` `Public` ,,`PublicAndInternal`,, ve .`Required All` `Required Public` `Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="07529-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="07529-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="07529-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07529-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="07529-158">Child Elements</span></span>  
 <span data-ttu-id="07529-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="07529-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07529-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="07529-160">Parent Elements</span></span>  
  
|<span data-ttu-id="07529-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="07529-161">Element</span></span>|<span data-ttu-id="07529-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07529-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07529-163">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="07529-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="07529-164">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="07529-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07529-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07529-165">Remarks</span></span>  
 <span data-ttu-id="07529-166">Öğesi, metot > öğesinin bir alt [ \<](method-element-net-native.md) öğesidir ve ilkeyi belirli bir yöntem `<Parameter>` parametresine uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07529-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="07529-167">Belirli yöntem parametresi, türüne göre değil, adıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="07529-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="07529-168">`Activate` Veya`Dynamic`gibi bir ilke türünü temsil eden en az bir özniteliğin mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="07529-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07529-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07529-169">See also</span></span>

- [<span data-ttu-id="07529-170">\<Metot > öğesi</span><span class="sxs-lookup"><span data-stu-id="07529-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="07529-171">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="07529-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="07529-172">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="07529-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="07529-173">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="07529-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

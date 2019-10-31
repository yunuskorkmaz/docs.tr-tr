---
title: <Parameter> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: c6dfc347d44a794ee8496c45ca879f9daab12b22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128192"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="e86f0-102">\<parametre > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e86f0-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="e86f0-103">Bir yönteme geçirilen bağımsız değişkenin türüne yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="e86f0-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e86f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e86f0-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e86f0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e86f0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e86f0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e86f0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e86f0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e86f0-107">Attributes</span></span>  
  
|<span data-ttu-id="e86f0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e86f0-108">Attribute</span></span>|<span data-ttu-id="e86f0-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="e86f0-109">Attribute type</span></span>|<span data-ttu-id="e86f0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e86f0-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e86f0-111">Genel</span><span class="sxs-lookup"><span data-stu-id="e86f0-111">General</span></span>|<span data-ttu-id="e86f0-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-112">Required attribute.</span></span> <span data-ttu-id="e86f0-113">Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="e86f0-113">The parameter name.</span></span> <span data-ttu-id="e86f0-114">Örneğin, yöntem imzası `String.CompareTo(Object value)`için `Name` özniteliğinin değeri "Value" değeridir.</span><span class="sxs-lookup"><span data-stu-id="e86f0-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="e86f0-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e86f0-115">Reflection</span></span>|<span data-ttu-id="e86f0-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-116">Optional attribute.</span></span> <span data-ttu-id="e86f0-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="e86f0-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e86f0-118">Reflection</span></span>|<span data-ttu-id="e86f0-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-119">Optional attribute.</span></span> <span data-ttu-id="e86f0-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="e86f0-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="e86f0-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e86f0-121">Reflection</span></span>|<span data-ttu-id="e86f0-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-122">Optional attribute.</span></span> <span data-ttu-id="e86f0-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="e86f0-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e86f0-124">Serialization</span></span>|<span data-ttu-id="e86f0-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-125">Optional attribute.</span></span> <span data-ttu-id="e86f0-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="e86f0-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e86f0-127">Serialization</span></span>|<span data-ttu-id="e86f0-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-128">Optional attribute.</span></span> <span data-ttu-id="e86f0-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="e86f0-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e86f0-130">Serialization</span></span>|<span data-ttu-id="e86f0-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-131">Optional attribute.</span></span> <span data-ttu-id="e86f0-132"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="e86f0-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e86f0-133">Serialization</span></span>|<span data-ttu-id="e86f0-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-134">Optional attribute.</span></span> <span data-ttu-id="e86f0-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="e86f0-136">Interop</span><span class="sxs-lookup"><span data-stu-id="e86f0-136">Interop</span></span>|<span data-ttu-id="e86f0-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-137">Optional attribute.</span></span> <span data-ttu-id="e86f0-138">WinRT ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="e86f0-139">Interop</span><span class="sxs-lookup"><span data-stu-id="e86f0-139">Interop</span></span>|<span data-ttu-id="e86f0-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-140">Optional attribute.</span></span> <span data-ttu-id="e86f0-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="e86f0-142">Interop</span><span class="sxs-lookup"><span data-stu-id="e86f0-142">Interop</span></span>|<span data-ttu-id="e86f0-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e86f0-143">Optional attribute.</span></span> <span data-ttu-id="e86f0-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e86f0-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e86f0-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="e86f0-145">Name attribute</span></span>  
  
|<span data-ttu-id="e86f0-146">Değer</span><span class="sxs-lookup"><span data-stu-id="e86f0-146">Value</span></span>|<span data-ttu-id="e86f0-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e86f0-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e86f0-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="e86f0-148">*parameter_name*</span></span>|<span data-ttu-id="e86f0-149">İlkenin uygulandığı Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="e86f0-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="e86f0-150">Örneğin, yöntem imzası `String.CompareTo(Object value)`için `Name` özniteliğinin değeri "Value" değeridir.</span><span class="sxs-lookup"><span data-stu-id="e86f0-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e86f0-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e86f0-151">All other attributes</span></span>  
  
|<span data-ttu-id="e86f0-152">Değer</span><span class="sxs-lookup"><span data-stu-id="e86f0-152">Value</span></span>|<span data-ttu-id="e86f0-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e86f0-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e86f0-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e86f0-154">*policy_setting*</span></span>|<span data-ttu-id="e86f0-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="e86f0-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="e86f0-156">Olası değerler şunlardır `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="e86f0-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e86f0-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e86f0-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e86f0-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e86f0-158">Child Elements</span></span>  
 <span data-ttu-id="e86f0-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="e86f0-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e86f0-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e86f0-160">Parent Elements</span></span>  
  
|<span data-ttu-id="e86f0-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="e86f0-161">Element</span></span>|<span data-ttu-id="e86f0-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e86f0-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e86f0-163">\<yöntemi ></span><span class="sxs-lookup"><span data-stu-id="e86f0-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="e86f0-164">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="e86f0-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e86f0-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e86f0-165">Remarks</span></span>  
 <span data-ttu-id="e86f0-166">`<Parameter>` öğesi [\<yöntemi >](method-element-net-native.md) öğesinin bir alt öğesidir ve belirli bir yöntem parametresine ilke uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e86f0-166">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="e86f0-167">Belirli yöntem parametresi, türüne göre değil, adıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e86f0-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="e86f0-168">`Activate` veya `Dynamic`gibi bir ilke türünü temsil eden en az bir öznitelik mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e86f0-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e86f0-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e86f0-169">See also</span></span>

- [<span data-ttu-id="e86f0-170">\<yöntemi > öğesi</span><span class="sxs-lookup"><span data-stu-id="e86f0-170">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="e86f0-171">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e86f0-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e86f0-172">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="e86f0-172">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="e86f0-173">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="e86f0-173">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

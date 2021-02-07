---
description: 'Daha fazla bilgi edinin: <GenericParameter> öğesi (.NET Native)'
title: <GenericParameter> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: 57cbb3418289d7da4f25577188299acd55ce6c94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747835"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="a355b-103">\<GenericParameter> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a355b-103">\<GenericParameter> Element (.NET Native)</span></span>

<span data-ttu-id="a355b-104">İlkeyi genel bir türün veya yöntemin parametre türüne uygular.</span><span class="sxs-lookup"><span data-stu-id="a355b-104">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a355b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a355b-105">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a355b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a355b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a355b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a355b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a355b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a355b-108">Attributes</span></span>  
  
|<span data-ttu-id="a355b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a355b-109">Attribute</span></span>|<span data-ttu-id="a355b-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="a355b-110">Attribute type</span></span>|<span data-ttu-id="a355b-111">Description</span><span class="sxs-lookup"><span data-stu-id="a355b-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="a355b-112">Genel</span><span class="sxs-lookup"><span data-stu-id="a355b-112">General</span></span>|<span data-ttu-id="a355b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-113">Required attribute.</span></span> <span data-ttu-id="a355b-114">Genel parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="a355b-114">The name of the generic parameter.</span></span> <span data-ttu-id="a355b-115">Örneğin, genel temsilci için <xref:System.Func%603> , `Name` çalışma zamanı ilkesini temsilcinin dönüş değerine uygulamak için özniteliğinin değeri "TResult" olur.</span><span class="sxs-lookup"><span data-stu-id="a355b-115">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="a355b-116">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a355b-116">Reflection</span></span>|<span data-ttu-id="a355b-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-117">Optional attribute.</span></span> <span data-ttu-id="a355b-118">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="a355b-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="a355b-119">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a355b-119">Reflection</span></span>|<span data-ttu-id="a355b-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-120">Optional attribute.</span></span> <span data-ttu-id="a355b-121">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="a355b-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="a355b-122">Yansıma</span><span class="sxs-lookup"><span data-stu-id="a355b-122">Reflection</span></span>|<span data-ttu-id="a355b-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-123">Optional attribute.</span></span> <span data-ttu-id="a355b-124">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="a355b-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="a355b-125">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a355b-125">Serialization</span></span>|<span data-ttu-id="a355b-126">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-126">Optional attribute.</span></span> <span data-ttu-id="a355b-127">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="a355b-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="a355b-128">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a355b-128">Serialization</span></span>|<span data-ttu-id="a355b-129">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-129">Optional attribute.</span></span> <span data-ttu-id="a355b-130">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a355b-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="a355b-131">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a355b-131">Serialization</span></span>|<span data-ttu-id="a355b-132">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-132">Optional attribute.</span></span> <span data-ttu-id="a355b-133">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a355b-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="a355b-134">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a355b-134">Serialization</span></span>|<span data-ttu-id="a355b-135">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-135">Optional attribute.</span></span> <span data-ttu-id="a355b-136">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a355b-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="a355b-137">Interop</span><span class="sxs-lookup"><span data-stu-id="a355b-137">Interop</span></span>|<span data-ttu-id="a355b-138">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-138">Optional attribute.</span></span> <span data-ttu-id="a355b-139">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="a355b-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="a355b-140">Interop</span><span class="sxs-lookup"><span data-stu-id="a355b-140">Interop</span></span>|<span data-ttu-id="a355b-141">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-141">Optional attribute.</span></span> <span data-ttu-id="a355b-142">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="a355b-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="a355b-143">Interop</span><span class="sxs-lookup"><span data-stu-id="a355b-143">Interop</span></span>|<span data-ttu-id="a355b-144">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-144">Optional attribute.</span></span> <span data-ttu-id="a355b-145">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="a355b-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a355b-146">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="a355b-146">Name attribute</span></span>  
  
|<span data-ttu-id="a355b-147">Değer</span><span class="sxs-lookup"><span data-stu-id="a355b-147">Value</span></span>|<span data-ttu-id="a355b-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a355b-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a355b-149">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="a355b-149">*generic_parameter_name*</span></span>|<span data-ttu-id="a355b-150">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a355b-150">Required attribute.</span></span> <span data-ttu-id="a355b-151">Genel tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="a355b-151">The name of the generic type parameter.</span></span> <span data-ttu-id="a355b-152">Örneğin, genel temsilci için <xref:System.Func%603> , "TResult" *generic_parameter_name* değeri, temsilcinin dönüş değerine çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="a355b-152">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="a355b-153">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a355b-153">All other attributes</span></span>  
  
|<span data-ttu-id="a355b-154">Değer</span><span class="sxs-lookup"><span data-stu-id="a355b-154">Value</span></span>|<span data-ttu-id="a355b-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a355b-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a355b-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="a355b-156">*policy_setting*</span></span>|<span data-ttu-id="a355b-157">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="a355b-157">The setting to apply to this policy type.</span></span> <span data-ttu-id="a355b-158">Olası değerler şunlardır,,,, `All` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="a355b-158">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="a355b-159">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a355b-159">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a355b-160">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a355b-160">Child Elements</span></span>  

 <span data-ttu-id="a355b-161">Yok.</span><span class="sxs-lookup"><span data-stu-id="a355b-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a355b-162">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a355b-162">Parent Elements</span></span>  
  
|<span data-ttu-id="a355b-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="a355b-163">Element</span></span>|<span data-ttu-id="a355b-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a355b-164">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="a355b-165">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="a355b-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="a355b-166">Çalışma zamanı yansıma ilkesini sınıf veya yapı gibi belirli bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="a355b-166">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a355b-167">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a355b-167">Remarks</span></span>  

 <span data-ttu-id="a355b-168">`<GenericParameter>`Öğesi ya da öğesinin bir alt öğesidir [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) ve ilkeyi genel tür veya yöntem imzasında adıyla belirtilen belirli bir genel tür parametresine uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a355b-168">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="a355b-169">`<GenericParameter>`Öğesi, serileştiriciler ile kullanıldığında en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a355b-169">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="a355b-170">Aşağıdaki örnek, `<GenericParameter>` `T` NewtonSoft JSON seri hale getirici 'Nin [JsonConvert. DeserializeObject \<T> (dize)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) yöntemi aşırı yüklerini çağıran türe ilke uygulamak için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a355b-170">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a355b-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a355b-171">See also</span></span>

- [<span data-ttu-id="a355b-172">\<Method> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="a355b-172">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="a355b-173">\<Type> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="a355b-173">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="a355b-174">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a355b-174">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a355b-175">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="a355b-175">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="a355b-176">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="a355b-176">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

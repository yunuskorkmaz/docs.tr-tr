---
title: <GenericParameter>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: d0b18211206a8f9d4365ab3affe6d1c376003348
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128427"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="866ae-102">\<GenericParameter>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="866ae-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="866ae-103">İlkeyi genel bir türün veya yöntemin parametre türüne uygular.</span><span class="sxs-lookup"><span data-stu-id="866ae-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="866ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="866ae-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="866ae-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="866ae-105">Attributes and Elements</span></span>  
 <span data-ttu-id="866ae-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="866ae-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="866ae-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="866ae-107">Attributes</span></span>  
  
|<span data-ttu-id="866ae-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="866ae-108">Attribute</span></span>|<span data-ttu-id="866ae-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="866ae-109">Attribute type</span></span>|<span data-ttu-id="866ae-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="866ae-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="866ae-111">Genel</span><span class="sxs-lookup"><span data-stu-id="866ae-111">General</span></span>|<span data-ttu-id="866ae-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-112">Required attribute.</span></span> <span data-ttu-id="866ae-113">Genel parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="866ae-113">The name of the generic parameter.</span></span> <span data-ttu-id="866ae-114">Örneğin, genel temsilci için <xref:System.Func%603> , `Name` çalışma zamanı ilkesini temsilcinin dönüş değerine uygulamak için özniteliğinin değeri "TResult" olur.</span><span class="sxs-lookup"><span data-stu-id="866ae-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="866ae-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="866ae-115">Reflection</span></span>|<span data-ttu-id="866ae-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-116">Optional attribute.</span></span> <span data-ttu-id="866ae-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="866ae-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="866ae-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="866ae-118">Reflection</span></span>|<span data-ttu-id="866ae-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-119">Optional attribute.</span></span> <span data-ttu-id="866ae-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="866ae-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="866ae-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="866ae-121">Reflection</span></span>|<span data-ttu-id="866ae-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-122">Optional attribute.</span></span> <span data-ttu-id="866ae-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="866ae-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="866ae-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="866ae-124">Serialization</span></span>|<span data-ttu-id="866ae-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-125">Optional attribute.</span></span> <span data-ttu-id="866ae-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="866ae-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="866ae-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="866ae-127">Serialization</span></span>|<span data-ttu-id="866ae-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-128">Optional attribute.</span></span> <span data-ttu-id="866ae-129">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="866ae-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="866ae-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="866ae-130">Serialization</span></span>|<span data-ttu-id="866ae-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-131">Optional attribute.</span></span> <span data-ttu-id="866ae-132">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="866ae-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="866ae-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="866ae-133">Serialization</span></span>|<span data-ttu-id="866ae-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-134">Optional attribute.</span></span> <span data-ttu-id="866ae-135">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="866ae-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="866ae-136">Interop</span><span class="sxs-lookup"><span data-stu-id="866ae-136">Interop</span></span>|<span data-ttu-id="866ae-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-137">Optional attribute.</span></span> <span data-ttu-id="866ae-138">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="866ae-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="866ae-139">Interop</span><span class="sxs-lookup"><span data-stu-id="866ae-139">Interop</span></span>|<span data-ttu-id="866ae-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-140">Optional attribute.</span></span> <span data-ttu-id="866ae-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="866ae-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="866ae-142">Interop</span><span class="sxs-lookup"><span data-stu-id="866ae-142">Interop</span></span>|<span data-ttu-id="866ae-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-143">Optional attribute.</span></span> <span data-ttu-id="866ae-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="866ae-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="866ae-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="866ae-145">Name attribute</span></span>  
  
|<span data-ttu-id="866ae-146">Değer</span><span class="sxs-lookup"><span data-stu-id="866ae-146">Value</span></span>|<span data-ttu-id="866ae-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="866ae-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="866ae-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="866ae-148">*generic_parameter_name*</span></span>|<span data-ttu-id="866ae-149">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="866ae-149">Required attribute.</span></span> <span data-ttu-id="866ae-150">Genel tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="866ae-150">The name of the generic type parameter.</span></span> <span data-ttu-id="866ae-151">Örneğin, genel temsilci için <xref:System.Func%603> , "TResult" *generic_parameter_name* değeri, temsilcinin dönüş değerine çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="866ae-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="866ae-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="866ae-152">All other attributes</span></span>  
  
|<span data-ttu-id="866ae-153">Değer</span><span class="sxs-lookup"><span data-stu-id="866ae-153">Value</span></span>|<span data-ttu-id="866ae-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="866ae-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="866ae-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="866ae-155">*policy_setting*</span></span>|<span data-ttu-id="866ae-156">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="866ae-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="866ae-157">Olası değerler şunlardır,,,, `All` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="866ae-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="866ae-158">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="866ae-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="866ae-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="866ae-159">Child Elements</span></span>  
 <span data-ttu-id="866ae-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="866ae-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="866ae-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="866ae-161">Parent Elements</span></span>  
  
|<span data-ttu-id="866ae-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="866ae-162">Element</span></span>|<span data-ttu-id="866ae-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="866ae-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="866ae-164">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="866ae-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="866ae-165">Çalışma zamanı yansıma ilkesini sınıf veya yapı gibi belirli bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="866ae-165">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="866ae-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="866ae-166">Remarks</span></span>  
 <span data-ttu-id="866ae-167">`<GenericParameter>`Öğesi ya da öğesinin bir alt öğesidir [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) ve ilkeyi genel tür veya yöntem imzasında adıyla belirtilen belirli bir genel tür parametresine uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="866ae-167">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="866ae-168">`<GenericParameter>`Öğesi, serileştiriciler ile kullanıldığında en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="866ae-168">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="866ae-169">Aşağıdaki örnek, `<GenericParameter>` `T` NewtonSoft JSON seri hale getirici 'Nin [JsonConvert. DeserializeObject \<T> (dize)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) yöntemi aşırı yüklerini çağıran türe ilke uygulamak için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="866ae-169">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="866ae-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="866ae-170">See also</span></span>

- [<span data-ttu-id="866ae-171">\<Method>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="866ae-171">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="866ae-172">\<Type>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="866ae-172">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="866ae-173">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="866ae-173">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="866ae-174">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="866ae-174">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="866ae-175">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="866ae-175">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

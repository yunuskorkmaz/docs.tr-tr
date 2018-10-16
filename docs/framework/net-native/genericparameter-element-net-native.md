---
title: '&lt;GenericParameter&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd0d9851f62381a16f628607c326c6690492628b
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347857"
---
# <a name="ltgenericparametergt-element-net-native"></a><span data-ttu-id="07959-102">&lt;GenericParameter&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="07959-102">&lt;GenericParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="07959-103">İlke bir genel tür veya yöntemin parametre türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07959-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07959-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07959-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07959-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="07959-105">Attributes and Elements</span></span>  
 <span data-ttu-id="07959-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07959-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07959-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07959-107">Attributes</span></span>  
  
|<span data-ttu-id="07959-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07959-108">Attribute</span></span>|<span data-ttu-id="07959-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="07959-109">Attribute type</span></span>|<span data-ttu-id="07959-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07959-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="07959-111">Genel</span><span class="sxs-lookup"><span data-stu-id="07959-111">General</span></span>|<span data-ttu-id="07959-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-112">Required attribute.</span></span> <span data-ttu-id="07959-113">Genel parametre adı.</span><span class="sxs-lookup"><span data-stu-id="07959-113">The name of the generic parameter.</span></span> <span data-ttu-id="07959-114">Örneğin, Genel temsilci <xref:System.Func%603>, değerini `Name` özniteliktir "TResult" temsilcinin dönüş değeri için çalışma zamanı ilkesini uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="07959-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="07959-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="07959-115">Reflection</span></span>|<span data-ttu-id="07959-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-116">Optional attribute.</span></span> <span data-ttu-id="07959-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="07959-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="07959-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="07959-118">Reflection</span></span>|<span data-ttu-id="07959-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-119">Optional attribute.</span></span> <span data-ttu-id="07959-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="07959-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="07959-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="07959-121">Reflection</span></span>|<span data-ttu-id="07959-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-122">Optional attribute.</span></span> <span data-ttu-id="07959-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="07959-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="07959-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07959-124">Serialization</span></span>|<span data-ttu-id="07959-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-125">Optional attribute.</span></span> <span data-ttu-id="07959-126">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="07959-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="07959-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07959-127">Serialization</span></span>|<span data-ttu-id="07959-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-128">Optional attribute.</span></span> <span data-ttu-id="07959-129">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="07959-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="07959-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07959-130">Serialization</span></span>|<span data-ttu-id="07959-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-131">Optional attribute.</span></span> <span data-ttu-id="07959-132">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="07959-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="07959-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="07959-133">Serialization</span></span>|<span data-ttu-id="07959-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-134">Optional attribute.</span></span> <span data-ttu-id="07959-135">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="07959-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="07959-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="07959-136">Interop</span></span>|<span data-ttu-id="07959-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-137">Optional attribute.</span></span> <span data-ttu-id="07959-138">Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi</span><span class="sxs-lookup"><span data-stu-id="07959-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="07959-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="07959-139">Interop</span></span>|<span data-ttu-id="07959-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-140">Optional attribute.</span></span> <span data-ttu-id="07959-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="07959-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="07959-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="07959-142">Interop</span></span>|<span data-ttu-id="07959-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-143">Optional attribute.</span></span> <span data-ttu-id="07959-144">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="07959-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="07959-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="07959-145">Name attribute</span></span>  
  
|<span data-ttu-id="07959-146">Değer</span><span class="sxs-lookup"><span data-stu-id="07959-146">Value</span></span>|<span data-ttu-id="07959-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07959-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07959-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="07959-148">*generic_parameter_name*</span></span>|<span data-ttu-id="07959-149">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07959-149">Required attribute.</span></span> <span data-ttu-id="07959-150">Genel tür parametre adı.</span><span class="sxs-lookup"><span data-stu-id="07959-150">The name of the generic type parameter.</span></span> <span data-ttu-id="07959-151">Örneğin, Genel temsilci <xref:System.Func%603>, *generic_parameter_name* "TResult" değerini çalışma zamanı İlkesi temsilcinin dönüş değeri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07959-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="07959-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07959-152">All other attributes</span></span>  
  
|<span data-ttu-id="07959-153">Değer</span><span class="sxs-lookup"><span data-stu-id="07959-153">Value</span></span>|<span data-ttu-id="07959-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07959-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07959-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="07959-155">*policy_setting*</span></span>|<span data-ttu-id="07959-156">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="07959-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="07959-157">Olası değerler `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="07959-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="07959-158">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="07959-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07959-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="07959-159">Child Elements</span></span>  
 <span data-ttu-id="07959-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="07959-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07959-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="07959-161">Parent Elements</span></span>  
  
|<span data-ttu-id="07959-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="07959-162">Element</span></span>|<span data-ttu-id="07959-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07959-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07959-164">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="07959-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="07959-165">Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07959-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="07959-166">\<türü ></span><span class="sxs-lookup"><span data-stu-id="07959-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="07959-167">Bir sınıf veya yapı gibi belirli bir tür için çalışma zamanı yansıma ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="07959-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07959-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07959-168">Remarks</span></span>  
 <span data-ttu-id="07959-169">`<GenericParameter>` Ya da bir alt öğedir [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) veya [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi olan bir belirli genel tür parametresi için ilkeyi uygulamak için kullanılır genel tür veya yöntem İmzasındaki adı belirtildi.</span><span class="sxs-lookup"><span data-stu-id="07959-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="07959-170">`<GenericParameter>` Öğesi, seri hale getiricileri genişletme ile kullanıldığında en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="07959-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="07959-171">Aşağıdaki örnekte `<GenericParameter>` ilke türü için geçerli öğe `T` NewtonSoft JSON seri hale getirici'nın çağrılarında [JsonConvert.DeserializeObject\<T > (dize)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) yöntemi aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="07959-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07959-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07959-172">See Also</span></span>  
 [<span data-ttu-id="07959-173">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="07959-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="07959-174">\<Türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="07959-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="07959-175">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="07959-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="07959-176">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="07959-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="07959-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="07959-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

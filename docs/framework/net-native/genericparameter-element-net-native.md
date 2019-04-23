---
title: <GenericParameter> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40fef845a55412e5731ec08bd1e038d6b311694c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111663"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="6a244-102">\<GenericParameter > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="6a244-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="6a244-103">İlke bir genel tür veya yöntemin parametre türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6a244-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a244-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a244-104">Syntax</span></span>  
  
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
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a244-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a244-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6a244-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a244-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a244-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a244-107">Attributes</span></span>  
  
|<span data-ttu-id="6a244-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a244-108">Attribute</span></span>|<span data-ttu-id="6a244-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="6a244-109">Attribute type</span></span>|<span data-ttu-id="6a244-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a244-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6a244-111">Genel</span><span class="sxs-lookup"><span data-stu-id="6a244-111">General</span></span>|<span data-ttu-id="6a244-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-112">Required attribute.</span></span> <span data-ttu-id="6a244-113">Genel parametre adı.</span><span class="sxs-lookup"><span data-stu-id="6a244-113">The name of the generic parameter.</span></span> <span data-ttu-id="6a244-114">Örneğin, Genel temsilci <xref:System.Func%603>, değerini `Name` özniteliktir "TResult" temsilcinin dönüş değeri için çalışma zamanı ilkesini uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="6a244-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="6a244-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6a244-115">Reflection</span></span>|<span data-ttu-id="6a244-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-116">Optional attribute.</span></span> <span data-ttu-id="6a244-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="6a244-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6a244-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6a244-118">Reflection</span></span>|<span data-ttu-id="6a244-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-119">Optional attribute.</span></span> <span data-ttu-id="6a244-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6a244-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6a244-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="6a244-121">Reflection</span></span>|<span data-ttu-id="6a244-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-122">Optional attribute.</span></span> <span data-ttu-id="6a244-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="6a244-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6a244-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a244-124">Serialization</span></span>|<span data-ttu-id="6a244-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-125">Optional attribute.</span></span> <span data-ttu-id="6a244-126">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="6a244-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6a244-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a244-127">Serialization</span></span>|<span data-ttu-id="6a244-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-128">Optional attribute.</span></span> <span data-ttu-id="6a244-129">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a244-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6a244-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a244-130">Serialization</span></span>|<span data-ttu-id="6a244-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-131">Optional attribute.</span></span> <span data-ttu-id="6a244-132">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a244-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6a244-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="6a244-133">Serialization</span></span>|<span data-ttu-id="6a244-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-134">Optional attribute.</span></span> <span data-ttu-id="6a244-135">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a244-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6a244-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6a244-136">Interop</span></span>|<span data-ttu-id="6a244-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-137">Optional attribute.</span></span> <span data-ttu-id="6a244-138">Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi</span><span class="sxs-lookup"><span data-stu-id="6a244-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6a244-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6a244-139">Interop</span></span>|<span data-ttu-id="6a244-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-140">Optional attribute.</span></span> <span data-ttu-id="6a244-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="6a244-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6a244-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="6a244-142">Interop</span></span>|<span data-ttu-id="6a244-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-143">Optional attribute.</span></span> <span data-ttu-id="6a244-144">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="6a244-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6a244-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="6a244-145">Name attribute</span></span>  
  
|<span data-ttu-id="6a244-146">Değer</span><span class="sxs-lookup"><span data-stu-id="6a244-146">Value</span></span>|<span data-ttu-id="6a244-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a244-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a244-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="6a244-148">*generic_parameter_name*</span></span>|<span data-ttu-id="6a244-149">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6a244-149">Required attribute.</span></span> <span data-ttu-id="6a244-150">Genel tür parametre adı.</span><span class="sxs-lookup"><span data-stu-id="6a244-150">The name of the generic type parameter.</span></span> <span data-ttu-id="6a244-151">Örneğin, Genel temsilci <xref:System.Func%603>, *generic_parameter_name* "TResult" değerini çalışma zamanı İlkesi temsilcinin dönüş değeri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6a244-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6a244-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a244-152">All other attributes</span></span>  
  
|<span data-ttu-id="6a244-153">Değer</span><span class="sxs-lookup"><span data-stu-id="6a244-153">Value</span></span>|<span data-ttu-id="6a244-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a244-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a244-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6a244-155">*policy_setting*</span></span>|<span data-ttu-id="6a244-156">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="6a244-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="6a244-157">Olası değerler `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="6a244-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6a244-158">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6a244-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a244-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a244-159">Child Elements</span></span>  
 <span data-ttu-id="6a244-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a244-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a244-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a244-161">Parent Elements</span></span>  
  
|<span data-ttu-id="6a244-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a244-162">Element</span></span>|<span data-ttu-id="6a244-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a244-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a244-164">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="6a244-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="6a244-165">Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6a244-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="6a244-166">\<türü ></span><span class="sxs-lookup"><span data-stu-id="6a244-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6a244-167">Bir sınıf veya yapı gibi belirli bir tür için çalışma zamanı yansıma ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="6a244-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a244-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a244-168">Remarks</span></span>  
 <span data-ttu-id="6a244-169">`<GenericParameter>` Ya da bir alt öğedir [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) veya [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi olan bir belirli genel tür parametresi için ilkeyi uygulamak için kullanılır genel tür veya yöntem İmzasındaki adı belirtildi.</span><span class="sxs-lookup"><span data-stu-id="6a244-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="6a244-170">`<GenericParameter>` Öğesi, seri hale getiricileri genişletme ile kullanıldığında en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6a244-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="6a244-171">Aşağıdaki örnekte `<GenericParameter>` ilke türü için geçerli öğe `T` NewtonSoft JSON seri hale getirici'nın çağrılarında [JsonConvert.DeserializeObject\<T > (dize)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) yöntemi aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="6a244-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a244-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a244-172">See also</span></span>

- [<span data-ttu-id="6a244-173">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="6a244-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="6a244-174">\<Türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="6a244-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="6a244-175">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6a244-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6a244-176">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="6a244-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="6a244-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6a244-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

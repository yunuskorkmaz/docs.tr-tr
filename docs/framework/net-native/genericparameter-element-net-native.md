---
title: "&lt;GenericParameter&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c682c75d4be78e9219a32e2a92520e9f9bfff823
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltgenericparametergt-element-net-native"></a><span data-ttu-id="0e09c-102">&lt;GenericParameter&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="0e09c-102">&lt;GenericParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="0e09c-103">İlke genel türü veya yöntemi parametresinin türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0e09c-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e09c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e09c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e09c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e09c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0e09c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e09c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e09c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e09c-107">Attributes</span></span>  
  
|<span data-ttu-id="0e09c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e09c-108">Attribute</span></span>|<span data-ttu-id="0e09c-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="0e09c-109">Attribute type</span></span>|<span data-ttu-id="0e09c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e09c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0e09c-111">Genel</span><span class="sxs-lookup"><span data-stu-id="0e09c-111">General</span></span>|<span data-ttu-id="0e09c-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-112">Required attribute.</span></span> <span data-ttu-id="0e09c-113">Genel parametre adı.</span><span class="sxs-lookup"><span data-stu-id="0e09c-113">The name of the generic parameter.</span></span> <span data-ttu-id="0e09c-114">Örneğin, genel temsilcisi <xref:System.Func%603>, değeri `Name` özniteliktir "TResult" temsilcinin dönüş değeri için çalışma zamanı ilkesi uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="0e09c-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="0e09c-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0e09c-115">Reflection</span></span>|<span data-ttu-id="0e09c-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-116">Optional attribute.</span></span> <span data-ttu-id="0e09c-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0e09c-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0e09c-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0e09c-118">Reflection</span></span>|<span data-ttu-id="0e09c-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-119">Optional attribute.</span></span> <span data-ttu-id="0e09c-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0e09c-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="0e09c-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0e09c-121">Reflection</span></span>|<span data-ttu-id="0e09c-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-122">Optional attribute.</span></span> <span data-ttu-id="0e09c-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0e09c-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0e09c-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e09c-124">Serialization</span></span>|<span data-ttu-id="0e09c-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-125">Optional attribute.</span></span> <span data-ttu-id="0e09c-126">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="0e09c-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0e09c-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e09c-127">Serialization</span></span>|<span data-ttu-id="0e09c-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-128">Optional attribute.</span></span> <span data-ttu-id="0e09c-129">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e09c-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0e09c-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e09c-130">Serialization</span></span>|<span data-ttu-id="0e09c-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-131">Optional attribute.</span></span> <span data-ttu-id="0e09c-132">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e09c-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0e09c-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e09c-133">Serialization</span></span>|<span data-ttu-id="0e09c-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-134">Optional attribute.</span></span> <span data-ttu-id="0e09c-135">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e09c-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0e09c-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="0e09c-136">Interop</span></span>|<span data-ttu-id="0e09c-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-137">Optional attribute.</span></span> <span data-ttu-id="0e09c-138">Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi</span><span class="sxs-lookup"><span data-stu-id="0e09c-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0e09c-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="0e09c-139">Interop</span></span>|<span data-ttu-id="0e09c-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-140">Optional attribute.</span></span> <span data-ttu-id="0e09c-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="0e09c-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0e09c-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="0e09c-142">Interop</span></span>|<span data-ttu-id="0e09c-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-143">Optional attribute.</span></span> <span data-ttu-id="0e09c-144">Değer türleri yerel koda hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="0e09c-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0e09c-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="0e09c-145">Name attribute</span></span>  
  
|<span data-ttu-id="0e09c-146">Değer</span><span class="sxs-lookup"><span data-stu-id="0e09c-146">Value</span></span>|<span data-ttu-id="0e09c-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e09c-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e09c-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="0e09c-148">*generic_parameter_name*</span></span>|<span data-ttu-id="0e09c-149">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e09c-149">Required attribute.</span></span> <span data-ttu-id="0e09c-150">Genel tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="0e09c-150">The name of the generic type parameter.</span></span> <span data-ttu-id="0e09c-151">Örneğin, genel temsilcisi <xref:System.Func%603>, *generic_parameter_name* "TResult" değerini temsilcinin dönüş değeri için çalışma zamanı ilkesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0e09c-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0e09c-152">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="0e09c-152">All other attributes</span></span>  
  
|<span data-ttu-id="0e09c-153">Değer</span><span class="sxs-lookup"><span data-stu-id="0e09c-153">Value</span></span>|<span data-ttu-id="0e09c-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e09c-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e09c-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0e09c-155">*policy_setting*</span></span>|<span data-ttu-id="0e09c-156">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="0e09c-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="0e09c-157">Olası değerler şunlardır: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="0e09c-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0e09c-158">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0e09c-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e09c-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e09c-159">Child Elements</span></span>  
 <span data-ttu-id="0e09c-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e09c-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e09c-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e09c-161">Parent Elements</span></span>  
  
|<span data-ttu-id="0e09c-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e09c-162">Element</span></span>|<span data-ttu-id="0e09c-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e09c-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e09c-164">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="0e09c-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="0e09c-165">Çalışma zamanı yansıma ilke oluşturucunun ya da yöntemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0e09c-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="0e09c-166">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="0e09c-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="0e09c-167">Bir sınıf veya yapı gibi belirli türde bir çalışma zamanı yansıma ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0e09c-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e09c-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e09c-168">Remarks</span></span>  
 <span data-ttu-id="0e09c-169">`<GenericParameter>` Ya da bir alt öğedir [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) veya [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi ve olan belirli genel tür parametresi, ilkeyi uygulamak için kullanılır Genel türü veya yöntemi imzada adıyla belirtilen.</span><span class="sxs-lookup"><span data-stu-id="0e09c-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="0e09c-170">`<GenericParameter>` Öğesidir serileştiricileri ile kullanıldığında en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e09c-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="0e09c-171">Aşağıdaki örnek kullanır `<GenericParameter>` ilke türü için geçerli öğe `T` NewtonSoft JSON seri hale getirici'nın çağrılarında [JsonConvert.DeserializeObject\<T > (dize)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) yöntemi aşırı.</span><span class="sxs-lookup"><span data-stu-id="0e09c-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e09c-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e09c-172">See Also</span></span>  
 [<span data-ttu-id="0e09c-173">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="0e09c-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="0e09c-174">\<Tür > öğesi</span><span class="sxs-lookup"><span data-stu-id="0e09c-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="0e09c-175">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="0e09c-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="0e09c-176">Çalışma zamanı yönerge İlkesi ayarları</span><span class="sxs-lookup"><span data-stu-id="0e09c-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="0e09c-177">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="0e09c-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

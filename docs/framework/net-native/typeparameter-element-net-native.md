---
description: 'Daha fazla bilgi edinin: <TypeParameter> öğesi (.NET Native)'
title: <TypeParameter> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: 182cd62dc0584991b8ef0f5757d6005173d6d7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803652"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="544ee-103">\<TypeParameter> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="544ee-103">\<TypeParameter> Element (.NET Native)</span></span>

<span data-ttu-id="544ee-104">Bir yönteme geçirilen bir tür bağımsız değişkeni tarafından temsil edilen türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="544ee-104">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544ee-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="544ee-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="544ee-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="544ee-106">Attributes and Elements</span></span>  

 <span data-ttu-id="544ee-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="544ee-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="544ee-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="544ee-108">Attributes</span></span>  
  
|<span data-ttu-id="544ee-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="544ee-109">Attribute</span></span>|<span data-ttu-id="544ee-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="544ee-110">Attribute type</span></span>|<span data-ttu-id="544ee-111">Description</span><span class="sxs-lookup"><span data-stu-id="544ee-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="544ee-112">Genel</span><span class="sxs-lookup"><span data-stu-id="544ee-112">General</span></span>|<span data-ttu-id="544ee-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-113">Required attribute.</span></span> <span data-ttu-id="544ee-114">Türünün parametresinin adı <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="544ee-114">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="544ee-115">Örneğin, yöntem imzası için `Type.GetInterfaceMap(Type interfaceType)` , `Name` özniteliği değeri "InterfaceType" olur.</span><span class="sxs-lookup"><span data-stu-id="544ee-115">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="544ee-116">Yansıma</span><span class="sxs-lookup"><span data-stu-id="544ee-116">Reflection</span></span>|<span data-ttu-id="544ee-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-117">Optional attribute.</span></span> <span data-ttu-id="544ee-118">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="544ee-118">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="544ee-119">Yansıma</span><span class="sxs-lookup"><span data-stu-id="544ee-119">Reflection</span></span>|<span data-ttu-id="544ee-120">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-120">Optional attribute.</span></span> <span data-ttu-id="544ee-121">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="544ee-121">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="544ee-122">Yansıma</span><span class="sxs-lookup"><span data-stu-id="544ee-122">Reflection</span></span>|<span data-ttu-id="544ee-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-123">Optional attribute.</span></span> <span data-ttu-id="544ee-124">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="544ee-124">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="544ee-125">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="544ee-125">Serialization</span></span>|<span data-ttu-id="544ee-126">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-126">Optional attribute.</span></span> <span data-ttu-id="544ee-127">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="544ee-127">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="544ee-128">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="544ee-128">Serialization</span></span>|<span data-ttu-id="544ee-129">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-129">Optional attribute.</span></span> <span data-ttu-id="544ee-130">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="544ee-130">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="544ee-131">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="544ee-131">Serialization</span></span>|<span data-ttu-id="544ee-132">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-132">Optional attribute.</span></span> <span data-ttu-id="544ee-133">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="544ee-133">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="544ee-134">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="544ee-134">Serialization</span></span>|<span data-ttu-id="544ee-135">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-135">Optional attribute.</span></span> <span data-ttu-id="544ee-136">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="544ee-136">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="544ee-137">Interop</span><span class="sxs-lookup"><span data-stu-id="544ee-137">Interop</span></span>|<span data-ttu-id="544ee-138">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-138">Optional attribute.</span></span> <span data-ttu-id="544ee-139">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="544ee-139">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="544ee-140">Interop</span><span class="sxs-lookup"><span data-stu-id="544ee-140">Interop</span></span>|<span data-ttu-id="544ee-141">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-141">Optional attribute.</span></span> <span data-ttu-id="544ee-142">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="544ee-142">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="544ee-143">Interop</span><span class="sxs-lookup"><span data-stu-id="544ee-143">Interop</span></span>|<span data-ttu-id="544ee-144">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="544ee-144">Optional attribute.</span></span> <span data-ttu-id="544ee-145">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="544ee-145">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="544ee-146">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="544ee-146">Name attribute</span></span>  
  
|<span data-ttu-id="544ee-147">Değer</span><span class="sxs-lookup"><span data-stu-id="544ee-147">Value</span></span>|<span data-ttu-id="544ee-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="544ee-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="544ee-149">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="544ee-149">*parameter_name*</span></span>|<span data-ttu-id="544ee-150">Türünün parametresinin adı <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="544ee-150">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="544ee-151">Örneğin, yöntem imzası için `Type.GetInterfaceMap(Type interfaceType)` , `Name` özniteliği değeri "InterfaceType" olur.</span><span class="sxs-lookup"><span data-stu-id="544ee-151">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="544ee-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="544ee-152">All other attributes</span></span>  
  
|<span data-ttu-id="544ee-153">Değer</span><span class="sxs-lookup"><span data-stu-id="544ee-153">Value</span></span>|<span data-ttu-id="544ee-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="544ee-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="544ee-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="544ee-155">*policy_setting*</span></span>|<span data-ttu-id="544ee-156">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="544ee-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="544ee-157">Olası değerler şunlardır,,,, `All` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="544ee-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="544ee-158">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="544ee-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="544ee-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="544ee-159">Child Elements</span></span>  

 <span data-ttu-id="544ee-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="544ee-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="544ee-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="544ee-161">Parent Elements</span></span>  
  
|<span data-ttu-id="544ee-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="544ee-162">Element</span></span>|<span data-ttu-id="544ee-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="544ee-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="544ee-164">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="544ee-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="544ee-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="544ee-165">Remarks</span></span>  

 <span data-ttu-id="544ee-166">`<TypeParameter>`Öğesi öğesine benzerdir [\<Parameter>](parameter-element-net-native.md) , ancak yalnızca türündeki parametrelere uygulanabilirler <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="544ee-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="544ee-167">Çalışma zamanında, özniteliği tarafından belirtilen tür bağımsız değişkeni tarafından temsil edilen herhangi bir tür için ilke uygular `Name` .</span><span class="sxs-lookup"><span data-stu-id="544ee-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="544ee-168">Örneğin, NewtonSoft JSON seri hale getirici statik bir `JsonConvert.DeserializeObject(String value, Type type)` yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="544ee-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="544ee-169">Aşağıdaki yansıma yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="544ee-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="544ee-170">bağımsız değişkenle temsil edilen çalışma zamanı türü için meta verilerin `type` serileştirme için kullanılabilir hale getirilmesi gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="544ee-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="544ee-171">Bu çalışma zamanı yönergeleri aşağıdaki kaynak kodu içeren bir proje için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="544ee-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="544ee-172">yansıma yönergeleri, `StockQuote` çalışma zamanında NewtonSoft JSON serileştirici için kullanılabilir tür meta verilerini yapar.</span><span class="sxs-lookup"><span data-stu-id="544ee-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544ee-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="544ee-173">See also</span></span>

- [<span data-ttu-id="544ee-174">\<Method> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="544ee-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="544ee-175">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="544ee-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="544ee-176">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="544ee-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="544ee-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="544ee-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

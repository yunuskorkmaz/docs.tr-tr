---
title: <TypeParameter> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: c69b535f3a01c287d30189138130066fc10a77e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128921"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="15f40-102">\<TypeParameter > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="15f40-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="15f40-103">Bir yönteme geçirilen bir tür bağımsız değişkeni tarafından temsil edilen türe ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="15f40-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15f40-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15f40-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15f40-105">Attributes and Elements</span></span>  
 <span data-ttu-id="15f40-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15f40-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15f40-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15f40-107">Attributes</span></span>  
  
|<span data-ttu-id="15f40-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15f40-108">Attribute</span></span>|<span data-ttu-id="15f40-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="15f40-109">Attribute type</span></span>|<span data-ttu-id="15f40-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f40-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="15f40-111">Genel</span><span class="sxs-lookup"><span data-stu-id="15f40-111">General</span></span>|<span data-ttu-id="15f40-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-112">Required attribute.</span></span> <span data-ttu-id="15f40-113"><xref:System.Type>türünün parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="15f40-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="15f40-114">Örneğin, yöntem imzası `Type.GetInterfaceMap(Type interfaceType)`, `Name` özniteliğinin değeri "InterfaceType" olur.</span><span class="sxs-lookup"><span data-stu-id="15f40-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="15f40-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="15f40-115">Reflection</span></span>|<span data-ttu-id="15f40-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-116">Optional attribute.</span></span> <span data-ttu-id="15f40-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="15f40-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="15f40-118">Reflection</span></span>|<span data-ttu-id="15f40-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-119">Optional attribute.</span></span> <span data-ttu-id="15f40-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="15f40-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="15f40-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="15f40-121">Reflection</span></span>|<span data-ttu-id="15f40-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-122">Optional attribute.</span></span> <span data-ttu-id="15f40-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="15f40-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="15f40-124">Serialization</span></span>|<span data-ttu-id="15f40-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-125">Optional attribute.</span></span> <span data-ttu-id="15f40-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="15f40-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="15f40-127">Serialization</span></span>|<span data-ttu-id="15f40-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-128">Optional attribute.</span></span> <span data-ttu-id="15f40-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="15f40-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="15f40-130">Serialization</span></span>|<span data-ttu-id="15f40-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-131">Optional attribute.</span></span> <span data-ttu-id="15f40-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="15f40-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="15f40-133">Serialization</span></span>|<span data-ttu-id="15f40-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-134">Optional attribute.</span></span> <span data-ttu-id="15f40-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="15f40-136">Interop</span><span class="sxs-lookup"><span data-stu-id="15f40-136">Interop</span></span>|<span data-ttu-id="15f40-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-137">Optional attribute.</span></span> <span data-ttu-id="15f40-138">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="15f40-139">Interop</span><span class="sxs-lookup"><span data-stu-id="15f40-139">Interop</span></span>|<span data-ttu-id="15f40-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-140">Optional attribute.</span></span> <span data-ttu-id="15f40-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="15f40-142">Interop</span><span class="sxs-lookup"><span data-stu-id="15f40-142">Interop</span></span>|<span data-ttu-id="15f40-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f40-143">Optional attribute.</span></span> <span data-ttu-id="15f40-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="15f40-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="15f40-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="15f40-145">Name attribute</span></span>  
  
|<span data-ttu-id="15f40-146">Değer</span><span class="sxs-lookup"><span data-stu-id="15f40-146">Value</span></span>|<span data-ttu-id="15f40-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f40-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15f40-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="15f40-148">*parameter_name*</span></span>|<span data-ttu-id="15f40-149"><xref:System.Type>türünün parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="15f40-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="15f40-150">Örneğin, yöntem imzası `Type.GetInterfaceMap(Type interfaceType)`, `Name` özniteliğinin değeri "InterfaceType" olur.</span><span class="sxs-lookup"><span data-stu-id="15f40-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="15f40-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15f40-151">All other attributes</span></span>  
  
|<span data-ttu-id="15f40-152">Değer</span><span class="sxs-lookup"><span data-stu-id="15f40-152">Value</span></span>|<span data-ttu-id="15f40-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f40-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15f40-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="15f40-154">*policy_setting*</span></span>|<span data-ttu-id="15f40-155">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="15f40-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="15f40-156">Olası değerler şunlardır `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="15f40-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="15f40-157">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="15f40-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15f40-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15f40-158">Child Elements</span></span>  
 <span data-ttu-id="15f40-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="15f40-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15f40-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15f40-160">Parent Elements</span></span>  
  
|<span data-ttu-id="15f40-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="15f40-161">Element</span></span>|<span data-ttu-id="15f40-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f40-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15f40-163">\<yöntemi ></span><span class="sxs-lookup"><span data-stu-id="15f40-163">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="15f40-164">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="15f40-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15f40-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15f40-165">Remarks</span></span>  
 <span data-ttu-id="15f40-166">`<TypeParameter>` öğesi [\<Parameter >](parameter-element-net-native.md) öğesine benzerdir, ancak yalnızca <xref:System.Type>türündeki parametrelere uygulanabilirler.</span><span class="sxs-lookup"><span data-stu-id="15f40-166">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="15f40-167">Çalışma zamanında, `Name` özniteliği tarafından belirtilen tür bağımsız değişkeni tarafından temsil edilen herhangi bir tür için ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="15f40-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="15f40-168">Örneğin, NewtonSoft JSON seri hale getirici statik bir `JsonConvert.DeserializeObject(String value, Type type)` yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="15f40-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="15f40-169">Aşağıdaki yansıma yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="15f40-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="15f40-170">`type` bağımsız değişkeniyle temsil edilen çalışma zamanı türü için meta verilerin serileştirme için kullanılabilir hale getirilmesi gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="15f40-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="15f40-171">Bu çalışma zamanı yönergeleri aşağıdaki kaynak kodu içeren bir proje için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="15f40-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="15f40-172">yansıma yönergeleri, çalışma zamanında NewtonSoft JSON serileştirici için kullanılabilir `StockQuote` türü için meta verileri yapar.</span><span class="sxs-lookup"><span data-stu-id="15f40-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f40-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15f40-173">See also</span></span>

- [<span data-ttu-id="15f40-174">\<yöntemi > öğesi</span><span class="sxs-lookup"><span data-stu-id="15f40-174">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="15f40-175">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="15f40-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="15f40-176">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="15f40-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="15f40-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="15f40-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

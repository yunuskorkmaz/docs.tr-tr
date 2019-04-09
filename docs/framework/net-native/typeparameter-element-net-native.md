---
title: <TypeParameter> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b03c87c70fa1bfcd331f468d369632f4164300bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110220"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="8aa70-102">\<TypeParameter > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="8aa70-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="8aa70-103">Bir yönteme geçirilen tür bağımsız değişkeni tarafından temsil edilen bir türün ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8aa70-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8aa70-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aa70-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa70-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8aa70-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8aa70-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aa70-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8aa70-107">Attributes</span></span>  
  
|<span data-ttu-id="8aa70-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8aa70-108">Attribute</span></span>|<span data-ttu-id="8aa70-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="8aa70-109">Attribute type</span></span>|<span data-ttu-id="8aa70-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa70-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8aa70-111">Genel</span><span class="sxs-lookup"><span data-stu-id="8aa70-111">General</span></span>|<span data-ttu-id="8aa70-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-112">Required attribute.</span></span> <span data-ttu-id="8aa70-113">Tür parametresinin adı <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="8aa70-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="8aa70-114">Örneğin, yöntem imzası için `Type.GetInterfaceMap(Type interfaceType)`, değerini `Name` özniteliktir "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="8aa70-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="8aa70-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8aa70-115">Reflection</span></span>|<span data-ttu-id="8aa70-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-116">Optional attribute.</span></span> <span data-ttu-id="8aa70-117">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="8aa70-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8aa70-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8aa70-118">Reflection</span></span>|<span data-ttu-id="8aa70-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-119">Optional attribute.</span></span> <span data-ttu-id="8aa70-120">Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8aa70-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8aa70-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="8aa70-121">Reflection</span></span>|<span data-ttu-id="8aa70-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-122">Optional attribute.</span></span> <span data-ttu-id="8aa70-123">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemler, alanlar, özellikler ve olaylar, tüm tür üyelerini, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="8aa70-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8aa70-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8aa70-124">Serialization</span></span>|<span data-ttu-id="8aa70-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-125">Optional attribute.</span></span> <span data-ttu-id="8aa70-126">Oluşturucular, alanları ve tür örnekleri sıralanabilir ve kitaplıkları gibi Newtonsoft JSON seri hale getirici tarafından serisi etkinleştirmek için özellikler, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="8aa70-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8aa70-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8aa70-127">Serialization</span></span>|<span data-ttu-id="8aa70-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-128">Optional attribute.</span></span> <span data-ttu-id="8aa70-129">Denetimleri İlkesi kullanan Serileştirmenin <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8aa70-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8aa70-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8aa70-130">Serialization</span></span>|<span data-ttu-id="8aa70-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-131">Optional attribute.</span></span> <span data-ttu-id="8aa70-132">İlke kullanan bir JSON serileştirme denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8aa70-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8aa70-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8aa70-133">Serialization</span></span>|<span data-ttu-id="8aa70-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-134">Optional attribute.</span></span> <span data-ttu-id="8aa70-135">İlke kullanan bir XML serileştirme denetleyen <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8aa70-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8aa70-136">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8aa70-136">Interop</span></span>|<span data-ttu-id="8aa70-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-137">Optional attribute.</span></span> <span data-ttu-id="8aa70-138">Windows çalışma zamanı ve COM başvuru türlerini hazırlama denetimleri İlkesi</span><span class="sxs-lookup"><span data-stu-id="8aa70-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8aa70-139">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8aa70-139">Interop</span></span>|<span data-ttu-id="8aa70-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-140">Optional attribute.</span></span> <span data-ttu-id="8aa70-141">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="8aa70-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8aa70-142">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="8aa70-142">Interop</span></span>|<span data-ttu-id="8aa70-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aa70-143">Optional attribute.</span></span> <span data-ttu-id="8aa70-144">Yerel kod için değer türlerini hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="8aa70-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8aa70-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="8aa70-145">Name attribute</span></span>  
  
|<span data-ttu-id="8aa70-146">Değer</span><span class="sxs-lookup"><span data-stu-id="8aa70-146">Value</span></span>|<span data-ttu-id="8aa70-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa70-147">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="8aa70-148">parameter_name</span><span class="sxs-lookup"><span data-stu-id="8aa70-148">parameter_name</span></span>*|<span data-ttu-id="8aa70-149">Tür parametresinin adı <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="8aa70-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="8aa70-150">Örneğin, yöntem imzası için `Type.GetInterfaceMap(Type interfaceType)`, değerini `Name` özniteliktir "InterfaceType".</span><span class="sxs-lookup"><span data-stu-id="8aa70-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8aa70-151">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8aa70-151">All other attributes</span></span>  
  
|<span data-ttu-id="8aa70-152">Değer</span><span class="sxs-lookup"><span data-stu-id="8aa70-152">Value</span></span>|<span data-ttu-id="8aa70-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa70-153">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="8aa70-154">policy_setting</span><span class="sxs-lookup"><span data-stu-id="8aa70-154">policy_setting</span></span>*|<span data-ttu-id="8aa70-155">Bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="8aa70-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="8aa70-156">Olası değerler `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="8aa70-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8aa70-157">Daha fazla bilgi için [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8aa70-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aa70-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa70-158">Child Elements</span></span>  
 <span data-ttu-id="8aa70-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="8aa70-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aa70-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa70-160">Parent Elements</span></span>  
  
|<span data-ttu-id="8aa70-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="8aa70-161">Element</span></span>|<span data-ttu-id="8aa70-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa70-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8aa70-163">\<Yöntem ></span><span class="sxs-lookup"><span data-stu-id="8aa70-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="8aa70-164">Çalışma zamanı yansıma ilkesini yapıcıya veya yönteme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8aa70-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aa70-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8aa70-165">Remarks</span></span>  
 <span data-ttu-id="8aa70-166">`<TypeParameter>` Öğesi benzer [ \<parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md) BT'nin yalnızca tür parametreleri için uygulanabilir dışında öğesi <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="8aa70-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="8aa70-167">Hangi tür çalışma zamanında tarafından belirtilen tür bağımsız değişkeni tarafından temsil edilen için ilke uygulanır `Name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8aa70-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="8aa70-168">Örneğin, bir statik NewtonSoft JSON serileştirici içerir `JsonConvert.DeserializeObject(String value, Type type)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8aa70-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="8aa70-169">Aşağıdaki yansıma yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="8aa70-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="8aa70-170">tarafından temsil edilen çalışma zamanı türü için meta verilerin belirtin `type` bağımsız değişkeni seri hale getirme için kullanılabilir hale.</span><span class="sxs-lookup"><span data-stu-id="8aa70-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="8aa70-171">Bu çalışma zamanı yönergeleri aşağıdaki kaynak kodunu içeren bir projeye uygularsanız:</span><span class="sxs-lookup"><span data-stu-id="8aa70-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="8aa70-172">Yansıma yönergeleri meta verileri oluşturmak için `StockQuote` türü NewtonSoft JSON serileştirici çalışma zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8aa70-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa70-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aa70-173">See also</span></span>

- [<span data-ttu-id="8aa70-174">\<Yöntem > öğesi</span><span class="sxs-lookup"><span data-stu-id="8aa70-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="8aa70-175">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8aa70-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8aa70-176">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="8aa70-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="8aa70-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="8aa70-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

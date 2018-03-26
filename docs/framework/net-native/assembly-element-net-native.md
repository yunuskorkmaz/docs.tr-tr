---
title: '&lt;Assembly&gt; Öğesi (.NET Yerel)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34e49e4d11f442f15db2f06b330b8b84a165a08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="ltassemblygt-element-net-native"></a><span data-ttu-id="2cf7d-102">&lt;Assembly&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="2cf7d-102">&lt;Assembly&gt; Element (.NET Native)</span></span>
<span data-ttu-id="2cf7d-103">Belirtilen derleme içindeki tüm türler için çalışma zamanı yansıma ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-103">Applies runtime reflection policy to all the types in a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cf7d-104">Syntax</span></span>  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting" />  
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cf7d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cf7d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2cf7d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cf7d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2cf7d-107">Attributes</span></span>  
  
|<span data-ttu-id="2cf7d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2cf7d-108">Attribute</span></span>|<span data-ttu-id="2cf7d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="2cf7d-109">Attribute type</span></span>|<span data-ttu-id="2cf7d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cf7d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="2cf7d-111">Genel</span><span class="sxs-lookup"><span data-stu-id="2cf7d-111">General</span></span>|<span data-ttu-id="2cf7d-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-112">Required attribute.</span></span> <span data-ttu-id="2cf7d-113">Basit bir bütünleştirilmiş kodun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-113">Specifies the simple name of an assembly.</span></span>|  
|`Activate`|<span data-ttu-id="2cf7d-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2cf7d-114">Reflection</span></span>|<span data-ttu-id="2cf7d-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-115">Optional attribute.</span></span> <span data-ttu-id="2cf7d-116">Oluşturucular örneklerinin etkinleştirmesi için çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="2cf7d-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2cf7d-117">Reflection</span></span>|<span data-ttu-id="2cf7d-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-118">Optional attribute.</span></span> <span data-ttu-id="2cf7d-119">Hakkında bilgi için sorgulama veya derlemesindeki türler numaralandırma kontrol eder, ancak çalışma zamanında herhangi bir dinamik erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-119">Controls querying for information about or enumerating the types in the assembly, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="2cf7d-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2cf7d-120">Reflection</span></span>|<span data-ttu-id="2cf7d-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-121">Optional attribute.</span></span> <span data-ttu-id="2cf7d-122">Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="2cf7d-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2cf7d-123">Serialization</span></span>|<span data-ttu-id="2cf7d-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-124">Optional attribute.</span></span> <span data-ttu-id="2cf7d-125">Oluşturucular, alanları ve seri hale getirilmiş ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="2cf7d-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2cf7d-126">Serialization</span></span>|<span data-ttu-id="2cf7d-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-127">Optional attribute.</span></span> <span data-ttu-id="2cf7d-128">Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="2cf7d-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2cf7d-129">Serialization</span></span>|<span data-ttu-id="2cf7d-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-130">Optional attribute.</span></span> <span data-ttu-id="2cf7d-131">Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="2cf7d-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2cf7d-132">Serialization</span></span>|<span data-ttu-id="2cf7d-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-133">Optional attribute.</span></span> <span data-ttu-id="2cf7d-134">Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="2cf7d-135">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="2cf7d-135">Interop</span></span>|<span data-ttu-id="2cf7d-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-136">Optional attribute.</span></span> <span data-ttu-id="2cf7d-137">Başvuru türleri Windows çalışma zamanı ve COM hazırlama denetimlerini İlkesi</span><span class="sxs-lookup"><span data-stu-id="2cf7d-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="2cf7d-138">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="2cf7d-138">Interop</span></span>|<span data-ttu-id="2cf7d-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-139">Optional attribute.</span></span> <span data-ttu-id="2cf7d-140">Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="2cf7d-141">Birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="2cf7d-141">Interop</span></span>|<span data-ttu-id="2cf7d-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-142">Optional attribute.</span></span> <span data-ttu-id="2cf7d-143">Yerel kod yapılara hazırlama için ilke denetler.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="2cf7d-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="2cf7d-144">Name attribute</span></span>  
  
|<span data-ttu-id="2cf7d-145">Değer</span><span class="sxs-lookup"><span data-stu-id="2cf7d-145">Value</span></span>|<span data-ttu-id="2cf7d-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cf7d-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2cf7d-147">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="2cf7d-147">*assembly_name*</span></span>|<span data-ttu-id="2cf7d-148">Derlemenin dosya uzantısı olmadan basit adı.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-148">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="2cf7d-149">Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-149">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2cf7d-150">Örneğin, Extensions.dll adlı bir derleme "Uzantılarla" adıdır.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-150">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span><br /><br /> <span data-ttu-id="2cf7d-151">Değişmez değer dize de belirtebilirsiniz `*Application*` bu derlemeler yüklü olsun olmasın tüm derlemelerde uygulama paketi, ilkeyi uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-151">You can also specify the literal string `*Application*` to apply policy to all assemblies in your app package, whether those assemblies are loaded or not.</span></span> <span data-ttu-id="2cf7d-152">`*Application*` hiç ilke .NET Framework derlemeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-152">`*Application*` never applies policy to .NET Framework assemblies.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="2cf7d-153">Tüm diğer özniteliklerle</span><span class="sxs-lookup"><span data-stu-id="2cf7d-153">All other attributes</span></span>  
  
|<span data-ttu-id="2cf7d-154">Değer</span><span class="sxs-lookup"><span data-stu-id="2cf7d-154">Value</span></span>|<span data-ttu-id="2cf7d-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cf7d-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2cf7d-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="2cf7d-156">*policy_setting*</span></span>|<span data-ttu-id="2cf7d-157">Derleme içindeki tüm türler için bu ilke türü için geçerli ayar.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-157">The setting to apply to this policy type for all types in the assembly.</span></span> <span data-ttu-id="2cf7d-158">Olası değerler şunlardır: `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-158">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="2cf7d-159">Daha fazla bilgi için bkz: [çalışma zamanı yönerge İlkesi ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2cf7d-159">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cf7d-160">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cf7d-160">Child Elements</span></span>  
  
|<span data-ttu-id="2cf7d-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="2cf7d-161">Element</span></span>|<span data-ttu-id="2cf7d-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cf7d-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf7d-163">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="2cf7d-163">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="2cf7d-164">Bir alt ad alanındaki tüm türleri yansıma ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-164">Applies reflection policy to all types in a child namespace.</span></span>|  
|[<span data-ttu-id="2cf7d-165">\<türü ></span><span class="sxs-lookup"><span data-stu-id="2cf7d-165">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="2cf7d-166">Yansıma ilke türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-166">Applies reflection policy to a type.</span></span>|  
|[<span data-ttu-id="2cf7d-167">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="2cf7d-167">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="2cf7d-168">Yansıma ilke oluşturulan genel bir tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-168">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2cf7d-169">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cf7d-169">Parent Elements</span></span>  
  
|<span data-ttu-id="2cf7d-170">Öğe</span><span class="sxs-lookup"><span data-stu-id="2cf7d-170">Element</span></span>|<span data-ttu-id="2cf7d-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cf7d-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf7d-172">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="2cf7d-172">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="2cf7d-173">Uygulama çapında türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-173">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="2cf7d-174">[ \<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi sıfır, bir veya daha fazla olabilir `<Assembly>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-174">The [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element can have zero, one, or more `<Assembly>` elements.</span></span>|  
|[<span data-ttu-id="2cf7d-175">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="2cf7d-175">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="2cf7d-176">Türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir içeren derlemenin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-176">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="2cf7d-177">[ \<Kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğesi sıfır veya bir olabilir `<Assembly>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-177">The [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element can have zero or one `<Assembly>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf7d-178">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cf7d-178">Remarks</span></span>  
 <span data-ttu-id="2cf7d-179">`<Assembly>` Öğesi, bir derlemede tüm türleri için çalışma zamanı İlkesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-179">The `<Assembly>` element defines runtime policy for all the types in an assembly.</span></span> <span data-ttu-id="2cf7d-180">Bu farklı [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) , bir kitaplık belirtiyor, ancak çalışma zamanı yansıma ilkesini tanımlamak için ve alt öğeleri bağımlı öğesi.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-180">It differs from the [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element, which specifies a library but depends on its child elements to define runtime reflection policy.</span></span> <span data-ttu-id="2cf7d-181">`<Assembly>` Öğesi geçerli bir derleme içindeki tüm türler için bir alt öğesi tarafından kılınmadıkça.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-181">The `<Assembly>` element applies to all the types in an assembly unless they are overridden by a child element.</span></span>  
  
 <span data-ttu-id="2cf7d-182">Aşağıdaki örnek, nasıl çalışma zamanı İlkesi derlemeleri içindeki tüm türler uygulama paketinizi içinde atayarak uygulayabileceğiniz gösterir `Name` değerini özniteliği "* uygulama\*".</span><span class="sxs-lookup"><span data-stu-id="2cf7d-182">The following example shows how you can apply runtime policy to all the types in assemblies within your app package by assigning the `Name` attribute a value of "*Application\*".</span></span> <span data-ttu-id="2cf7d-183">`<Assembly>` Öğesi bir alt öğesi olması gerekir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-183">The `<Assembly>` element must be a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 <span data-ttu-id="2cf7d-184">`Activate`, `Browse`, `Dynamic`, Ve `Serialize` öznitelikleri tüm isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-184">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="2cf7d-185">Ancak, `<Assembly>` öğesi bu öznitelikler en az birini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-185">However, the `<Assembly>` element must contain at least one of these attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf7d-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cf7d-186">See Also</span></span>  
 [<span data-ttu-id="2cf7d-187">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="2cf7d-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="2cf7d-188">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2cf7d-188">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="2cf7d-189">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="2cf7d-189">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

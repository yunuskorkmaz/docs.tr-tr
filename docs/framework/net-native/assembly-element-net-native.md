---
description: 'Daha fazla bilgi edinin: <Assembly> öğesi (.NET Native)'
title: <Assembly> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: 567a30a6a77e9de03635a9dfaae6bb28c9d728f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747926"
---
# <a name="assembly-element-net-native"></a><span data-ttu-id="0e0d0-103">\<Assembly> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0e0d0-103">\<Assembly> Element (.NET Native)</span></span>

<span data-ttu-id="0e0d0-104">Belirtilen derlemedeki tüm türlere çalışma zamanı yansıma ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-104">Applies runtime reflection policy to all the types in a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e0d0-105">Syntax</span></span>  
  
```xml  
<Assembly Name="assembly_name"
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting"  
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e0d0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e0d0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0e0d0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e0d0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e0d0-108">Attributes</span></span>  
  
|<span data-ttu-id="0e0d0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e0d0-109">Attribute</span></span>|<span data-ttu-id="0e0d0-110">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="0e0d0-110">Attribute type</span></span>|<span data-ttu-id="0e0d0-111">Description</span><span class="sxs-lookup"><span data-stu-id="0e0d0-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0e0d0-112">Genel</span><span class="sxs-lookup"><span data-stu-id="0e0d0-112">General</span></span>|<span data-ttu-id="0e0d0-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-113">Required attribute.</span></span> <span data-ttu-id="0e0d0-114">Bir derlemenin basit adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-114">Specifies the simple name of an assembly.</span></span>|  
|`Activate`|<span data-ttu-id="0e0d0-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0e0d0-115">Reflection</span></span>|<span data-ttu-id="0e0d0-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-116">Optional attribute.</span></span> <span data-ttu-id="0e0d0-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="0e0d0-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0e0d0-118">Reflection</span></span>|<span data-ttu-id="0e0d0-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-119">Optional attribute.</span></span> <span data-ttu-id="0e0d0-120">Derlemedeki türler hakkında bilgi sorgulamayı veya numaralandırma denetimleri yapar, ancak çalışma zamanında hiçbir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-120">Controls querying for information about or enumerating the types in the assembly, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0e0d0-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0e0d0-121">Reflection</span></span>|<span data-ttu-id="0e0d0-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-122">Optional attribute.</span></span> <span data-ttu-id="0e0d0-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="0e0d0-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e0d0-124">Serialization</span></span>|<span data-ttu-id="0e0d0-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-125">Optional attribute.</span></span> <span data-ttu-id="0e0d0-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="0e0d0-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e0d0-127">Serialization</span></span>|<span data-ttu-id="0e0d0-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-128">Optional attribute.</span></span> <span data-ttu-id="0e0d0-129">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="0e0d0-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e0d0-130">Serialization</span></span>|<span data-ttu-id="0e0d0-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-131">Optional attribute.</span></span> <span data-ttu-id="0e0d0-132">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="0e0d0-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="0e0d0-133">Serialization</span></span>|<span data-ttu-id="0e0d0-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-134">Optional attribute.</span></span> <span data-ttu-id="0e0d0-135">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="0e0d0-136">Interop</span><span class="sxs-lookup"><span data-stu-id="0e0d0-136">Interop</span></span>|<span data-ttu-id="0e0d0-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-137">Optional attribute.</span></span> <span data-ttu-id="0e0d0-138">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="0e0d0-139">Interop</span><span class="sxs-lookup"><span data-stu-id="0e0d0-139">Interop</span></span>|<span data-ttu-id="0e0d0-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-140">Optional attribute.</span></span> <span data-ttu-id="0e0d0-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="0e0d0-142">Interop</span><span class="sxs-lookup"><span data-stu-id="0e0d0-142">Interop</span></span>|<span data-ttu-id="0e0d0-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-143">Optional attribute.</span></span> <span data-ttu-id="0e0d0-144">Yapıları yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-144">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0e0d0-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="0e0d0-145">Name attribute</span></span>  
  
|<span data-ttu-id="0e0d0-146">Değer</span><span class="sxs-lookup"><span data-stu-id="0e0d0-146">Value</span></span>|<span data-ttu-id="0e0d0-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e0d0-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e0d0-148">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="0e0d0-148">*assembly_name*</span></span>|<span data-ttu-id="0e0d0-149">Derlemenin, dosya uzantısı olmadan basit adı.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-149">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="0e0d0-150">Bu öznitelik, özelliğine karşılık gelir <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-150">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0e0d0-151">Örneğin, Extensions.dll adlı bir derlemenin adı "Uzantılar" dır.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-151">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span><br /><br /> <span data-ttu-id="0e0d0-152">Ayrıca, `*Application*` uygulama paketinizdeki tüm derlemelere ilke uygulamak için aynı dizeyi belirtebilir, bu derlemeler yüklenip yüklenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-152">You can also specify the literal string `*Application*` to apply policy to all assemblies in your app package, whether those assemblies are loaded or not.</span></span> <span data-ttu-id="0e0d0-153">`*Application*` ilke .NET Framework derlemelerine hiçbir şekilde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-153">`*Application*` never applies policy to .NET Framework assemblies.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0e0d0-154">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e0d0-154">All other attributes</span></span>  
  
|<span data-ttu-id="0e0d0-155">Değer</span><span class="sxs-lookup"><span data-stu-id="0e0d0-155">Value</span></span>|<span data-ttu-id="0e0d0-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e0d0-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e0d0-157">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0e0d0-157">*policy_setting*</span></span>|<span data-ttu-id="0e0d0-158">Derlemedeki tüm türler için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-158">The setting to apply to this policy type for all types in the assembly.</span></span> <span data-ttu-id="0e0d0-159">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-159">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="0e0d0-160">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0e0d0-160">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e0d0-161">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e0d0-161">Child Elements</span></span>  
  
|<span data-ttu-id="0e0d0-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e0d0-162">Element</span></span>|<span data-ttu-id="0e0d0-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e0d0-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="0e0d0-164">Bir alt ad alanındaki tüm türlere yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-164">Applies reflection policy to all types in a child namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="0e0d0-165">Yansıma ilkesini bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-165">Applies reflection policy to a type.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0e0d0-166">Yansıma ilkesini oluşturulmuş genel bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-166">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e0d0-167">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e0d0-167">Parent Elements</span></span>  
  
|<span data-ttu-id="0e0d0-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e0d0-168">Element</span></span>|<span data-ttu-id="0e0d0-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e0d0-169">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="0e0d0-170">Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-170">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="0e0d0-171">[\<Application>](application-element-net-native.md)Öğesinde sıfır, bir veya daha fazla `<Assembly>` öğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-171">The [\<Application>](application-element-net-native.md) element can have zero, one, or more `<Assembly>` elements.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="0e0d0-172">Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-172">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="0e0d0-173">[\<Library>](library-element-net-native.md)Öğe sıfır veya bir `<Assembly>` öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-173">The [\<Library>](library-element-net-native.md) element can have zero or one `<Assembly>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e0d0-174">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e0d0-174">Remarks</span></span>  

 <span data-ttu-id="0e0d0-175">`<Assembly>`Öğesi bir derlemedeki tüm türler için çalışma zamanı ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-175">The `<Assembly>` element defines runtime policy for all the types in an assembly.</span></span> <span data-ttu-id="0e0d0-176">Bu, [\<Library>](library-element-net-native.md) bir kitaplığı belirten, ancak çalışma zamanı yansıtma ilkesini tanımlamak için alt öğelerine bağımlı olan öğeden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-176">It differs from the [\<Library>](library-element-net-native.md) element, which specifies a library but depends on its child elements to define runtime reflection policy.</span></span> <span data-ttu-id="0e0d0-177">`<Assembly>`Öğesi bir alt öğe tarafından geçersiz kılınmadıkça derlemedeki tüm türlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-177">The `<Assembly>` element applies to all the types in an assembly unless they are overridden by a child element.</span></span>  
  
 <span data-ttu-id="0e0d0-178">Aşağıdaki örnek, `Name` özniteliğini "\* Application" değeri atayarak uygulama paketinizdeki derlemelerdeki tüm türlere çalışma zamanı ilkesini nasıl uygulayacağınızı gösterir \* .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-178">The following example shows how you can apply runtime policy to all the types in assemblies within your app package by assigning the `Name` attribute a value of "\*Application\*".</span></span> <span data-ttu-id="0e0d0-179">`<Assembly>`Öğesi öğesinin bir alt öğesi olmalıdır [\<Application>](application-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0e0d0-179">The `<Assembly>` element must be a child of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 <span data-ttu-id="0e0d0-180">`Activate`,, `Browse` `Dynamic` Ve `Serialize` özniteliklerinin tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-180">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="0e0d0-181">Ancak, `<Assembly>` öğesi bu özniteliklerden en az birini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-181">However, the `<Assembly>` element must contain at least one of these attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0d0-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e0d0-182">See also</span></span>

- [<span data-ttu-id="0e0d0-183">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="0e0d0-183">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="0e0d0-184">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0e0d0-184">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0e0d0-185">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="0e0d0-185">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

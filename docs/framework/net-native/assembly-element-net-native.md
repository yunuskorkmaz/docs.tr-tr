---
title: <Assembly> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: 9d1556d8d414386d3f350a96396381bd7b66ffc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251132"
---
# <a name="assembly-element-net-native"></a><span data-ttu-id="e6853-102">\<Assembly> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e6853-102">\<Assembly> Element (.NET Native)</span></span>

<span data-ttu-id="e6853-103">Belirtilen derlemedeki tüm türlere çalışma zamanı yansıma ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="e6853-103">Applies runtime reflection policy to all the types in a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6853-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6853-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6853-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6853-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e6853-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6853-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6853-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6853-107">Attributes</span></span>  
  
|<span data-ttu-id="e6853-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6853-108">Attribute</span></span>|<span data-ttu-id="e6853-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="e6853-109">Attribute type</span></span>|<span data-ttu-id="e6853-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6853-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e6853-111">Genel</span><span class="sxs-lookup"><span data-stu-id="e6853-111">General</span></span>|<span data-ttu-id="e6853-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-112">Required attribute.</span></span> <span data-ttu-id="e6853-113">Bir derlemenin basit adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6853-113">Specifies the simple name of an assembly.</span></span>|  
|`Activate`|<span data-ttu-id="e6853-114">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e6853-114">Reflection</span></span>|<span data-ttu-id="e6853-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-115">Optional attribute.</span></span> <span data-ttu-id="e6853-116">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6853-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="e6853-117">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e6853-117">Reflection</span></span>|<span data-ttu-id="e6853-118">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-118">Optional attribute.</span></span> <span data-ttu-id="e6853-119">Derlemedeki türler hakkında bilgi sorgulamayı veya numaralandırma denetimleri yapar, ancak çalışma zamanında hiçbir dinamik erişimi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="e6853-119">Controls querying for information about or enumerating the types in the assembly, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e6853-120">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e6853-120">Reflection</span></span>|<span data-ttu-id="e6853-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-121">Optional attribute.</span></span> <span data-ttu-id="e6853-122">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6853-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="e6853-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e6853-123">Serialization</span></span>|<span data-ttu-id="e6853-124">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-124">Optional attribute.</span></span> <span data-ttu-id="e6853-125">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6853-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="e6853-126">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e6853-126">Serialization</span></span>|<span data-ttu-id="e6853-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-127">Optional attribute.</span></span> <span data-ttu-id="e6853-128">Sınıfını kullanan serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6853-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="e6853-129">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e6853-129">Serialization</span></span>|<span data-ttu-id="e6853-130">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-130">Optional attribute.</span></span> <span data-ttu-id="e6853-131">Sınıfını kullanan JSON serileştirme için ilkeyi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6853-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="e6853-132">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e6853-132">Serialization</span></span>|<span data-ttu-id="e6853-133">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-133">Optional attribute.</span></span> <span data-ttu-id="e6853-134">Sınıfını kullanan XML serileştirme ilkesini denetler <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6853-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="e6853-135">Interop</span><span class="sxs-lookup"><span data-stu-id="e6853-135">Interop</span></span>|<span data-ttu-id="e6853-136">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-136">Optional attribute.</span></span> <span data-ttu-id="e6853-137">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6853-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="e6853-138">Interop</span><span class="sxs-lookup"><span data-stu-id="e6853-138">Interop</span></span>|<span data-ttu-id="e6853-139">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-139">Optional attribute.</span></span> <span data-ttu-id="e6853-140">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6853-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="e6853-141">Interop</span><span class="sxs-lookup"><span data-stu-id="e6853-141">Interop</span></span>|<span data-ttu-id="e6853-142">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6853-142">Optional attribute.</span></span> <span data-ttu-id="e6853-143">Yapıları yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6853-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e6853-144">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="e6853-144">Name attribute</span></span>  
  
|<span data-ttu-id="e6853-145">Değer</span><span class="sxs-lookup"><span data-stu-id="e6853-145">Value</span></span>|<span data-ttu-id="e6853-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6853-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6853-147">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="e6853-147">*assembly_name*</span></span>|<span data-ttu-id="e6853-148">Derlemenin, dosya uzantısı olmadan basit adı.</span><span class="sxs-lookup"><span data-stu-id="e6853-148">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="e6853-149">Bu öznitelik, özelliğine karşılık gelir <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6853-149">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e6853-150">Örneğin, Extensions.dll adlı bir derlemenin adı "Uzantılar" dır.</span><span class="sxs-lookup"><span data-stu-id="e6853-150">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span><br /><br /> <span data-ttu-id="e6853-151">Ayrıca, `*Application*` uygulama paketinizdeki tüm derlemelere ilke uygulamak için aynı dizeyi belirtebilir, bu derlemeler yüklenip yüklenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e6853-151">You can also specify the literal string `*Application*` to apply policy to all assemblies in your app package, whether those assemblies are loaded or not.</span></span> <span data-ttu-id="e6853-152">`*Application*` ilke .NET Framework derlemelerine hiçbir şekilde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="e6853-152">`*Application*` never applies policy to .NET Framework assemblies.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e6853-153">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6853-153">All other attributes</span></span>  
  
|<span data-ttu-id="e6853-154">Değer</span><span class="sxs-lookup"><span data-stu-id="e6853-154">Value</span></span>|<span data-ttu-id="e6853-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6853-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6853-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e6853-156">*policy_setting*</span></span>|<span data-ttu-id="e6853-157">Derlemedeki tüm türler için bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="e6853-157">The setting to apply to this policy type for all types in the assembly.</span></span> <span data-ttu-id="e6853-158">Olası değerler şunlardır,,,,,, `All` `Auto` `Excluded` `Public` `PublicAndInternal` `Required Public` `Required PublicAndInternal` ve `Required All` .</span><span class="sxs-lookup"><span data-stu-id="e6853-158">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e6853-159">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e6853-159">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6853-160">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6853-160">Child Elements</span></span>  
  
|<span data-ttu-id="e6853-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6853-161">Element</span></span>|<span data-ttu-id="e6853-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6853-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="e6853-163">Bir alt ad alanındaki tüm türlere yansıma ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="e6853-163">Applies reflection policy to all types in a child namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="e6853-164">Yansıma ilkesini bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="e6853-164">Applies reflection policy to a type.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e6853-165">Yansıma ilkesini oluşturulmuş genel bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="e6853-165">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6853-166">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6853-166">Parent Elements</span></span>  
  
|<span data-ttu-id="e6853-167">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6853-167">Element</span></span>|<span data-ttu-id="e6853-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6853-168">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="e6853-169">Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.</span><span class="sxs-lookup"><span data-stu-id="e6853-169">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="e6853-170">[\<Application>](application-element-net-native.md)Öğesinde sıfır, bir veya daha fazla `<Assembly>` öğe olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6853-170">The [\<Application>](application-element-net-native.md) element can have zero, one, or more `<Assembly>` elements.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="e6853-171">Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6853-171">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="e6853-172">[\<Library>](library-element-net-native.md)Öğe sıfır veya bir `<Assembly>` öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e6853-172">The [\<Library>](library-element-net-native.md) element can have zero or one `<Assembly>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6853-173">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6853-173">Remarks</span></span>  

 <span data-ttu-id="e6853-174">`<Assembly>`Öğesi bir derlemedeki tüm türler için çalışma zamanı ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6853-174">The `<Assembly>` element defines runtime policy for all the types in an assembly.</span></span> <span data-ttu-id="e6853-175">Bu, [\<Library>](library-element-net-native.md) bir kitaplığı belirten, ancak çalışma zamanı yansıtma ilkesini tanımlamak için alt öğelerine bağımlı olan öğeden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e6853-175">It differs from the [\<Library>](library-element-net-native.md) element, which specifies a library but depends on its child elements to define runtime reflection policy.</span></span> <span data-ttu-id="e6853-176">`<Assembly>`Öğesi bir alt öğe tarafından geçersiz kılınmadıkça derlemedeki tüm türlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e6853-176">The `<Assembly>` element applies to all the types in an assembly unless they are overridden by a child element.</span></span>  
  
 <span data-ttu-id="e6853-177">Aşağıdaki örnek, `Name` özniteliğini "\* Application" değeri atayarak uygulama paketinizdeki derlemelerdeki tüm türlere çalışma zamanı ilkesini nasıl uygulayacağınızı gösterir \* .</span><span class="sxs-lookup"><span data-stu-id="e6853-177">The following example shows how you can apply runtime policy to all the types in assemblies within your app package by assigning the `Name` attribute a value of "\*Application\*".</span></span> <span data-ttu-id="e6853-178">`<Assembly>`Öğesi öğesinin bir alt öğesi olmalıdır [\<Application>](application-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="e6853-178">The `<Assembly>` element must be a child of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 <span data-ttu-id="e6853-179">`Activate`,, `Browse` `Dynamic` Ve `Serialize` özniteliklerinin tümü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6853-179">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="e6853-180">Ancak, `<Assembly>` öğesi bu özniteliklerden en az birini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="e6853-180">However, the `<Assembly>` element must contain at least one of these attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6853-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6853-181">See also</span></span>

- [<span data-ttu-id="e6853-182">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="e6853-182">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="e6853-183">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e6853-183">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e6853-184">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="e6853-184">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

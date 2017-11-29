---
title: "&lt;Library&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b93335d0d5d1524c9a0b955d1ea279be8c0f243
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlibrarygt-element-net-native"></a><span data-ttu-id="26d46-102">&lt;Library&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="26d46-102">&lt;Library&gt; Element (.NET Native)</span></span>
<span data-ttu-id="26d46-103">Türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir içeren derlemenin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26d46-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="26d46-104">\<Yönergeleri > öğesi</span><span class="sxs-lookup"><span data-stu-id="26d46-104">\<Directives> Element</span></span>  
<span data-ttu-id="26d46-105">\<Kitaplık > öğesi</span><span class="sxs-lookup"><span data-stu-id="26d46-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d46-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26d46-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26d46-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26d46-107">Attributes and Elements</span></span>  
 <span data-ttu-id="26d46-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26d46-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26d46-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26d46-109">Attributes</span></span>  
  
|<span data-ttu-id="26d46-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26d46-110">Attribute</span></span>|<span data-ttu-id="26d46-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26d46-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="26d46-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="26d46-112">Required attribute.</span></span> <span data-ttu-id="26d46-113">Bir bütünleştirilmiş kodun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="26d46-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="26d46-114">Bu alt öğelerinin `<Library>` öğesi türleri ve bu derleme içinde bulunan tür üyeleri için çalışma zamanı yansıma ilkesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="26d46-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="26d46-115">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="26d46-115">Name attribute</span></span>  
  
|<span data-ttu-id="26d46-116">Değer</span><span class="sxs-lookup"><span data-stu-id="26d46-116">Value</span></span>|<span data-ttu-id="26d46-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26d46-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26d46-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="26d46-118">*assembly_name*</span></span>|<span data-ttu-id="26d46-119">Derlemenin dosya uzantısı olmadan basit adı.</span><span class="sxs-lookup"><span data-stu-id="26d46-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="26d46-120">Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="26d46-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="26d46-121">Örneğin, Extensions.dll adlı bir derleme "Uzantılarla" adıdır.</span><span class="sxs-lookup"><span data-stu-id="26d46-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="26d46-122">Özel bir tür için Açıklamalar bölümüne bakın *assembly_name* koşullu derleme meta verilerini edilmesi destekler.</span><span class="sxs-lookup"><span data-stu-id="26d46-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26d46-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26d46-123">Child Elements</span></span>  
  
|<span data-ttu-id="26d46-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="26d46-124">Element</span></span>|<span data-ttu-id="26d46-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26d46-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26d46-126">\<Derleme ></span><span class="sxs-lookup"><span data-stu-id="26d46-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="26d46-127">Belirli bir derleme içindeki tüm türler için ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="26d46-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="26d46-128">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="26d46-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="26d46-129">Belirli bir ad alanı içindeki tüm türler için ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="26d46-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="26d46-130">\<Türü ></span><span class="sxs-lookup"><span data-stu-id="26d46-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="26d46-131">Bir sınıf veya yapı gibi belirli türde bir ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="26d46-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="26d46-132">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="26d46-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="26d46-133">İlke oluşturulan genel bir tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="26d46-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="26d46-134">Örneğin, bir [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi için ilke tanımlamak için kullanılan bir `List<String>` türü.</span><span class="sxs-lookup"><span data-stu-id="26d46-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26d46-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26d46-135">Parent Elements</span></span>  
  
|<span data-ttu-id="26d46-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="26d46-136">Element</span></span>|<span data-ttu-id="26d46-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26d46-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26d46-138">\<Yönergeleri ></span><span class="sxs-lookup"><span data-stu-id="26d46-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="26d46-139">Bir çalışma zamanı yönergeleri dosyasının kök öğesinin.</span><span class="sxs-lookup"><span data-stu-id="26d46-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26d46-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26d46-140">Remarks</span></span>  
 <span data-ttu-id="26d46-141">[ \<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) sıfır, bir veya daha fazla öğe içerebilir `<Library>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="26d46-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="26d46-142">`<Library>` Olan meta veri çalışma zamanında gereken program öğeleri tanımlamak için bir kapsayıcı öğe görür; bu öğe ilkesini ifade değil.</span><span class="sxs-lookup"><span data-stu-id="26d46-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="26d46-143">Derleme zamanında arama derleyici araçları yalnızca belirlenen kitaplık `<Library>` öğesi alt öğeleri tarafından tanıtılan program öğeleri için.</span><span class="sxs-lookup"><span data-stu-id="26d46-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="26d46-144">Buna karşılık, derleyici arama araçları tüm kitaplıkları, alt öğeleri tarafından tanımlanan programı öğelerin including.NET Framework core kitaplıkları [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="26d46-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="26d46-145">`<Library>`yönergeleri koşullu yararlı.</span><span class="sxs-lookup"><span data-stu-id="26d46-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="26d46-146">Varsa adını `<Library>` öğesi başlar ve biter yıldız işareti (*) ile `<Library>` yönergesi yalnızca yıldız arasında belirtilen derlemesi uygulama tarafından başvurulduğunda bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="26d46-146">If the name of the `<Library>` element starts and ends with an asterisk (*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="26d46-147">Örneğin, yalnızca Utillities.dll derleme uygulama tarafından başvurulduğunda aşağıdaki çalışma zamanı yönerge geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="26d46-147">For example, the following runtime directive applies only if the Utillities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26d46-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26d46-148">See Also</span></span>  
 [<span data-ttu-id="26d46-149">\<Uygulama > öğesi</span><span class="sxs-lookup"><span data-stu-id="26d46-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 [<span data-ttu-id="26d46-150">\<Yönergeleri > öğesi</span><span class="sxs-lookup"><span data-stu-id="26d46-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 [<span data-ttu-id="26d46-151">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="26d46-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="26d46-152">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="26d46-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

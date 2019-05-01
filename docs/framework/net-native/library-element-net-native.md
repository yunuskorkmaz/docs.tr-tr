---
title: <Library> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda4f8d3819af05b022e0633d6883cca940f67e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866870"
---
# <a name="library-element-net-native"></a><span data-ttu-id="56578-102">\<Kitaplık > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="56578-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="56578-103">Türler ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir içeren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56578-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="56578-104">\<Yönergeleri > öğesi</span><span class="sxs-lookup"><span data-stu-id="56578-104">\<Directives> Element</span></span>  
<span data-ttu-id="56578-105">\<Kitaplık > öğesi</span><span class="sxs-lookup"><span data-stu-id="56578-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56578-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56578-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56578-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="56578-107">Attributes and Elements</span></span>  
 <span data-ttu-id="56578-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56578-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56578-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56578-109">Attributes</span></span>  
  
|<span data-ttu-id="56578-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="56578-110">Attribute</span></span>|<span data-ttu-id="56578-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56578-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="56578-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="56578-112">Required attribute.</span></span> <span data-ttu-id="56578-113">Bir derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="56578-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="56578-114">Alt öğelerinin bu `<Library>` öğesi türleri ve bu derlemede bulunan tür üyeleri için çalışma zamanı yansıma ilkesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="56578-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="56578-115">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="56578-115">Name attribute</span></span>  
  
|<span data-ttu-id="56578-116">Değer</span><span class="sxs-lookup"><span data-stu-id="56578-116">Value</span></span>|<span data-ttu-id="56578-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56578-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56578-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="56578-118">*assembly_name*</span></span>|<span data-ttu-id="56578-119">Dosya uzantısı olmadan derlemenin basit adını.</span><span class="sxs-lookup"><span data-stu-id="56578-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="56578-120">Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="56578-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="56578-121">Örneğin, Extensions.dll adlı bir derleme adı "Uzantıları" dir.</span><span class="sxs-lookup"><span data-stu-id="56578-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="56578-122">Özel için Açıklamalar bölümüne bakın *assembly_name* , koşullu dahil etme derlemesinden meta verileri destekler.</span><span class="sxs-lookup"><span data-stu-id="56578-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56578-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="56578-123">Child Elements</span></span>  
  
|<span data-ttu-id="56578-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="56578-124">Element</span></span>|<span data-ttu-id="56578-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56578-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56578-126">\<Derleme ></span><span class="sxs-lookup"><span data-stu-id="56578-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="56578-127">İlke, belirli bir derlemedeki tüm türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="56578-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="56578-128">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="56578-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="56578-129">İlke, belirli bir ad alanındaki tüm türlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="56578-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="56578-130">\<türü ></span><span class="sxs-lookup"><span data-stu-id="56578-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="56578-131">İlke, bir sınıf veya yapı gibi belirli bir türe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="56578-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="56578-132">\<Typeınstantiation ></span><span class="sxs-lookup"><span data-stu-id="56578-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="56578-133">İlke oluşturulmuş bir genel türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="56578-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="56578-134">Örneğin, bir [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi için ilke tanımlamak için kullanılabilir bir `List<String>` türü.</span><span class="sxs-lookup"><span data-stu-id="56578-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56578-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="56578-135">Parent Elements</span></span>  
  
|<span data-ttu-id="56578-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="56578-136">Element</span></span>|<span data-ttu-id="56578-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56578-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56578-138">\<Yönergeleri ></span><span class="sxs-lookup"><span data-stu-id="56578-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="56578-139">Bir çalışma zamanı yönergeleri dosyasının kök öğe.</span><span class="sxs-lookup"><span data-stu-id="56578-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56578-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56578-140">Remarks</span></span>  
 <span data-ttu-id="56578-141">[ \<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) sıfır, bir veya daha fazla öğe içerebilir `<Library>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="56578-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="56578-142">`<Library>` Olan meta verileri çalışma zamanında gereken program öğeleri tanımlamak için bir kapsayıcı öğe görür; bu öğe ilkesini ifade etmez.</span><span class="sxs-lookup"><span data-stu-id="56578-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="56578-143">Derleme zamanında derleyici araçları yalnızca belirlenen kitaplık arama `<Library>` program öğeleri alt öğeleri tarafından tanımlanan öğe.</span><span class="sxs-lookup"><span data-stu-id="56578-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="56578-144">Buna karşılık, derleyici arama araçları tüm kitaplıkları, alt öğeler tarafından tanıtılan program öğeler için including.NET Framework Çekirdek kitaplıkları [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="56578-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="56578-145">`<Library>` yönergeleri koşullu olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56578-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="56578-146">Varsa adını `<Library>` öğesi başlar ve biter yıldız işaretiyle (\*), `<Library>` yönergesi, yalnızca uygulama tarafından arasında yıldız belirtilen derleme başvuruluyorsa bir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="56578-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="56578-147">Örneğin, yalnızca, uygulama tarafından Utillities.dll derlemeye başvurulduğundan durumunda aşağıdaki çalışma zamanı yönerge geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="56578-147">For example, the following runtime directive applies only if the Utillities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56578-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56578-148">See also</span></span>

- [<span data-ttu-id="56578-149">\<Uygulama > öğesi</span><span class="sxs-lookup"><span data-stu-id="56578-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)
- [<span data-ttu-id="56578-150">\<Yönergeleri > öğesi</span><span class="sxs-lookup"><span data-stu-id="56578-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)
- [<span data-ttu-id="56578-151">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="56578-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="56578-152">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="56578-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)

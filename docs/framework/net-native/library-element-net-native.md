---
title: <Library>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128365"
---
# <a name="library-element-net-native"></a><span data-ttu-id="0e784-102">\<Library>Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0e784-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="0e784-103">Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e784-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="0e784-104">\<Directives> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0e784-104">\<Directives> Element</span></span>  
<span data-ttu-id="0e784-105">\<Library> Öğesi</span><span class="sxs-lookup"><span data-stu-id="0e784-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e784-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e784-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e784-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e784-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0e784-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e784-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e784-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e784-109">Attributes</span></span>  
  
|<span data-ttu-id="0e784-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e784-110">Attribute</span></span>|<span data-ttu-id="0e784-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e784-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="0e784-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e784-112">Required attribute.</span></span> <span data-ttu-id="0e784-113">Bir derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e784-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="0e784-114">Bu öğenin alt öğeleri `<Library>` , bu derlemede bulunan türler ve tür üyeleri için çalışma zamanı yansıtma ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e784-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0e784-115">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="0e784-115">Name attribute</span></span>  
  
|<span data-ttu-id="0e784-116">Değer</span><span class="sxs-lookup"><span data-stu-id="0e784-116">Value</span></span>|<span data-ttu-id="0e784-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e784-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e784-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="0e784-118">*assembly_name*</span></span>|<span data-ttu-id="0e784-119">Derlemenin, dosya uzantısı olmadan basit adı.</span><span class="sxs-lookup"><span data-stu-id="0e784-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="0e784-120">Bu öznitelik, özelliğine karşılık gelir <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e784-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0e784-121">Örneğin, Extensions. dll adlı bir derlemenin adı "Uzantılar" dır.</span><span class="sxs-lookup"><span data-stu-id="0e784-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="0e784-122">Derlemeden meta verilerin koşullu eklenmesini destekleyen *assembly_name* özel bir biçimi için açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0e784-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e784-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e784-123">Child Elements</span></span>  
  
|<span data-ttu-id="0e784-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e784-124">Element</span></span>|<span data-ttu-id="0e784-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e784-125">Description</span></span>|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="0e784-126">İlkeyi belirli bir derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="0e784-126">Applies policy to all the types in a particular assembly.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="0e784-127">İlkeyi belirli bir ad alanındaki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="0e784-127">Applies policy to all the types in a particular namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="0e784-128">İlkeyi sınıf veya yapı gibi belirli bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="0e784-128">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0e784-129">İlkeyi oluşturulan genel bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="0e784-129">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="0e784-130">Örneğin, bir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) öğe bir tür için ilke tanımlamak üzere kullanılabilir `List<String>` .</span><span class="sxs-lookup"><span data-stu-id="0e784-130">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e784-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e784-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0e784-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e784-132">Element</span></span>|<span data-ttu-id="0e784-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e784-133">Description</span></span>|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|<span data-ttu-id="0e784-134">Çalışma zamanı yönergeleri dosyasının kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="0e784-134">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e784-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e784-135">Remarks</span></span>  
 <span data-ttu-id="0e784-136">[\<Directives>](directives-element-net-native.md)Öğesi sıfır, bir veya daha fazla `<Library>` öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0e784-136">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="0e784-137">`<Library>`Öğesi, meta verileri çalışma zamanında gerekli olan program öğelerini tanımlamak için bir kapsayıcı görevi görür; bu öğe, ilkeyi ifade etmez.</span><span class="sxs-lookup"><span data-stu-id="0e784-137">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="0e784-138">Derleme zamanında, derleyici araçları yalnızca `<Library>` kendi alt öğeleri tarafından tanımlanan program öğeleri için öğesi tarafından belirlenen kitaplığı arar.</span><span class="sxs-lookup"><span data-stu-id="0e784-138">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="0e784-139">Buna karşılık, derleyici araçları, öğesinin alt öğeleri tarafından tanımlanan program öğeleri için tüm kitaplıkları, including.NET Framework Çekirdek kitaplıklarını arar [\<Application>](application-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0e784-139">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="0e784-140">`<Library>`yönergeler koşullu olarak kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e784-140">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="0e784-141">`<Library>`Öğenin adı bir yıldız işaretiyle başlıyorsa ve bitiyorsa \* , `<Library>` yönerge yalnızca yıldız işaretleri arasında belirtilen derlemeye uygulama tarafından başvuruluyorsa bir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0e784-141">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="0e784-142">Örneğin, aşağıdaki çalışma zamanı yönergesi yalnızca uygulama tarafından Utilities. dll derlemesine başvuruluyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0e784-142">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e784-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e784-143">See also</span></span>

- [<span data-ttu-id="0e784-144">\<Application>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="0e784-144">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="0e784-145">\<Directives>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="0e784-145">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="0e784-146">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0e784-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0e784-147">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="0e784-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

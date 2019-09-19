---
title: <Library>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049642"
---
# <a name="library-element-net-native"></a><span data-ttu-id="a806b-102">\<Kitaplık > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="a806b-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="a806b-103">Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a806b-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="a806b-104">\<Yönergeler > öğesi</span><span class="sxs-lookup"><span data-stu-id="a806b-104">\<Directives> Element</span></span>  
<span data-ttu-id="a806b-105">\<Kitaplık > öğesi</span><span class="sxs-lookup"><span data-stu-id="a806b-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a806b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a806b-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a806b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a806b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a806b-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a806b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a806b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a806b-109">Attributes</span></span>  
  
|<span data-ttu-id="a806b-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a806b-110">Attribute</span></span>|<span data-ttu-id="a806b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a806b-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="a806b-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a806b-112">Required attribute.</span></span> <span data-ttu-id="a806b-113">Bir derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a806b-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="a806b-114">Bu `<Library>` öğenin alt öğeleri, bu derlemede bulunan türler ve tür üyeleri için çalışma zamanı yansıtma ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a806b-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="a806b-115">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="a806b-115">Name attribute</span></span>  
  
|<span data-ttu-id="a806b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="a806b-116">Value</span></span>|<span data-ttu-id="a806b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a806b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a806b-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="a806b-118">*assembly_name*</span></span>|<span data-ttu-id="a806b-119">Derlemenin, dosya uzantısı olmadan basit adı.</span><span class="sxs-lookup"><span data-stu-id="a806b-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="a806b-120">Bu öznitelik, <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a806b-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a806b-121">Örneğin, Extensions. dll adlı bir derlemenin adı "Uzantılar" dır.</span><span class="sxs-lookup"><span data-stu-id="a806b-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="a806b-122">Derlemeden meta verilerin koşullu eklenmesini destekleyen özel bir *assembly_name* formu için açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a806b-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a806b-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a806b-123">Child Elements</span></span>  
  
|<span data-ttu-id="a806b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a806b-124">Element</span></span>|<span data-ttu-id="a806b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a806b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a806b-126">\<Bütünleştirilmiş kod ></span><span class="sxs-lookup"><span data-stu-id="a806b-126">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="a806b-127">İlkeyi belirli bir derlemedeki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="a806b-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="a806b-128">\<Ad alanı ></span><span class="sxs-lookup"><span data-stu-id="a806b-128">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="a806b-129">İlkeyi belirli bir ad alanındaki tüm türlere uygular.</span><span class="sxs-lookup"><span data-stu-id="a806b-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="a806b-130">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="a806b-130">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="a806b-131">İlkeyi sınıf veya yapı gibi belirli bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="a806b-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="a806b-132">\<Typeörneklemesi ></span><span class="sxs-lookup"><span data-stu-id="a806b-132">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="a806b-133">İlkeyi oluşturulan genel bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="a806b-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="a806b-134">Örneğin, [ \<](typeinstantiation-element-net-native.md) bir`List<String>` tür için ilke tanımlamak üzere bir typeörneklemesi > öğesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a806b-134">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a806b-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a806b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a806b-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="a806b-136">Element</span></span>|<span data-ttu-id="a806b-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a806b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a806b-138">\<Yönergeler ></span><span class="sxs-lookup"><span data-stu-id="a806b-138">\<Directives></span></span>](directives-element-net-native.md)|<span data-ttu-id="a806b-139">Çalışma zamanı yönergeleri dosyasının kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a806b-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a806b-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a806b-140">Remarks</span></span>  
 <span data-ttu-id="a806b-141">Yönergeler > öğesi sıfır, bir veya daha fazla `<Library>` öğe içerebilir. [ \<](directives-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="a806b-141">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="a806b-142">Öğesi `<Library>` , meta verileri çalışma zamanında gerekli olan program öğelerini tanımlamak için bir kapsayıcı görevi görür; bu öğe, ilkeyi ifade etmez.</span><span class="sxs-lookup"><span data-stu-id="a806b-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="a806b-143">Derleme zamanında, derleyici araçları yalnızca kendi alt öğeleri tarafından tanımlanan program öğeleri `<Library>` için öğesi tarafından belirlenen kitaplığı arar.</span><span class="sxs-lookup"><span data-stu-id="a806b-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="a806b-144">Buna karşılık, derleyici araçları, [ \<uygulama >](application-element-net-native.md) öğesinin alt öğeleri tarafından tanımlanan program öğeleri için tüm kitaplıkları, including.NET Framework Çekirdek kitaplıklarını arar.</span><span class="sxs-lookup"><span data-stu-id="a806b-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="a806b-145">`<Library>`yönergeler koşullu olarak kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a806b-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="a806b-146">`<Library>` Öğenin adı bir\*yıldız işaretiyle başlıyorsa ve bitiyorsa, `<Library>` yönerge yalnızca yıldız işaretleri arasında belirtilen derlemeye uygulama tarafından başvuruluyorsa bir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a806b-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="a806b-147">Örneğin, aşağıdaki çalışma zamanı yönergesi yalnızca uygulama tarafından Utilities. dll derlemesine başvuruluyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a806b-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a806b-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a806b-148">See also</span></span>

- [<span data-ttu-id="a806b-149">\<Uygulama > öğesi</span><span class="sxs-lookup"><span data-stu-id="a806b-149">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="a806b-150">\<Yönergeler > öğesi</span><span class="sxs-lookup"><span data-stu-id="a806b-150">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="a806b-151">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a806b-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="a806b-152">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="a806b-152">Runtime Directive Elements</span></span>](runtime-directive-elements.md)

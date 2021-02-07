---
description: 'İçin: öğesi hakkında daha fazla bilgi <assemblyIdentity><runtime>'
title: <runtime> için <assemblyIdentity> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: d53c4f7f5207fbcf9ad4a8f82667eacc1f57f5e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719194"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="7ccfc-103">\<runtime> için \<assemblyIdentity> Öğesi</span><span class="sxs-lookup"><span data-stu-id="7ccfc-103">\<assemblyIdentity> Element for \<runtime></span></span>

<span data-ttu-id="7ccfc-104">Derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-104">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="7ccfc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ccfc-105">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ccfc-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ccfc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7ccfc-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ccfc-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7ccfc-108">Attributes</span></span>  
  
|<span data-ttu-id="7ccfc-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7ccfc-109">Attribute</span></span>|<span data-ttu-id="7ccfc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ccfc-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="7ccfc-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7ccfc-112">Derlemenin adı</span><span class="sxs-lookup"><span data-stu-id="7ccfc-112">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="7ccfc-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7ccfc-114">Derlemenin dil ve ülke/bölge bilgisini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-114">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="7ccfc-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7ccfc-116">Derlemenin tanımlayıcı adını belirten onaltılık bir değer.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-116">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="7ccfc-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7ccfc-118">"X86", "amd64", "MSIL" veya "ia64" değerlerinden biri, işlemciye özgü kod içeren bir derlemenin işlemci mimarisini belirleyen.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-118">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="7ccfc-119">Değerler büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-119">The values are not case-sensitive.</span></span> <span data-ttu-id="7ccfc-120">Özniteliği başka bir değer atanırsa, tüm `<assemblyIdentity>` öğesi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-120">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="7ccfc-121">Bkz. <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-121">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="7ccfc-122">processorArchitecture özniteliği</span><span class="sxs-lookup"><span data-stu-id="7ccfc-122">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="7ccfc-123">Değer</span><span class="sxs-lookup"><span data-stu-id="7ccfc-123">Value</span></span>|<span data-ttu-id="7ccfc-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ccfc-124">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="7ccfc-125">Yalnızca AMD x86-64 mimarisi.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-125">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="7ccfc-126">Yalnızca Intel Itanium mimarisi.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-126">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="7ccfc-127">İşlemci ve sözcüğe göre bit başına açısından nötr.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-127">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="7ccfc-128">64 bit platformda yerel veya Windows üzerinde Windows (WOW) ortamındaki 32 bitlik bir x86 işlemcisi.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-128">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ccfc-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ccfc-129">Child Elements</span></span>  

 <span data-ttu-id="7ccfc-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ccfc-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ccfc-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7ccfc-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ccfc-132">Element</span></span>|<span data-ttu-id="7ccfc-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ccfc-133">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="7ccfc-134">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-134">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="7ccfc-135">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="7ccfc-136">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-136">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="7ccfc-137">`<dependentAssembly>`Her derleme için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-137">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="7ccfc-138">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-138">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ccfc-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ccfc-139">Remarks</span></span>  

 <span data-ttu-id="7ccfc-140">Her **\<dependentAssembly>** öğenin bir **\<assemblyIdentity>** alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-140">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="7ccfc-141">`processorArchitecture`Öznitelik varsa, `<assemblyIdentity>` öğe yalnızca karşılık gelen işlemci mimarisine sahip derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-141">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="7ccfc-142">`processorArchitecture`Özniteliği yoksa, `<assemblyIdentity>` öğesi herhangi bir işlemci mimarisine sahip bir derleme için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-142">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="7ccfc-143">Aşağıdaki örnek, iki farklı iki işlemci mimarisinden oluşan aynı ada sahip iki derleme için bir yapılandırma dosyası gösterir ve sürümleri eşitlenmiş olarak korunmaz. Uygulama x86 platformunda yürütüldüğünde ilk `<assemblyIdentity>` öğe uygulanır ve diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-143">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="7ccfc-144">Uygulama, x86 veya ia64 dışında bir platformda yürütülüyorsa her ikisi de yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-144">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="7ccfc-145">Bir yapılandırma dosyası özniteliği olmayan bir `<assemblyIdentity>` öğe içeriyorsa `processorArchitecture` ve platformla eşleşen bir öğe içermiyorsa, özniteliği olmayan öğesi `processorArchitecture` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-145">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ccfc-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ccfc-146">Example</span></span>  

 <span data-ttu-id="7ccfc-147">Aşağıdaki örnek, bir derleme hakkında nasıl bilgi sağlayagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-147">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ccfc-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ccfc-148">See also</span></span>

- [<span data-ttu-id="7ccfc-149">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="7ccfc-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7ccfc-150">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7ccfc-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7ccfc-151">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="7ccfc-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)

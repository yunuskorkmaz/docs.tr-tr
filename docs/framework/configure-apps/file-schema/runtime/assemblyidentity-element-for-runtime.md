---
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
ms.openlocfilehash: 815e1c26a328d986f91992a1e67e438a563ffea6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663896"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="c0a6f-102">\<çalışma zamanı için \<assemblyIdentity > öğesi ></span><span class="sxs-lookup"><span data-stu-id="c0a6f-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="c0a6f-103">Derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="c0a6f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="c0a6f-104">\<configuration></span></span>  
<span data-ttu-id="c0a6f-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="c0a6f-105">\<runtime></span></span>  
<span data-ttu-id="c0a6f-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="c0a6f-106">\<assemblyBinding></span></span>  
<span data-ttu-id="c0a6f-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="c0a6f-107">\<dependentAssembly></span></span>  
<span data-ttu-id="c0a6f-108">\<AssemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="c0a6f-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a6f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0a6f-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0a6f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0a6f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0a6f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0a6f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0a6f-112">Attributes</span></span>  
  
|<span data-ttu-id="c0a6f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c0a6f-113">Attribute</span></span>|<span data-ttu-id="c0a6f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0a6f-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c0a6f-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0a6f-116">Derlemenin adı</span><span class="sxs-lookup"><span data-stu-id="c0a6f-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="c0a6f-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c0a6f-118">Derlemenin dil ve ülke/bölge bilgisini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="c0a6f-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c0a6f-120">Derlemenin tanımlayıcı adını belirten onaltılık bir değer.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="c0a6f-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c0a6f-122">"X86", "amd64", "MSIL" veya "ia64" değerlerinden biri, işlemciye özgü kod içeren bir derlemenin işlemci mimarisini belirleyen.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="c0a6f-123">Değerler büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-123">The values are not case-sensitive.</span></span> <span data-ttu-id="c0a6f-124">Özniteliği başka bir değer atanırsa, tüm `<assemblyIdentity>` öğesi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="c0a6f-125">Bkz. <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="c0a6f-126">processorArchitecture özniteliği</span><span class="sxs-lookup"><span data-stu-id="c0a6f-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="c0a6f-127">Değer</span><span class="sxs-lookup"><span data-stu-id="c0a6f-127">Value</span></span>|<span data-ttu-id="c0a6f-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0a6f-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="c0a6f-129">Yalnızca AMD x86-64 mimarisi.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="c0a6f-130">Yalnızca Intel Itanium mimarisi.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="c0a6f-131">İşlemci ve sözcüğe göre bit başına açısından nötr.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="c0a6f-132">64 bit platformda yerel veya Windows üzerinde Windows (WOW) ortamındaki 32 bitlik bir x86 işlemcisi.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0a6f-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0a6f-133">Child Elements</span></span>  
 <span data-ttu-id="c0a6f-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0a6f-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0a6f-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c0a6f-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0a6f-136">Element</span></span>|<span data-ttu-id="c0a6f-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0a6f-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="c0a6f-138">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="c0a6f-139">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="c0a6f-140">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="c0a6f-141">Her derleme `<dependentAssembly>` için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="c0a6f-142">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0a6f-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0a6f-143">Remarks</span></span>  
 <span data-ttu-id="c0a6f-144">**Her\<dependentAssembly >** öğesi bir  **\<assemblyIdentity >** alt öğe içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="c0a6f-145">`processorArchitecture` Öznitelik varsa`<assemblyIdentity>` , öğe yalnızca karşılık gelen işlemci mimarisine sahip derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="c0a6f-146">`processorArchitecture` Özniteliği yoksa`<assemblyIdentity>` , öğesi herhangi bir işlemci mimarisine sahip bir derleme için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="c0a6f-147">Aşağıdaki örnek, iki farklı iki işlemci mimarisinden oluşan aynı ada sahip iki derleme için bir yapılandırma dosyası gösterir ve sürümleri eşitlenmiş olarak korunmaz. Uygulama x86 platformunda yürütüldüğünde ilk `<assemblyIdentity>` öğe uygulanır ve diğeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="c0a6f-148">Uygulama, x86 veya ia64 dışında bir platformda yürütülüyorsa her ikisi de yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="c0a6f-149">Bir yapılandırma dosyası `processorArchitecture` özniteliği olmayan bir `<assemblyIdentity>` öğe içeriyorsa ve platformla eşleşen bir öğe içermiyorsa `processorArchitecture` , özniteliği olmayan öğesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0a6f-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0a6f-150">Example</span></span>  
 <span data-ttu-id="c0a6f-151">Aşağıdaki örnek, bir derleme hakkında nasıl bilgi sağlayagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0a6f-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0a6f-152">See also</span></span>

- [<span data-ttu-id="c0a6f-153">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c0a6f-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c0a6f-154">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c0a6f-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c0a6f-155">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c0a6f-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)

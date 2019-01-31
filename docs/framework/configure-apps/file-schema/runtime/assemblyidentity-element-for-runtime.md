---
title: <assemblyIdentity> için <runtime> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: 6f05f1f395156e149e73c1081e486b5285c2b599
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277504"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="de802-102">\<assemblyIdentity > öğesi için \<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="de802-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="de802-103">Derleme hakkında tanımlayıcı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="de802-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="de802-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="de802-104">\<configuration></span></span>  
<span data-ttu-id="de802-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="de802-105">\<runtime></span></span>  
<span data-ttu-id="de802-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="de802-106">\<assemblyBinding></span></span>  
<span data-ttu-id="de802-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="de802-107">\<dependentAssembly></span></span>  
<span data-ttu-id="de802-108">\<assemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="de802-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de802-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de802-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de802-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de802-110">Attributes and Elements</span></span>  
 <span data-ttu-id="de802-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de802-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de802-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de802-112">Attributes</span></span>  
  
|<span data-ttu-id="de802-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de802-113">Attribute</span></span>|<span data-ttu-id="de802-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de802-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="de802-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="de802-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="de802-116">Derlemenin adı</span><span class="sxs-lookup"><span data-stu-id="de802-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="de802-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="de802-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="de802-118">Dil ve ülke/bölge derlemenin belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="de802-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="de802-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="de802-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="de802-120">Bir onaltılık değer derlemenin tanımlayıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="de802-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="de802-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="de802-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="de802-122">Biri değerleri "x86", "amd64", "msil" veya "ia64" İşlemci mimarisi işlemciye özgü kodu içeren bir derleme için belirtme.</span><span class="sxs-lookup"><span data-stu-id="de802-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="de802-123">Değerler büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="de802-123">The values are not case-sensitive.</span></span> <span data-ttu-id="de802-124">Öznitelik başka bir değer tüm atanıp atanmadığını `<assemblyIdentity>` öğesi göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="de802-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="de802-125">Bkz. <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="de802-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="de802-126">processorArchitecture özniteliği</span><span class="sxs-lookup"><span data-stu-id="de802-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="de802-127">Değer</span><span class="sxs-lookup"><span data-stu-id="de802-127">Value</span></span>|<span data-ttu-id="de802-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de802-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="de802-129">Yalnızca AMD x86 64 mimari.</span><span class="sxs-lookup"><span data-stu-id="de802-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="de802-130">Yalnızca Intel Itanium mimarisini.</span><span class="sxs-lookup"><span data-stu-id="de802-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="de802-131">Nötr işlemcisi ve sözcük başına bit göre.</span><span class="sxs-lookup"><span data-stu-id="de802-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="de802-132">Bir 32-bit x86 işlemci, ya da yerel ya da Windows 64-bit platformlarda ortamında Windows (WOW).</span><span class="sxs-lookup"><span data-stu-id="de802-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de802-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de802-133">Child Elements</span></span>  
 <span data-ttu-id="de802-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="de802-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de802-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de802-135">Parent Elements</span></span>  
  
|<span data-ttu-id="de802-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="de802-136">Element</span></span>|<span data-ttu-id="de802-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de802-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="de802-138">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="de802-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="de802-139">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="de802-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="de802-140">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="de802-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="de802-141">Bir `<dependentAssembly>` her derleme için öğesi.</span><span class="sxs-lookup"><span data-stu-id="de802-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="de802-142">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="de802-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de802-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de802-143">Remarks</span></span>  
 <span data-ttu-id="de802-144">Her  **\<dependentAssembly >** öğesi biri olmalı  **\<assemblyIdentity >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="de802-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="de802-145">Varsa `processorArchitecture` özniteliği mevcutsa, `<assemblyIdentity>` öğesi uygulandığı yalnızca bütünleştirilmiş kod ile ilgili İşlemci mimarisi.</span><span class="sxs-lookup"><span data-stu-id="de802-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="de802-146">Varsa `processorArchitecture` özniteliği mevcut değil `<assemblyIdentity>` öğesi herhangi bir işlemci mimarisine sahip bir derleme için geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="de802-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="de802-147">Aşağıdaki örnek, iki farklı iki işlemci mimarileri hedefleyen ve sürümleri eşitlenmiş tutulmuş olmayan iki derlemeler için aynı ada sahip bir yapılandırma dosyası gösterir. Ne zaman uygulama yürütür üzerinde x86 platformu ilk `<assemblyIdentity>` öğesine uygular ve diğer göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="de802-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="de802-148">Uygulama x86 veya IA64 dışındaki bir platformda yürütülürse, iki göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="de802-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="de802-149">Bir yapılandırma dosyası içeriyorsa bir `<assemblyIdentity>` öğe olmadan `processorArchitecture` özniteliği ve platformu, öğe olmadan eşleşen bir öğe içermiyor `processorArchitecture` özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de802-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de802-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="de802-150">Example</span></span>  
 <span data-ttu-id="de802-151">Aşağıdaki örnek, bir derleme hakkındaki bilgilerin nasıl sağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de802-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de802-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de802-152">See also</span></span>
- [<span data-ttu-id="de802-153">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="de802-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="de802-154">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="de802-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="de802-155">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="de802-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

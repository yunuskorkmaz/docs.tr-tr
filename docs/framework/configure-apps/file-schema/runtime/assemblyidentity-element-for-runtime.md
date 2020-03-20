---
title: <runtime> için <assemblyIdentity> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154315"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="3038e-102">\<çalışma zamanı> \<için assemblyIdentity> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3038e-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="3038e-103">Derleme hakkında tanımlayıcı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3038e-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="3038e-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3038e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3038e-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3038e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3038e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montajBağlama>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="3038e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="3038e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bağımlıAssembly>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="3038e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="3038e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span><span class="sxs-lookup"><span data-stu-id="3038e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3038e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3038e-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3038e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3038e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3038e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3038e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3038e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3038e-112">Attributes</span></span>  
  
|<span data-ttu-id="3038e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3038e-113">Attribute</span></span>|<span data-ttu-id="3038e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3038e-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3038e-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3038e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="3038e-116">Derlemenin adı</span><span class="sxs-lookup"><span data-stu-id="3038e-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="3038e-117">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3038e-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3038e-118">Derlemenin dilini ve ülkesini/bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3038e-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="3038e-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3038e-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3038e-120">Derlemenin güçlü adını belirten bir hexadecimal değer.</span><span class="sxs-lookup"><span data-stu-id="3038e-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="3038e-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3038e-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3038e-122">"x86", "amd64", "msil" veya "ia64" değerlerinden biri, işlemciye özgü kod içeren bir derlemenin işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3038e-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="3038e-123">Değerler büyük/küçük harf duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="3038e-123">The values are not case-sensitive.</span></span> <span data-ttu-id="3038e-124">Öznitelik başka bir değer atanırsa, tüm `<assemblyIdentity>` öğe yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="3038e-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="3038e-125">Bkz. <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="3038e-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="3038e-126">processorMimari Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3038e-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="3038e-127">Değer</span><span class="sxs-lookup"><span data-stu-id="3038e-127">Value</span></span>|<span data-ttu-id="3038e-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3038e-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="3038e-129">Sadece AMD x86-64 mimarisi.</span><span class="sxs-lookup"><span data-stu-id="3038e-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="3038e-130">Intel Itanium mimarisi sadece.</span><span class="sxs-lookup"><span data-stu-id="3038e-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="3038e-131">İşlemci ve kelime başına bit açısından nötr.</span><span class="sxs-lookup"><span data-stu-id="3038e-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="3038e-132">32 bit x86 işlemci, 64 bit platformda yerel veya Windows Windows (WOW) ortamında.</span><span class="sxs-lookup"><span data-stu-id="3038e-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3038e-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3038e-133">Child Elements</span></span>  
 <span data-ttu-id="3038e-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="3038e-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3038e-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3038e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3038e-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3038e-136">Element</span></span>|<span data-ttu-id="3038e-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3038e-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="3038e-138">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3038e-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="3038e-139">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3038e-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="3038e-140">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="3038e-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="3038e-141">Her `<dependentAssembly>` montaj için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="3038e-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="3038e-142">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3038e-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3038e-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3038e-143">Remarks</span></span>  
 <span data-ttu-id="3038e-144">Her \*\* \<bağımlıAssembly>\*\* öğesi bir \*\* \<assemblyIdentity>\*\* alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3038e-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="3038e-145">`processorArchitecture` Öznitelik varsa, `<assemblyIdentity>` öğe yalnızca ilgili işlemci mimarisi ile derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3038e-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="3038e-146">`processorArchitecture` Öznitelik yoksa, `<assemblyIdentity>` öğe herhangi bir işlemci mimarisi olan bir derlemeye uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="3038e-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="3038e-147">Aşağıdaki örnek, iki farklı iki işlemci mimarisini hedefleyen ve sürümleri eşitlemede korunmayan aynı ada sahip iki derleme için bir yapılandırma dosyası gösterir. Uygulama x86 platformunda yürütüldüğünde `<assemblyIdentity>` ilk öğe uygulanır ve diğeri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="3038e-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="3038e-148">Uygulama x86 veya ia64 dışında bir platformda yürütülürse, her ikisi de yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="3038e-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="3038e-149">Yapılandırma dosyası özniteliği `<assemblyIdentity>` olmayan `processorArchitecture` bir öğe içeriyorsa ve platformla eşleşen bir öğe `processorArchitecture` içermiyorsa, özniteliği olmayan öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3038e-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3038e-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="3038e-150">Example</span></span>  
 <span data-ttu-id="3038e-151">Aşağıdaki örnek, bir derleme hakkında nasıl bilgi verilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3038e-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3038e-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3038e-152">See also</span></span>

- [<span data-ttu-id="3038e-153">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3038e-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3038e-154">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3038e-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3038e-155">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="3038e-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)

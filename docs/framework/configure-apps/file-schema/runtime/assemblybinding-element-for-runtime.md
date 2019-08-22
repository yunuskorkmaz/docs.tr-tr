---
title: <runtime> için <assemblyBinding> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84ec54eeb8adee90031057dadc4549cb73527be1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663907"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="0f81e-102">\<çalışma zamanı için \<assemblyBinding > öğesi ></span><span class="sxs-lookup"><span data-stu-id="0f81e-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="0f81e-103">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="0f81e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0f81e-104">\<configuration></span></span>  
<span data-ttu-id="0f81e-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="0f81e-105">\<runtime></span></span>  
<span data-ttu-id="0f81e-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="0f81e-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f81e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f81e-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f81e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f81e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0f81e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f81e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f81e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f81e-110">Attributes</span></span>  
  
|<span data-ttu-id="0f81e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0f81e-111">Attribute</span></span>|<span data-ttu-id="0f81e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f81e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f81e-113">**özniteliði**</span><span class="sxs-lookup"><span data-stu-id="0f81e-113">**xmlns**</span></span>|<span data-ttu-id="0f81e-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0f81e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0f81e-115">Derleme bağlaması için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="0f81e-116">Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f81e-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="0f81e-117">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="0f81e-117">**appliesTo**</span></span>|<span data-ttu-id="0f81e-118">.NET Framework derleme yeniden yönlendirmenin uygulandığı çalışma zamanı sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="0f81e-119">Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f81e-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="0f81e-120">Hiçbir **AppliesTo** özniteliği belirtilmemişse,  **\<assemblyBinding >** öğesi .NET Framework tüm sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="0f81e-121">**AppliesTo** özniteliği .NET Framework sürüm 1,1 ' de tanıtılmıştı; .NET Framework 1,0 sürümü tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0f81e-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="0f81e-122">Bu, bir **AppliesTo** özniteliği belirtilmiş olsa bile, .NET Framework sürüm 1,0 kullanılırken tüm  **\<assemblyBinding >** öğelerinin uygulandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f81e-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f81e-123">Child Elements</span></span>  
  
|<span data-ttu-id="0f81e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f81e-124">Element</span></span>|<span data-ttu-id="0f81e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f81e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f81e-126">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="0f81e-126">\<dependentAssembly></span></span>](dependentassembly-element.md)|<span data-ttu-id="0f81e-127">Derleme için bağlama ilkesini ve derleme konumunu kapsüller.</span><span class="sxs-lookup"><span data-stu-id="0f81e-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="0f81e-128">Her derleme için bir  **\<dependentAssembly >** etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f81e-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="0f81e-129">\<yoklama ></span><span class="sxs-lookup"><span data-stu-id="0f81e-129">\<probing></span></span>](probing-element.md)|<span data-ttu-id="0f81e-130">Derlemeler yüklenirken ortak dil çalışma zamanı aramalarının alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="0f81e-131">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="0f81e-131">\<publisherPolicy></span></span>](publisherpolicy-element.md)|<span data-ttu-id="0f81e-132">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="0f81e-133">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="0f81e-133">\<qualifyAssembly></span></span>](qualifyassembly-element.md)|<span data-ttu-id="0f81e-134">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f81e-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f81e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="0f81e-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f81e-136">Element</span></span>|<span data-ttu-id="0f81e-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f81e-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0f81e-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0f81e-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0f81e-139">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f81e-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f81e-140">Example</span></span>  
 <span data-ttu-id="0f81e-141">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceğini ve bir kod temeli nasıl sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="0f81e-142">Aşağıdaki örnek, bir .NET Framework derlemesinin bağlamasını yeniden yönlendirmek için **AppliesTo** özniteliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f81e-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f81e-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f81e-143">See also</span></span>

- [<span data-ttu-id="0f81e-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0f81e-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0f81e-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="0f81e-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0f81e-146">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="0f81e-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)

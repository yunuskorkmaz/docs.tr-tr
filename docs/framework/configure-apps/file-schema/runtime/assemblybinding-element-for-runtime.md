---
title: "&lt;assemblyBinding&gt; öğesi için &lt;çalışma zamanı&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fdf2bc90c496c9906b5d31bad0065e01bdb47942
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a><span data-ttu-id="94893-102">&lt;assemblyBinding&gt; öğesi için &lt;çalışma zamanı&gt;</span><span class="sxs-lookup"><span data-stu-id="94893-102">&lt;assemblyBinding&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="94893-103">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="94893-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="94893-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="94893-104">\<configuration></span></span>  
<span data-ttu-id="94893-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="94893-105">\<runtime></span></span>  
<span data-ttu-id="94893-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="94893-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94893-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94893-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94893-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="94893-108">Attributes and Elements</span></span>  
 <span data-ttu-id="94893-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94893-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94893-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94893-110">Attributes</span></span>  
  
|<span data-ttu-id="94893-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="94893-111">Attribute</span></span>|<span data-ttu-id="94893-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94893-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94893-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="94893-113">**xmlns**</span></span>|<span data-ttu-id="94893-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="94893-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="94893-115">Derleme bağlama için gereken XML ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="94893-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="94893-116">Dize kullanma "urn: şemaları-microsoft-com:asm.v1" değeri olarak.</span><span class="sxs-lookup"><span data-stu-id="94893-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="94893-117">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="94893-117">**appliesTo**</span></span>|<span data-ttu-id="94893-118">.NET Framework derleme yeniden yönlendirme uygulandığı çalışma zamanı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="94893-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="94893-119">Bu isteğe bağlı öznitelik uygulandığı hangi sürümünün belirtmek için bir .NET Framework sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="94893-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="94893-120">Öyle değilse **appliesTo** özniteliği belirtilirse  **\<assemblyBinding >** öğesi tüm .NET Framework sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94893-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="94893-121">**AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="94893-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="94893-122">Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.</span><span class="sxs-lookup"><span data-stu-id="94893-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94893-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="94893-123">Child Elements</span></span>  
  
|<span data-ttu-id="94893-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="94893-124">Element</span></span>|<span data-ttu-id="94893-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94893-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94893-126">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="94893-126">\<dependentAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|<span data-ttu-id="94893-127">Derleme bağlama ilkesi ve derleme konumu yalıtır.</span><span class="sxs-lookup"><span data-stu-id="94893-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="94893-128">Kullanmayı  **\<dependentAssembly >** her derleme için etiket.</span><span class="sxs-lookup"><span data-stu-id="94893-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="94893-129">\<yoklama ></span><span class="sxs-lookup"><span data-stu-id="94893-129">\<probing></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|<span data-ttu-id="94893-130">Ortak dil çalışma zamanı derlemeleri yükleme sırasında arama alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="94893-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="94893-131">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="94893-131">\<publisherPolicy></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|<span data-ttu-id="94893-132">Çalışma zamanı Yayımcı ilkesi geçerli olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="94893-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="94893-133">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="94893-133">\<qualifyAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|<span data-ttu-id="94893-134">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="94893-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94893-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="94893-135">Parent Elements</span></span>  
  
|<span data-ttu-id="94893-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="94893-136">Element</span></span>|<span data-ttu-id="94893-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94893-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="94893-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="94893-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="94893-139">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="94893-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="94893-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="94893-140">Example</span></span>  
 <span data-ttu-id="94893-141">Aşağıdaki örnek, bir derleme sürümünü yeniden yönlendirme ve bir codebase sağlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94893-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="94893-142">Aşağıdaki örnekte nasıl kullanılacağını gösterir **appliesTo** bir .NET Framework Derleme bağlaması yeniden yönlendirme için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="94893-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94893-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94893-143">See Also</span></span>  
 [<span data-ttu-id="94893-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="94893-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="94893-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="94893-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="94893-146">Derleme sürümlerini yönlendirme</span><span class="sxs-lookup"><span data-stu-id="94893-146">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

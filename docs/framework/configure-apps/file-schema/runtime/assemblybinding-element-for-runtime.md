---
title: '&lt;assemblyBinding&gt; öğesi için &lt;çalışma zamanı&gt;'
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
ms.openlocfilehash: c0060115360cd077fd1e390be916f2f8afbadd9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713999"
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a><span data-ttu-id="671c0-102">&lt;assemblyBinding&gt; öğesi için &lt;çalışma zamanı&gt;</span><span class="sxs-lookup"><span data-stu-id="671c0-102">&lt;assemblyBinding&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="671c0-103">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="671c0-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="671c0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="671c0-104">\<configuration></span></span>  
<span data-ttu-id="671c0-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="671c0-105">\<runtime></span></span>  
<span data-ttu-id="671c0-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="671c0-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="671c0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="671c0-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="671c0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="671c0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="671c0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="671c0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="671c0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="671c0-110">Attributes</span></span>  
  
|<span data-ttu-id="671c0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="671c0-111">Attribute</span></span>|<span data-ttu-id="671c0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="671c0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="671c0-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="671c0-113">**xmlns**</span></span>|<span data-ttu-id="671c0-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="671c0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="671c0-115">Derleme bağlama için gerekli XML ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="671c0-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="671c0-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span><span class="sxs-lookup"><span data-stu-id="671c0-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="671c0-117">**AppliesTo**</span><span class="sxs-lookup"><span data-stu-id="671c0-117">**appliesTo**</span></span>|<span data-ttu-id="671c0-118">.NET Framework derleme yeniden yönlendirme uygulandığı çalışma zamanı sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="671c0-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="671c0-119">İsteğe bağlı bu öznitelik, bir .NET Framework sürüm numarası geçerli hangi sürüm olduğunu belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="671c0-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="671c0-120">Hayır ise **appliesTo** özniteliği belirtilirse,  **\<assemblyBinding >** öğe tüm .NET Framework sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="671c0-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="671c0-121">**AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 tarafından göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="671c0-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="671c0-122">Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.</span><span class="sxs-lookup"><span data-stu-id="671c0-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="671c0-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="671c0-123">Child Elements</span></span>  
  
|<span data-ttu-id="671c0-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="671c0-124">Element</span></span>|<span data-ttu-id="671c0-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="671c0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="671c0-126">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="671c0-126">\<dependentAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|<span data-ttu-id="671c0-127">Bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="671c0-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="671c0-128">Bir  **\<dependentAssembly >** her derleme için etiket.</span><span class="sxs-lookup"><span data-stu-id="671c0-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="671c0-129">\<yoklama ></span><span class="sxs-lookup"><span data-stu-id="671c0-129">\<probing></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|<span data-ttu-id="671c0-130">Ortak dil çalışma zamanı derlemeleri yüklenirken arama alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="671c0-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="671c0-131">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="671c0-131">\<publisherPolicy></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|<span data-ttu-id="671c0-132">Çalışma zamanı Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="671c0-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="671c0-133">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="671c0-133">\<qualifyAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|<span data-ttu-id="671c0-134">Kısmi bir adı kullanıldığında dinamik olarak yüklenmesi gereken bütünleştirilmiş kodun tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="671c0-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="671c0-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="671c0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="671c0-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="671c0-136">Element</span></span>|<span data-ttu-id="671c0-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="671c0-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="671c0-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="671c0-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="671c0-139">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="671c0-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="671c0-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="671c0-140">Example</span></span>  
 <span data-ttu-id="671c0-141">Aşağıdaki örnek, bir derleme sürümünü diğerine yeniden yönlendirme ve bir kod temeli sağlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="671c0-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="671c0-142">Aşağıdaki örnek nasıl kullanılacağını gösterir **appliesTo** bir .NET Framework derlemesinin bağlama yeniden yönlendirme için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="671c0-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="671c0-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="671c0-143">See also</span></span>
- [<span data-ttu-id="671c0-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="671c0-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="671c0-145">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="671c0-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="671c0-146">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="671c0-146">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

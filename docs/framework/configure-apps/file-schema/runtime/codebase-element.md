---
title: "&lt;codeBase&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b30f1dc3ccade3028c31c57ffdab521802f086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="d4df6-102">&lt;codeBase&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d4df6-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="d4df6-103">Ortak dil çalışma zamanı bütünleştirilmiş bulabileceğiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="d4df6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d4df6-104">\<configuration></span></span>  
<span data-ttu-id="d4df6-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d4df6-105">\<runtime></span></span>  
<span data-ttu-id="d4df6-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="d4df6-106">\<assemblyBinding></span></span>  
<span data-ttu-id="d4df6-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="d4df6-107">\<dependentAssembly></span></span>  
<span data-ttu-id="d4df6-108">\<codeBase ></span><span class="sxs-lookup"><span data-stu-id="d4df6-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4df6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4df6-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4df6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4df6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4df6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4df6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4df6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4df6-112">Attributes</span></span>  
  
|<span data-ttu-id="d4df6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4df6-113">Attribute</span></span>|<span data-ttu-id="d4df6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4df6-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="d4df6-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d4df6-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4df6-116">Çalışma zamanı derlemesi belirtilen sürümünü bulabileceğiniz URL'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="d4df6-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d4df6-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="d4df6-118">Codebase uygulandığı derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="d4df6-119">Bir derleme sürüm numarası biçimi *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="d4df6-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="d4df6-120">Version özniteliği</span><span class="sxs-lookup"><span data-stu-id="d4df6-120">version Attribute</span></span>  
  
|<span data-ttu-id="d4df6-121">Değer</span><span class="sxs-lookup"><span data-stu-id="d4df6-121">Value</span></span>|<span data-ttu-id="d4df6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4df6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4df6-123">Sürüm numarasını her kısmı için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="d4df6-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="d4df6-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4df6-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4df6-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4df6-125">Child Elements</span></span>  
 <span data-ttu-id="d4df6-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4df6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4df6-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4df6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d4df6-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4df6-128">Element</span></span>|<span data-ttu-id="d4df6-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4df6-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="d4df6-130">Özel kaynak dosyalarını derlemek için kullanılan yapı sağlayıcıları koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4df6-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="d4df6-131">Yapı sağlayıcıları herhangi bir sayıda olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="d4df6-132">ASP.NET kullanan tüm derleme ayarlarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d4df6-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="d4df6-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d4df6-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="d4df6-134">ASP.NET yapılandırma bölümü için kök öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4df6-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4df6-135">Remarks</span></span>  
 <span data-ttu-id="d4df6-136">Çalışma zamanı için  **\<codeBase >** bir makine yapılandırma dosyası veya yayımcı ilkesi dosyası ayarı dosyası ayrıca derleme sürümünü yönlendirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="d4df6-137">Uygulama yapılandırma dosyaları, derleme sürümünü yeniden yönlendirme olmadan codebase ayarı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="d4df6-138">Hangi derleme sürümün kullanılacağını belirlendikten sonra çalışma zamanı sürümü belirler dosyasından codebase ayar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d4df6-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="d4df6-139">Hiçbir codebase belirtilirse, çalışma zamanı derlemesi için Normal yollardan araştırmaları.</span><span class="sxs-lookup"><span data-stu-id="d4df6-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="d4df6-140">Derleme tanımlayıcı adı varsa, codebase ayarı Yerel intranet veya Internet üzerinde herhangi bir yere olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="d4df6-141">Derleme özel bir derleme ise codebase ayarı uygulama dizinindeki göreli bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df6-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="d4df6-142">Güçlü bir ad olmadan derlemeler için sürüm dikkate alınmaz ve ilk görünümünü yükleyicisi kullanır \<codebase > içinde \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="d4df6-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="d4df6-143">Başka bir derlemeye bağlama yeniden yönlendirmelerini uygulama yapılandırma dosyasında bir girdi ise, yeniden yönlendirme derleme sürümünü bağlama isteği eşleşmiyor olsa bile öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="d4df6-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4df6-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4df6-144">Example</span></span>  
 <span data-ttu-id="d4df6-145">Aşağıdaki örnek, çalışma zamanı bütünleştirilmiş bulabileceğiniz belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d4df6-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4df6-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4df6-146">See Also</span></span>  
 [<span data-ttu-id="d4df6-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d4df6-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d4df6-148">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d4df6-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d4df6-149">Derlemenin konumunu belirtme</span><span class="sxs-lookup"><span data-stu-id="d4df6-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="d4df6-150">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="d4df6-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)

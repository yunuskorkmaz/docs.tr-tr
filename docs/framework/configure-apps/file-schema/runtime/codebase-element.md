---
title: <codeBase> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: b5825efcc613689e73fb56b6695fe7c75ff09136
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356617"
---
# <a name="codebase-element"></a><span data-ttu-id="369b6-102">\<codeBase > öğesi</span><span class="sxs-lookup"><span data-stu-id="369b6-102">\<codeBase> Element</span></span>

<span data-ttu-id="369b6-103">Ortak dil çalışma zamanının bir derlemeyi nerede belirtir.</span><span class="sxs-lookup"><span data-stu-id="369b6-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="369b6-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span><span class="sxs-lookup"><span data-stu-id="369b6-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="369b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="369b6-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="369b6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="369b6-106">Attributes and Elements</span></span>

<span data-ttu-id="369b6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="369b6-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="369b6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="369b6-108">Attributes</span></span>

|<span data-ttu-id="369b6-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="369b6-109">Attribute</span></span>|<span data-ttu-id="369b6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369b6-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="369b6-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="369b6-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="369b6-112">Çalışma zamanı derlemenin belirtilen sürümü nereden URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="369b6-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="369b6-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="369b6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="369b6-114">Kod temeli uygulandığı derleme sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="369b6-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="369b6-115">Bir derleme sürümü numarasının biçimi *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="369b6-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="369b6-116">Sürüm özniteliği</span><span class="sxs-lookup"><span data-stu-id="369b6-116">version Attribute</span></span>

|<span data-ttu-id="369b6-117">Değer</span><span class="sxs-lookup"><span data-stu-id="369b6-117">Value</span></span>|<span data-ttu-id="369b6-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369b6-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="369b6-119">Sürüm numarasının her bölüm için geçerli değerler 0 ile 65535 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="369b6-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="369b6-120">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="369b6-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="369b6-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="369b6-121">Child Elements</span></span>

<span data-ttu-id="369b6-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="369b6-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="369b6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="369b6-123">Parent Elements</span></span>

|<span data-ttu-id="369b6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="369b6-124">Element</span></span>|<span data-ttu-id="369b6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="369b6-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="369b6-126">Özel kaynak dosyalarını derlemek için kullanılan derleme sağlayıcıları koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="369b6-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="369b6-127">Herhangi bir sayıda derleme sağlayıcıları olabilir.</span><span class="sxs-lookup"><span data-stu-id="369b6-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="369b6-128">ASP.NET kullanan tüm derleme ayarlarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="369b6-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="369b6-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="369b6-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="369b6-130">ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="369b6-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="369b6-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="369b6-131">Remarks</span></span>

<span data-ttu-id="369b6-132">Çalışma zamanı kullanmak için  **\<codeBase >** bir makine yapılandırma dosyası ya da Yayımcı ilkesi dosyası ayarı dosyası da derleme sürümünü yeniden yönlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="369b6-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="369b6-133">Uygulama yapılandırma dosyaları, derleme sürümü yeniden yönlendirme olmadan bir kod temeli ayarı olabilir.</span><span class="sxs-lookup"><span data-stu-id="369b6-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="369b6-134">Hangi derleme sürümünün kullanılacağını belirledikten sonra çalışma zamanı sürümünü belirleyen dosyasından codebase ayarı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="369b6-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="369b6-135">Herhangi bir kod temelinde belirtilirse, çalışma zamanı derlemesi için her zamanki yolla araştırmaları.</span><span class="sxs-lookup"><span data-stu-id="369b6-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="369b6-136">Derlemeyi tanımlayıcı bir ada sahip, codebase ayar herhangi bir yerel intranet veya Internet üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="369b6-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="369b6-137">Derleme özel bir derleme ise, kod tabanının ayarı uygulamanın dizinine göreli bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="369b6-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="369b6-138">Güçlü adı olmayan derlemeler için sürüm göz ardı edilir ve ilk görünümünü yükleyicisi kullanır \<codebase > içinde \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="369b6-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="369b6-139">Başka bir derleme için bağlama yeniden yönlendirmeleri uygulama yapılandırma dosyasında bir girdi varsa, bağlama isteği derleme sürümü eşleşmiyor olsa bile yönlendirme öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="369b6-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="369b6-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="369b6-140">Example</span></span>

<span data-ttu-id="369b6-141">Aşağıdaki örnek, çalışma zamanının bir derlemeyi nerede belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="369b6-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="369b6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="369b6-142">See also</span></span>

- [<span data-ttu-id="369b6-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="369b6-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="369b6-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="369b6-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="369b6-145">Bütünleştirilmiş Kodun Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="369b6-145">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [<span data-ttu-id="369b6-146">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="369b6-146">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)

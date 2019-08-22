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
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663862"
---
# <a name="codebase-element"></a><span data-ttu-id="eefd0-102">\<codeBase > öğesi</span><span class="sxs-lookup"><span data-stu-id="eefd0-102">\<codeBase> Element</span></span>

<span data-ttu-id="eefd0-103">Ortak dil çalışma zamanının bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="eefd0-104">\<Yapılandırma > \<çalışma zamanı \<> assemblyBinding \<> dependentAssembly \<> kod temeli ></span><span class="sxs-lookup"><span data-stu-id="eefd0-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="eefd0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eefd0-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eefd0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eefd0-106">Attributes and Elements</span></span>

<span data-ttu-id="eefd0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eefd0-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eefd0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eefd0-108">Attributes</span></span>

|<span data-ttu-id="eefd0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eefd0-109">Attribute</span></span>|<span data-ttu-id="eefd0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eefd0-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="eefd0-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="eefd0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="eefd0-112">Çalışma zamanının belirtilen derleme sürümünü bulabileceği URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="eefd0-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="eefd0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="eefd0-114">Kod temelinin uygulandığı derlemenin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="eefd0-115">Bütünleştirilmiş kod sürümü numarası, *birincil. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="eefd0-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="eefd0-116">sürüm özniteliği</span><span class="sxs-lookup"><span data-stu-id="eefd0-116">version Attribute</span></span>

|<span data-ttu-id="eefd0-117">Değer</span><span class="sxs-lookup"><span data-stu-id="eefd0-117">Value</span></span>|<span data-ttu-id="eefd0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eefd0-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="eefd0-119">Sürüm numarasının her bir bölümü için geçerli değerler 0 ile 65535 arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="eefd0-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="eefd0-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eefd0-121">Child Elements</span></span>

<span data-ttu-id="eefd0-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="eefd0-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eefd0-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eefd0-123">Parent Elements</span></span>

|<span data-ttu-id="eefd0-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="eefd0-124">Element</span></span>|<span data-ttu-id="eefd0-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eefd0-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="eefd0-126">Özel kaynak dosyalarını derlemek için kullanılan yapı sağlayıcılarının koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eefd0-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="eefd0-127">Herhangi bir sayıda derleme sağlayıcısına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eefd0-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="eefd0-128">ASP.NET tarafından kullanılan tüm derleme ayarlarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="eefd0-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="eefd0-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="eefd0-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="eefd0-130">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eefd0-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eefd0-131">Remarks</span></span>

<span data-ttu-id="eefd0-132">Çalışma zamanının bir makine yapılandırma dosyası veya yayımcı ilke dosyasında  **\<codebase >** ayarını kullanması için, dosyanın de derleme sürümünü yeniden yönlendirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="eefd0-133">Uygulama yapılandırma dosyaları, derleme sürümünü yönlendirmeksizin bir kod temeli ayarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="eefd0-134">Hangi derleme sürümünün kullanılacağını belirledikten sonra, çalışma zamanı sürümü belirleyen dosyadan kod temeli ayarını uygular.</span><span class="sxs-lookup"><span data-stu-id="eefd0-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="eefd0-135">Kod temeli belirtilmemişse, çalışma zamanı derleme için her zamanki şekilde araştırılmış.</span><span class="sxs-lookup"><span data-stu-id="eefd0-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="eefd0-136">Derlemenin tanımlayıcı bir adı varsa, kod temeli ayarı yerel intranette veya Internet 'te herhangi bir yerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="eefd0-137">Derleme özel bir derlemedir, kod temeli ayarı uygulamanın dizinine göreli bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eefd0-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="eefd0-138">Tanımlayıcı adı olmayan derlemeler için sürüm yok sayılır ve yükleyici, bir \<kod temelinin ilk görünümünü dependentAssembly > içinde \<kullanır >.</span><span class="sxs-lookup"><span data-stu-id="eefd0-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="eefd0-139">Uygulama yapılandırma dosyasında bağlamayı başka bir derlemeye yönlendiren bir giriş varsa, derleme sürümü bağlama isteğiyle eşleşmezse bile yeniden yönlendirme öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="eefd0-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="eefd0-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="eefd0-140">Example</span></span>

<span data-ttu-id="eefd0-141">Aşağıdaki örnek, çalışma zamanının bir derlemeyi bulabileceği yeri nasıl belirtbileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="eefd0-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eefd0-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eefd0-142">See also</span></span>

- [<span data-ttu-id="eefd0-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="eefd0-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eefd0-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="eefd0-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="eefd0-145">Bütünleştirilmiş Kodun Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="eefd0-145">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="eefd0-146">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="eefd0-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)

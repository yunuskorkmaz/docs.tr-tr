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
ms.openlocfilehash: 475b7df55ed509157c1da0aeb8f979de238c72b5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971885"
---
# <a name="codebase-element"></a><span data-ttu-id="03fa0-102">\<codeBase > öğesi</span><span class="sxs-lookup"><span data-stu-id="03fa0-102">\<codeBase> Element</span></span>

<span data-ttu-id="03fa0-103">Ortak dil çalışma zamanının bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="03fa0-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03fa0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03fa0-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="03fa0-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="03fa0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="03fa0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="03fa0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="03fa0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="03fa0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Kod temeli >**</span><span class="sxs-lookup"><span data-stu-id="03fa0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**</span></span>

## <a name="syntax"></a><span data-ttu-id="03fa0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03fa0-109">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03fa0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="03fa0-110">Attributes and Elements</span></span>

<span data-ttu-id="03fa0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03fa0-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="03fa0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="03fa0-112">Attributes</span></span>

|<span data-ttu-id="03fa0-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="03fa0-113">Attribute</span></span>|<span data-ttu-id="03fa0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03fa0-114">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="03fa0-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="03fa0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="03fa0-116">Çalışma zamanının belirtilen derleme sürümünü bulabileceği URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="03fa0-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="03fa0-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="03fa0-118">Kod temelinin uygulandığı derlemenin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="03fa0-119">Bütünleştirilmiş kod sürümü numarası, *birincil. ikincil. derleme. düzeltme*.</span><span class="sxs-lookup"><span data-stu-id="03fa0-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="03fa0-120">sürüm özniteliği</span><span class="sxs-lookup"><span data-stu-id="03fa0-120">version Attribute</span></span>

|<span data-ttu-id="03fa0-121">Değer</span><span class="sxs-lookup"><span data-stu-id="03fa0-121">Value</span></span>|<span data-ttu-id="03fa0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03fa0-122">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="03fa0-123">Sürüm numarasının her bir bölümü için geçerli değerler 0 ile 65535 arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="03fa0-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-124">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="03fa0-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="03fa0-125">Child Elements</span></span>

<span data-ttu-id="03fa0-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="03fa0-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03fa0-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="03fa0-127">Parent Elements</span></span>

|<span data-ttu-id="03fa0-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="03fa0-128">Element</span></span>|<span data-ttu-id="03fa0-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03fa0-129">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="03fa0-130">Özel kaynak dosyalarını derlemek için kullanılan yapı sağlayıcılarının koleksiyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="03fa0-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="03fa0-131">Herhangi bir sayıda derleme sağlayıcısına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03fa0-131">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="03fa0-132">ASP.NET tarafından kullanılan tüm derleme ayarlarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="03fa0-132">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="03fa0-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="03fa0-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="03fa0-134">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-134">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03fa0-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03fa0-135">Remarks</span></span>

<span data-ttu-id="03fa0-136">Çalışma zamanının bir makine yapılandırma dosyası veya yayımcı ilke dosyasında  **\<codebase >** ayarını kullanması için, dosyanın de derleme sürümünü yeniden yönlendirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="03fa0-137">Uygulama yapılandırma dosyaları, derleme sürümünü yönlendirmeksizin bir kod temeli ayarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="03fa0-138">Hangi derleme sürümünün kullanılacağını belirledikten sonra, çalışma zamanı sürümü belirleyen dosyadan kod temeli ayarını uygular.</span><span class="sxs-lookup"><span data-stu-id="03fa0-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="03fa0-139">Kod temeli belirtilmemişse, çalışma zamanı derleme için her zamanki şekilde araştırılmış.</span><span class="sxs-lookup"><span data-stu-id="03fa0-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="03fa0-140">Derlemenin tanımlayıcı bir adı varsa, kod temeli ayarı yerel intranette veya Internet 'te herhangi bir yerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="03fa0-141">Derleme özel bir derlemedir, kod temeli ayarı uygulamanın dizinine göreli bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03fa0-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="03fa0-142">Tanımlayıcı adı olmayan derlemeler için sürüm yok sayılır ve yükleyici, bir \<kod temelinin ilk görünümünü dependentAssembly > içinde \<kullanır >.</span><span class="sxs-lookup"><span data-stu-id="03fa0-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="03fa0-143">Uygulama yapılandırma dosyasında bağlamayı başka bir derlemeye yönlendiren bir giriş varsa, derleme sürümü bağlama isteğiyle eşleşmezse bile yeniden yönlendirme öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="03fa0-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="03fa0-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="03fa0-144">Example</span></span>

<span data-ttu-id="03fa0-145">Aşağıdaki örnek, çalışma zamanının bir derlemeyi bulabileceği yeri nasıl belirtbileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="03fa0-145">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="03fa0-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03fa0-146">See also</span></span>

- [<span data-ttu-id="03fa0-147">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="03fa0-147">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="03fa0-148">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="03fa0-148">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="03fa0-149">Bir derlemenin konumunu belirtin</span><span class="sxs-lookup"><span data-stu-id="03fa0-149">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="03fa0-150">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="03fa0-150">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)

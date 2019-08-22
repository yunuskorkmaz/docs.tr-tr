---
title: <compiler> Öğesi
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 80eea3373e2f4b7e45ebeb31dd6552ea02c109e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659727"
---
# <a name="compiler-element"></a><span data-ttu-id="e3dea-102">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-102">\<compiler> Element</span></span>

<span data-ttu-id="e3dea-103">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="e3dea-104">\<Configuration öğesi > \<System. CodeDom öğesi > \<compilers öğesi > \<derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="e3dea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3dea-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3dea-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3dea-106">Attributes and Elements</span></span>

<span data-ttu-id="e3dea-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3dea-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3dea-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3dea-108">Attributes</span></span>

|<span data-ttu-id="e3dea-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3dea-109">Attribute</span></span>|<span data-ttu-id="e3dea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3dea-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="e3dea-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e3dea-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e3dea-112">Derleme için derleyiciye özgü ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="e3dea-113">`compilerOptions` Özniteliği için değerler, genellikle derleyicinin derleyici seçenekleri konusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="e3dea-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e3dea-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3dea-115">Dil sağlayıcısı için kaynak dosyalar tarafından kullanılan, noktalı virgülle ayrılmış dosya adı uzantılarının bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3dea-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="e3dea-116">Örneğin, ". cs".</span><span class="sxs-lookup"><span data-stu-id="e3dea-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="e3dea-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e3dea-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3dea-118">Dil sağlayıcısı tarafından desteklenen dil adlarının noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3dea-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="e3dea-119">Örneğin, "c#; CS; CSharp".</span><span class="sxs-lookup"><span data-stu-id="e3dea-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="e3dea-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e3dea-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3dea-121">Sağlayıcı uygulamasını içeren derlemenin adı da dahil olmak üzere, dil sağlayıcısının tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="e3dea-122">Tür adı, [tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)tanımlanan gereksinimlere uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3dea-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="e3dea-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e3dea-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e3dea-124">Varsayılan derleyici uyarı düzeyini belirtir; Dil sağlayıcısının derleme uyarılarını hata olarak değerlendirme düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="e3dea-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e3dea-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3dea-125">Child Elements</span></span>

|<span data-ttu-id="e3dea-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3dea-126">Element</span></span>|<span data-ttu-id="e3dea-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3dea-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3dea-128">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-128">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="e3dea-129">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3dea-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3dea-130">Parent Elements</span></span>

|<span data-ttu-id="e3dea-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3dea-131">Element</span></span>|<span data-ttu-id="e3dea-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3dea-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3dea-133">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-133">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e3dea-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e3dea-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="e3dea-135">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-135">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="e3dea-136">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="e3dea-137">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-137">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="e3dea-138">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e3dea-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3dea-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3dea-139">Remarks</span></span>

<span data-ttu-id="e3dea-140">Her `<compiler>` öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="e3dea-141">Sağlayıcı, <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil için genişletiyor `<compiler>` ; öğesi, dil sağlayıcısı için derleyici ve kod Oluşturucu ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3dea-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="e3dea-142">.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3dea-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e3dea-143">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e3dea-144">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e3dea-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="e3dea-145">Uygulama veya Web yapılandırma dosyasındaki derleyici öğeleri, makine yapılandırma dosyasındaki ayarları tamamlayabilir veya geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="e3dea-146">Aynı dil adı veya aynı dosya uzantısı için birden fazla sağlayıcı uygulamanız yapılandırılmışsa, son eşleştirme yapılandırması söz konusu dil adı veya dosya uzantısı için önceden yapılandırılmış tüm sağlayıcıları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e3dea-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="e3dea-147">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="e3dea-147">Configuration File</span></span>

<span data-ttu-id="e3dea-148">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3dea-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="e3dea-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3dea-149">Example</span></span>

<span data-ttu-id="e3dea-150">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e3dea-150">The following example illustrates a typical compiler configuration element:</span></span>

```xml
<configuration>
  <system.codedom>
    <compilers>
      <!-- zero or more compiler elements -->
      <compiler
        language="c#;cs;csharp"
        extension=".cs"
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"
        compilerOptions="/optimize"
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e3dea-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3dea-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e3dea-152">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e3dea-152">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e3dea-153">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="e3dea-153">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="e3dea-154">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="e3dea-154">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="e3dea-155">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3dea-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

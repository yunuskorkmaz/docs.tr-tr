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
ms.openlocfilehash: 46676f25597f85596598d6f67c98930971cb0447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088050"
---
# <a name="compiler-element"></a><span data-ttu-id="a1d6f-102">\<derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="a1d6f-102">\<compiler> Element</span></span>

<span data-ttu-id="a1d6f-103">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="a1d6f-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a1d6f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a1d6f-105">[**System. codedom >\<** ](system-codedom-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="a1d6f-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="a1d6f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyiciler >** ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="a1d6f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="a1d6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<derleyicisi >**</span><span class="sxs-lookup"><span data-stu-id="a1d6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a1d6f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1d6f-108">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1d6f-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1d6f-109">Attributes and Elements</span></span>

<span data-ttu-id="a1d6f-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1d6f-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1d6f-111">Attributes</span></span>

|<span data-ttu-id="a1d6f-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a1d6f-112">Attribute</span></span>|<span data-ttu-id="a1d6f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6f-113">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="a1d6f-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a1d6f-115">Derleme için derleyiciye özgü ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="a1d6f-116">`compilerOptions` özniteliği için değerler, genellikle derleyicinin derleyici seçenekleri konusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="a1d6f-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="a1d6f-118">Dil sağlayıcısı için kaynak dosyalar tarafından kullanılan, noktalı virgülle ayrılmış dosya adı uzantılarının bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-118">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="a1d6f-119">Örneğin, ". cs".</span><span class="sxs-lookup"><span data-stu-id="a1d6f-119">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="a1d6f-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="a1d6f-121">Dil sağlayıcısı tarafından desteklenen dil adlarının noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-121">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="a1d6f-122">Örneğin, "c#; CS; CSharp".</span><span class="sxs-lookup"><span data-stu-id="a1d6f-122">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="a1d6f-123">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-123">Required attribute.</span></span><br /><br /> <span data-ttu-id="a1d6f-124">Sağlayıcı uygulamasını içeren derlemenin adı da dahil olmak üzere, dil sağlayıcısının tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-124">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="a1d6f-125">Tür adı, [tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)tanımlanan gereksinimlere uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-125">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="a1d6f-126">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-126">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a1d6f-127">Varsayılan derleyici uyarı düzeyini belirtir; Dil sağlayıcısının derleme uyarılarını hata olarak değerlendirme düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-127">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a1d6f-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1d6f-128">Child Elements</span></span>

|<span data-ttu-id="a1d6f-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1d6f-129">Element</span></span>|<span data-ttu-id="a1d6f-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6f-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1d6f-131">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="a1d6f-131">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="a1d6f-132">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-132">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1d6f-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1d6f-133">Parent Elements</span></span>

|<span data-ttu-id="a1d6f-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1d6f-134">Element</span></span>|<span data-ttu-id="a1d6f-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6f-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1d6f-136">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="a1d6f-136">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="a1d6f-137">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="a1d6f-138">System. CodeDom > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="a1d6f-138">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="a1d6f-139">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-139">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="a1d6f-140">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="a1d6f-140">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="a1d6f-141">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-141">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1d6f-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1d6f-142">Remarks</span></span>

<span data-ttu-id="a1d6f-143">Her `<compiler>` öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-143">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="a1d6f-144">Sağlayıcı, belirli bir dil için <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfını genişletir; `<compiler>` öğesi, dil sağlayıcısı için derleyici ve kod Oluşturucu ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-144">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="a1d6f-145">.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-145">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a1d6f-146">Geliştiriciler ve derleyici satıcıları, yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulamasının yapılandırma ayarlarını ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-146">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a1d6f-147">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-147">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="a1d6f-148">Uygulama veya Web yapılandırma dosyasındaki derleyici öğeleri, makine yapılandırma dosyasındaki ayarları tamamlayabilir veya geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-148">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="a1d6f-149">Aynı dil adı veya aynı dosya uzantısı için birden fazla sağlayıcı uygulamanız yapılandırılmışsa, son eşleştirme yapılandırması söz konusu dil adı veya dosya uzantısı için önceden yapılandırılmış tüm sağlayıcıları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-149">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="a1d6f-150">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="a1d6f-150">Configuration File</span></span>

<span data-ttu-id="a1d6f-151">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-151">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="a1d6f-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1d6f-152">Example</span></span>

<span data-ttu-id="a1d6f-153">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a1d6f-153">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a1d6f-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d6f-154">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="a1d6f-155">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="a1d6f-155">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a1d6f-156">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="a1d6f-156">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="a1d6f-157">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="a1d6f-157">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="a1d6f-158">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a1d6f-158">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

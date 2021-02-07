---
description: 'Daha fazla bilgi edinin: <compiler> öğesi'
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
ms.openlocfilehash: 91540d2217320b225ae67a48d616720ef2a0b679
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699226"
---
# <a name="compiler-element"></a><span data-ttu-id="ea0cf-103">\<compiler> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ea0cf-103">\<compiler> Element</span></span>

<span data-ttu-id="ea0cf-104">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-104">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="ea0cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea0cf-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea0cf-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea0cf-106">Attributes and Elements</span></span>

<span data-ttu-id="ea0cf-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea0cf-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea0cf-108">Attributes</span></span>

|<span data-ttu-id="ea0cf-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea0cf-109">Attribute</span></span>|<span data-ttu-id="ea0cf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea0cf-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="ea0cf-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ea0cf-112">Derleme için derleyiciye özgü ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="ea0cf-113">Özniteliği için değerler, `compilerOptions` genellikle derleyicinin derleyici seçenekleri konusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="ea0cf-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea0cf-115">Dil sağlayıcısı için kaynak dosyalar tarafından kullanılan, noktalı virgülle ayrılmış dosya adı uzantılarının bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="ea0cf-116">Örneğin, ". cs".</span><span class="sxs-lookup"><span data-stu-id="ea0cf-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="ea0cf-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea0cf-118">Dil sağlayıcısı tarafından desteklenen dil adlarının noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="ea0cf-119">Örneğin, "c#; CS; CSharp".</span><span class="sxs-lookup"><span data-stu-id="ea0cf-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="ea0cf-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea0cf-121">Sağlayıcı uygulamasını içeren derlemenin adı da dahil olmak üzere, dil sağlayıcısının tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="ea0cf-122">Tür adı, [tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)tanımlanan gereksinimlere uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="ea0cf-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ea0cf-124">Varsayılan derleyici uyarı düzeyini belirtir; Dil sağlayıcısının derleme uyarılarını hata olarak değerlendirme düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ea0cf-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea0cf-125">Child Elements</span></span>

|<span data-ttu-id="ea0cf-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea0cf-126">Element</span></span>|<span data-ttu-id="ea0cf-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea0cf-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea0cf-128">\<providerOption> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ea0cf-128">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="ea0cf-129">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ea0cf-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea0cf-130">Parent Elements</span></span>

|<span data-ttu-id="ea0cf-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea0cf-131">Element</span></span>|<span data-ttu-id="ea0cf-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea0cf-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea0cf-133">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ea0cf-133">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="ea0cf-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="ea0cf-135">\<system.codedom> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ea0cf-135">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="ea0cf-136">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="ea0cf-137">\<compilers> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ea0cf-137">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="ea0cf-138">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ea0cf-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea0cf-139">Remarks</span></span>

<span data-ttu-id="ea0cf-140">Her `<compiler>` öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="ea0cf-141">Sağlayıcı, <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil için genişletiyor; öğesi, `<compiler>` dil sağlayıcısı için derleyici ve kod Oluşturucu ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="ea0cf-142">.NET Framework, makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="ea0cf-143">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> .</span><span class="sxs-lookup"><span data-stu-id="ea0cf-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="ea0cf-144"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="ea0cf-145">Uygulama veya Web yapılandırma dosyasındaki derleyici öğeleri, makine yapılandırma dosyasındaki ayarları tamamlayabilir veya geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="ea0cf-146">Aynı dil adı veya aynı dosya uzantısı için birden fazla sağlayıcı uygulamanız yapılandırılmışsa, son eşleştirme yapılandırması söz konusu dil adı veya dosya uzantısı için önceden yapılandırılmış tüm sağlayıcıları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ea0cf-147">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="ea0cf-147">Configuration File</span></span>

<span data-ttu-id="ea0cf-148">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ea0cf-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea0cf-149">Example</span></span>

<span data-ttu-id="ea0cf-150">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="ea0cf-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ea0cf-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea0cf-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="ea0cf-152">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ea0cf-152">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ea0cf-153">\<compilers> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ea0cf-153">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="ea0cf-154">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="ea0cf-154">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="ea0cf-155">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ea0cf-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

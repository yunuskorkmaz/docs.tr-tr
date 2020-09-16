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
ms.openlocfilehash: 0abbe594754cbd70ec4732a1e7ef98e8e88bf167
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544758"
---
# <a name="compiler-element"></a><span data-ttu-id="3b954-102">\<compiler> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3b954-102">\<compiler> Element</span></span>

<span data-ttu-id="3b954-103">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b954-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="3b954-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b954-104">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b954-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b954-105">Attributes and Elements</span></span>

<span data-ttu-id="3b954-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b954-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b954-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b954-107">Attributes</span></span>

|<span data-ttu-id="3b954-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3b954-108">Attribute</span></span>|<span data-ttu-id="3b954-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b954-109">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="3b954-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b954-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3b954-111">Derleme için derleyiciye özgü ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b954-111">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="3b954-112">Özniteliği için değerler, `compilerOptions` genellikle derleyicinin derleyici seçenekleri konusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="3b954-112">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="3b954-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b954-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b954-114">Dil sağlayıcısı için kaynak dosyalar tarafından kullanılan, noktalı virgülle ayrılmış dosya adı uzantılarının bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b954-114">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="3b954-115">Örneğin, ". cs".</span><span class="sxs-lookup"><span data-stu-id="3b954-115">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="3b954-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b954-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b954-117">Dil sağlayıcısı tarafından desteklenen dil adlarının noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b954-117">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="3b954-118">Örneğin, "c#; CS; CSharp".</span><span class="sxs-lookup"><span data-stu-id="3b954-118">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="3b954-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b954-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b954-120">Sağlayıcı uygulamasını içeren derlemenin adı da dahil olmak üzere, dil sağlayıcısının tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b954-120">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="3b954-121">Tür adı, [tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)tanımlanan gereksinimlere uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b954-121">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="3b954-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b954-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3b954-123">Varsayılan derleyici uyarı düzeyini belirtir; Dil sağlayıcısının derleme uyarılarını hata olarak değerlendirme düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="3b954-123">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3b954-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b954-124">Child Elements</span></span>

|<span data-ttu-id="3b954-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b954-125">Element</span></span>|<span data-ttu-id="3b954-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b954-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b954-127">\<providerOption> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="3b954-127">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="3b954-128">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b954-128">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3b954-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b954-129">Parent Elements</span></span>

|<span data-ttu-id="3b954-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b954-130">Element</span></span>|<span data-ttu-id="3b954-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b954-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b954-132">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="3b954-132">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="3b954-133">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3b954-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="3b954-134">\<system.codedom> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="3b954-134">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="3b954-135">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b954-135">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="3b954-136">\<compilers> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="3b954-136">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="3b954-137">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3b954-137">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b954-138">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b954-138">Remarks</span></span>

<span data-ttu-id="3b954-139">Her `<compiler>` öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b954-139">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="3b954-140">Sağlayıcı, <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil için genişletiyor; öğesi, `<compiler>` dil sağlayıcısı için derleyici ve kod Oluşturucu ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b954-140">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="3b954-141">.NET Framework, makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b954-141">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="3b954-142">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> .</span><span class="sxs-lookup"><span data-stu-id="3b954-142">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="3b954-143"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b954-143">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="3b954-144">Uygulama veya Web yapılandırma dosyasındaki derleyici öğeleri, makine yapılandırma dosyasındaki ayarları tamamlayabilir veya geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b954-144">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="3b954-145">Aynı dil adı veya aynı dosya uzantısı için birden fazla sağlayıcı uygulamanız yapılandırılmışsa, son eşleştirme yapılandırması söz konusu dil adı veya dosya uzantısı için önceden yapılandırılmış tüm sağlayıcıları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3b954-145">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="3b954-146">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="3b954-146">Configuration File</span></span>

<span data-ttu-id="3b954-147">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b954-147">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="3b954-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b954-148">Example</span></span>

<span data-ttu-id="3b954-149">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="3b954-149">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3b954-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b954-150">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="3b954-151">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3b954-151">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3b954-152">\<compilers> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="3b954-152">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="3b954-153">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="3b954-153">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="3b954-154">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3b954-154">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

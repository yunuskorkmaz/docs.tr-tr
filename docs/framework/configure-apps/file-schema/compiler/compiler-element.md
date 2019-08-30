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
ms.openlocfilehash: a19cf8182cdb338fd8596ef38311916de0daae37
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168936"
---
# <a name="compiler-element"></a><span data-ttu-id="718fa-102">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="718fa-102">\<compiler> Element</span></span>

<span data-ttu-id="718fa-103">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="718fa-103">Specifies the compiler configuration attributes for a language provider.</span></span>

[<span data-ttu-id="718fa-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="718fa-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="718fa-105">&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="718fa-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="718fa-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyiciler >** ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="718fa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>  
<span data-ttu-id="718fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Derleyici >**</span><span class="sxs-lookup"><span data-stu-id="718fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="718fa-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="718fa-108">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="718fa-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="718fa-109">Attributes and Elements</span></span>

<span data-ttu-id="718fa-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="718fa-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="718fa-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="718fa-111">Attributes</span></span>

|<span data-ttu-id="718fa-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="718fa-112">Attribute</span></span>|<span data-ttu-id="718fa-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718fa-113">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="718fa-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="718fa-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="718fa-115">Derleme için derleyiciye özgü ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="718fa-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="718fa-116">`compilerOptions` Özniteliği için değerler, genellikle derleyicinin derleyici seçenekleri konusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="718fa-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="718fa-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="718fa-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="718fa-118">Dil sağlayıcısı için kaynak dosyalar tarafından kullanılan, noktalı virgülle ayrılmış dosya adı uzantılarının bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="718fa-118">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="718fa-119">Örneğin, ". cs".</span><span class="sxs-lookup"><span data-stu-id="718fa-119">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="718fa-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="718fa-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="718fa-121">Dil sağlayıcısı tarafından desteklenen dil adlarının noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="718fa-121">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="718fa-122">Örneğin, "c#; CS; CSharp".</span><span class="sxs-lookup"><span data-stu-id="718fa-122">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="718fa-123">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="718fa-123">Required attribute.</span></span><br /><br /> <span data-ttu-id="718fa-124">Sağlayıcı uygulamasını içeren derlemenin adı da dahil olmak üzere, dil sağlayıcısının tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="718fa-124">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="718fa-125">Tür adı, [tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)tanımlanan gereksinimlere uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="718fa-125">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="718fa-126">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="718fa-126">Optional attribute.</span></span><br /><br /> <span data-ttu-id="718fa-127">Varsayılan derleyici uyarı düzeyini belirtir; Dil sağlayıcısının derleme uyarılarını hata olarak değerlendirme düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="718fa-127">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="718fa-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="718fa-128">Child Elements</span></span>

|<span data-ttu-id="718fa-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="718fa-129">Element</span></span>|<span data-ttu-id="718fa-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718fa-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="718fa-131">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="718fa-131">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="718fa-132">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="718fa-132">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="718fa-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="718fa-133">Parent Elements</span></span>

|<span data-ttu-id="718fa-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="718fa-134">Element</span></span>|<span data-ttu-id="718fa-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718fa-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="718fa-136">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="718fa-136">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="718fa-137">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="718fa-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="718fa-138">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="718fa-138">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="718fa-139">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="718fa-139">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="718fa-140">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="718fa-140">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="718fa-141">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="718fa-141">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="718fa-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="718fa-142">Remarks</span></span>

<span data-ttu-id="718fa-143">Her `<compiler>` öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="718fa-143">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="718fa-144">Sağlayıcı, <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil için genişletiyor `<compiler>` ; öğesi, dil sağlayıcısı için derleyici ve kod Oluşturucu ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="718fa-144">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="718fa-145">.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="718fa-145">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="718fa-146">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="718fa-146">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="718fa-147">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="718fa-147">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="718fa-148">Uygulama veya Web yapılandırma dosyasındaki derleyici öğeleri, makine yapılandırma dosyasındaki ayarları tamamlayabilir veya geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="718fa-148">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="718fa-149">Aynı dil adı veya aynı dosya uzantısı için birden fazla sağlayıcı uygulamanız yapılandırılmışsa, son eşleştirme yapılandırması söz konusu dil adı veya dosya uzantısı için önceden yapılandırılmış tüm sağlayıcıları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="718fa-149">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="718fa-150">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="718fa-150">Configuration File</span></span>

<span data-ttu-id="718fa-151">Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="718fa-151">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="718fa-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="718fa-152">Example</span></span>

<span data-ttu-id="718fa-153">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="718fa-153">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="718fa-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="718fa-154">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="718fa-155">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="718fa-155">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="718fa-156">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="718fa-156">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="718fa-157">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="718fa-157">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="718fa-158">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="718fa-158">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

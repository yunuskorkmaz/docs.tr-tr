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
ms.openlocfilehash: 34753d538ff37ac4ae621f653d47ac92ac6749a0
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674470"
---
# <a name="compiler-element"></a><span data-ttu-id="ef667-102">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-102">\<compiler> Element</span></span>

<span data-ttu-id="ef667-103">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef667-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="ef667-104">\<yapılandırma öğesi > \<system.codedom öğesi > \<compilers öğesi > \<derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="ef667-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef667-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef667-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef667-106">Attributes and Elements</span></span>

<span data-ttu-id="ef667-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef667-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef667-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef667-108">Attributes</span></span>

|<span data-ttu-id="ef667-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ef667-109">Attribute</span></span>|<span data-ttu-id="ef667-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef667-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="ef667-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ef667-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ef667-112">Derleme için ek derleyici özel bağımsız değişkenler belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef667-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="ef667-113">Değerleri `compilerOptions` özniteliği derleyicisi için derleyici seçeneklerini konularında genellikle listelenir.</span><span class="sxs-lookup"><span data-stu-id="ef667-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="ef667-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ef667-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef667-115">Dosya adı uzantıları için dil sağlayıcısı kaynak kodları tarafından kullanılan noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef667-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="ef667-116">Örneğin, ".cs".</span><span class="sxs-lookup"><span data-stu-id="ef667-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="ef667-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ef667-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef667-118">Dil sağlayıcısı tarafından desteklenen dil adları noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef667-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="ef667-119">Örneğin, "c#; cs; csharp".</span><span class="sxs-lookup"><span data-stu-id="ef667-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="ef667-120">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ef667-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef667-121">Sağlayıcısı uygulamasını içeren derlemenin adı dahil olmak üzere, bir dil sağlayıcısı türü adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef667-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="ef667-122">Tür adı tanımlanan gereksinimlerini karşılaması gerekir [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ef667-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="ef667-123">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ef667-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ef667-124">Varsayılan derleyici uyarı düzeyini belirtir. ve dil sağlayıcısı derleme uyarılarını hata olarak değerlendirir düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="ef667-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ef667-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef667-125">Child Elements</span></span>

|<span data-ttu-id="ef667-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef667-126">Element</span></span>|<span data-ttu-id="ef667-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef667-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef667-128">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-128">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="ef667-129">Derleyici sürümü öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef667-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef667-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef667-130">Parent Elements</span></span>

|<span data-ttu-id="ef667-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef667-131">Element</span></span>|<span data-ttu-id="ef667-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef667-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef667-133">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-133">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="ef667-134">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ef667-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="ef667-135">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-135">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="ef667-136">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef667-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="ef667-137">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-137">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="ef667-138">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren `<compiler>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ef667-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef667-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef667-139">Remarks</span></span>

<span data-ttu-id="ef667-140">Her `<compiler>` öğesi için belirli bir dil sağlayıcısı compiler configuration öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef667-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="ef667-141">Sağlayıcı genişletir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil; `<compiler>` öğe, derleyici ve dil sağlayıcısı için kod Oluşturucu ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef667-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="ef667-142">.NET Framework ilk derleyici ayarları makine yapılandırma dosyasındaki (Machine.config) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef667-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="ef667-143">Geliştiriciler ve derleyici satıcıları ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ef667-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="ef667-144">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarlarını bir bilgisayardaki program aracılığıyla listeleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef667-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="ef667-145">Bir uygulama ya da Web yapılandırma dosyası derleyici öğeleri tamamlayabilir veya makine yapılandırma dosyasındaki ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ef667-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="ef667-146">Son eşleşen yapılandırma sağlayıcısı uygulamasında birden fazla aynı dil adı veya dosya uzantısına için yapılandırılmışsa, bu dil adı veya dosya uzantısı için önceki tüm yapılandırılmış sağlayıcılarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ef667-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ef667-147">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="ef667-147">Configuration File</span></span>

<span data-ttu-id="ef667-148">Bu öğe, makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef667-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ef667-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef667-149">Example</span></span>

<span data-ttu-id="ef667-150">Aşağıdaki örnekte, tipik bir derleyici yapılandırma öğesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ef667-150">The following example illustrates a typical compiler configuration element:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef667-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef667-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="ef667-152">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ef667-152">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ef667-153">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef667-153">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [<span data-ttu-id="ef667-154">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="ef667-154">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="ef667-155">[derleme (ASP.NET Settings Schema) yönelik derleyiciler için derleyici öğesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef667-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

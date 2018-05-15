---
title: '&lt;Derleyici&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b033e26d64f23398a4da6842bb4688cc94627d68
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="0dd61-102">&lt;Derleyici&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="0dd61-103">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="0dd61-104">\<yapılandırma öğesi ></span><span class="sxs-lookup"><span data-stu-id="0dd61-104">\<configuration Element></span></span>  
<span data-ttu-id="0dd61-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="0dd61-105">\<system.codedom Element></span></span>  
<span data-ttu-id="0dd61-106">\<compilers öğesi ></span><span class="sxs-lookup"><span data-stu-id="0dd61-106">\<compilers Element></span></span>  
<span data-ttu-id="0dd61-107">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd61-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dd61-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dd61-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dd61-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0dd61-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0dd61-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dd61-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0dd61-111">Attributes</span></span>  
  
|<span data-ttu-id="0dd61-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0dd61-112">Attribute</span></span>|<span data-ttu-id="0dd61-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dd61-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="0dd61-114">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0dd61-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0dd61-115">Derleme için ek derleyici özgü bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="0dd61-116">Değerleri `compilerOptions` özniteliği derleyici için derleyici seçenekleri konudaki genellikle listelenir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="0dd61-117">Visual Studio 2005 belgelerinde derleyici seçenekleri "derleyici seçenekleri" dizinindeki arayarak bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd61-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="0dd61-118">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0dd61-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="0dd61-119">Dosya adı uzantıları için dil sağlayıcısı kaynak dosyalar tarafından kullanılan noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dd61-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="0dd61-120">Örneğin, ".cs".</span><span class="sxs-lookup"><span data-stu-id="0dd61-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="0dd61-121">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0dd61-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="0dd61-122">Dil sağlayıcısı tarafından desteklenen dil adlarını noktalı virgülle ayrılmış bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dd61-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="0dd61-123">Örneğin, "c#; cs; csharp".</span><span class="sxs-lookup"><span data-stu-id="0dd61-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="0dd61-124">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0dd61-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="0dd61-125">Sağlayıcı uygulaması içeren derlemenin adını içeren dil sağlayıcısı türü adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="0dd61-126">Tür adı tanımlanan gereksinimleri karşılaması gerekir [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="0dd61-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="0dd61-127">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0dd61-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0dd61-128">Varsayılan derleyici uyarı düzeyini belirtir; dil sağlayıcısı olarak hatalar derleme uyarıları değerlendirir düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="0dd61-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dd61-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dd61-129">Child Elements</span></span>  
  
|<span data-ttu-id="0dd61-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="0dd61-130">Element</span></span>|<span data-ttu-id="0dd61-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dd61-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dd61-132">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="0dd61-133">Derleyici sürüm öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0dd61-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0dd61-134">Parent Elements</span></span>  
  
|<span data-ttu-id="0dd61-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="0dd61-135">Element</span></span>|<span data-ttu-id="0dd61-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dd61-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dd61-137">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="0dd61-138">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0dd61-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="0dd61-139">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="0dd61-140">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="0dd61-141">\<derleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="0dd61-142">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren `<compiler>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0dd61-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dd61-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dd61-143">Remarks</span></span>  
 <span data-ttu-id="0dd61-144">Her `<compiler>` öğesi için özgün dil sağlayıcısı compiler configuration öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="0dd61-145">Sağlayıcı genişletir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil; `<compiler>` öğe, derleyici ve dil sağlayıcısı Kod Oluşturucusu ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0dd61-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="0dd61-146">.NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0dd61-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="0dd61-147">Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="0dd61-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="0dd61-148">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0dd61-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="0dd61-149">Uygulama veya Web yapılandırma dosyası derleyici öğeleri tamamlayabilir veya makine yapılandırma dosyasındaki ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0dd61-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="0dd61-150">Birden fazla sağlayıcı uygulaması aynı dil adı veya aynı dosya uzantısı için yapılandırılmışsa, son eşleşen yapılandırma tüm önceki yapılandırılmış sağlayıcılarını dil adı veya dosya uzantısı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0dd61-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0dd61-151">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="0dd61-151">Configuration File</span></span>  
 <span data-ttu-id="0dd61-152">Bu öğe makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dd61-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dd61-153">Example</span></span>  
 <span data-ttu-id="0dd61-154">Aşağıdaki örnek tipik derleyici yapılandırma öğesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0dd61-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0dd61-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd61-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="0dd61-156">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="0dd61-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0dd61-157">\<derleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="0dd61-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="0dd61-158">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="0dd61-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 <span data-ttu-id="0dd61-159">[compiler Ögesi (ASP.NET Ayarlar Şeması) derleyicileri](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0dd61-159">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>

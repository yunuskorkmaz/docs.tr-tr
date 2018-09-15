---
title: '&lt;providerOption&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75cc2003a88cc7be467b9062c37b6b5d9eb82f53
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618905"
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="25ca0-102">&lt;providerOption&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="25ca0-103">Derleyici sürümü öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="25ca0-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="25ca0-104">\<yapılandırma öğesi ></span><span class="sxs-lookup"><span data-stu-id="25ca0-104">\<configuration Element></span></span>  
<span data-ttu-id="25ca0-105">\<system.codedom Element></span><span class="sxs-lookup"><span data-stu-id="25ca0-105">\<system.codedom Element></span></span>  
<span data-ttu-id="25ca0-106">\<compilers öğesi ></span><span class="sxs-lookup"><span data-stu-id="25ca0-106">\<compilers Element></span></span>  
<span data-ttu-id="25ca0-107">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-107">\<compiler> Element</span></span>  
<span data-ttu-id="25ca0-108">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ca0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25ca0-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25ca0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25ca0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="25ca0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25ca0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25ca0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25ca0-112">Attributes</span></span>  
  
|<span data-ttu-id="25ca0-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="25ca0-113">Attribute</span></span>|<span data-ttu-id="25ca0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25ca0-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="25ca0-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25ca0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="25ca0-116">Seçenek adını belirtir. Örneğin, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="25ca0-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="25ca0-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="25ca0-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="25ca0-118">Seçeneği için bir değer belirtir. Örneğin, "v3.5".</span><span class="sxs-lookup"><span data-stu-id="25ca0-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25ca0-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25ca0-119">Child Elements</span></span>  
 <span data-ttu-id="25ca0-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="25ca0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25ca0-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25ca0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="25ca0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="25ca0-122">Element</span></span>|<span data-ttu-id="25ca0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25ca0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25ca0-124">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="25ca0-125">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="25ca0-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="25ca0-126">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="25ca0-127">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="25ca0-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="25ca0-128">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="25ca0-129">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren `<compiler>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="25ca0-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="25ca0-130">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="25ca0-131">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="25ca0-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ca0-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25ca0-132">Remarks</span></span>  
 <span data-ttu-id="25ca0-133">.NET Framework sürüm 3.5, kod belge nesne modeli (CodeDOM) kod sağlayıcıları sağlayıcıya özel seçenekleri kullanarak destekleyebilir `<providerOption>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="25ca0-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="25ca0-134">.NET Framework 3.5 güncelleştirilmiş .NET Framework 2.0 derlemeleri içerir ve yeni türleri içeren yeni sürüm 3.5 derlemeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="25ca0-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="25ca0-135">Microsoft C# ve Visual Basic kod sağlayıcıları, .NET Framework 2.0 derlemelerinde toplanır, ancak sürüm 3.5 derleyicileri desteklemek üzere güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="25ca0-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="25ca0-136">Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2.0 derleyicileri için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25ca0-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="25ca0-137">Kullanabileceğiniz `<providerOption>` hedef derleyici sürümü 3.5 değiştirmek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="25ca0-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="25ca0-138">Bunu yapmak için "CompilerVersion" belirtin `name` özniteliği ve "v3.5" `value` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="25ca0-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="25ca0-139">Bir küçük harf "v" sürüm numarasıyla gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="25ca0-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="25ca0-140">Sürüm belirtimi genel ekleyerek yapabileceğiniz `<providerOption>` .NET Framework 2.0 Machine.config veya Web.config dosyası kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="25ca0-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="25ca0-141">Varsayılan derleyici sürümü 3.5 Machine.config dosyasında güncelleştirirseniz, bunu uygulama başına temelinde 2.0 dön kullanarak değiştirebilirsiniz `<providerOption>` uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="25ca0-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="25ca0-142">CodeDOM kod sağlayıcısı uygulayıcılar, alan bir oluşturucu sağlayarak özel seçenekleri işlenebilecek bir `providerOptions` türünde parametre <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="25ca0-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25ca0-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="25ca0-143">Example</span></span>  
 <span data-ttu-id="25ca0-144">Aşağıdaki örnek, C# kod sağlayıcının 3.5 sürümünün kullanılması gerektiğini belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25ca0-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25ca0-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25ca0-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="25ca0-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="25ca0-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="25ca0-147">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="25ca0-148">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="25ca0-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="25ca0-149">derleme (ASP.NET Settings Schema) yönelik derleyiciler için derleyici öğesi</span><span class="sxs-lookup"><span data-stu-id="25ca0-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)

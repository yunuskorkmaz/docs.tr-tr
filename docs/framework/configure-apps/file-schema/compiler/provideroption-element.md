---
title: "&lt;providerOption&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3a01a64ab8828104e8404f7d4efdd7b37eea373e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltprovideroptiongt-element"></a><span data-ttu-id="52f3f-102">&lt;providerOption&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-102">&lt;providerOption&gt; Element</span></span>
<span data-ttu-id="52f3f-103">Derleyici sürüm öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="52f3f-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="52f3f-104">\<yapılandırma öğesi ></span><span class="sxs-lookup"><span data-stu-id="52f3f-104">\<configuration Element></span></span>  
<span data-ttu-id="52f3f-105">\<System.codeDom öğesi ></span><span class="sxs-lookup"><span data-stu-id="52f3f-105">\<system.codedom Element></span></span>  
<span data-ttu-id="52f3f-106">\<compilers öğesi ></span><span class="sxs-lookup"><span data-stu-id="52f3f-106">\<compilers Element></span></span>  
<span data-ttu-id="52f3f-107">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-107">\<compiler> Element</span></span>  
<span data-ttu-id="52f3f-108">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f3f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52f3f-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52f3f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52f3f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="52f3f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52f3f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52f3f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52f3f-112">Attributes</span></span>  
  
|<span data-ttu-id="52f3f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52f3f-113">Attribute</span></span>|<span data-ttu-id="52f3f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52f3f-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="52f3f-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="52f3f-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="52f3f-116">Seçeneğin adı belirtir; Örneğin, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="52f3f-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="52f3f-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="52f3f-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="52f3f-118">Seçeneği için bir değer belirtir; Örneğin, "v3.5".</span><span class="sxs-lookup"><span data-stu-id="52f3f-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52f3f-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52f3f-119">Child Elements</span></span>  
 <span data-ttu-id="52f3f-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="52f3f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52f3f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52f3f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="52f3f-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="52f3f-122">Element</span></span>|<span data-ttu-id="52f3f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52f3f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52f3f-124">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="52f3f-125">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="52f3f-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="52f3f-126">\<System.codeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="52f3f-127">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="52f3f-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="52f3f-128">\<derleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="52f3f-129">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren `<compiler>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="52f3f-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="52f3f-130">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="52f3f-131">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="52f3f-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52f3f-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52f3f-132">Remarks</span></span>  
 <span data-ttu-id="52f3f-133">.NET Framework sürüm 3.5, kod belge nesne modeli (CodeDOM) kod sağlayıcıları sağlayıcıya özel seçenekleri kullanarak destekleyebilir `<providerOption>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="52f3f-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="52f3f-134">.NET Framework 3.5 güncelleştirilmiş .NET Framework 2.0 bütünleştirilmiş kodları bulunur ve yeni türlerini içeren yeni sürüm 3.5 derlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="52f3f-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="52f3f-135">Microsoft C# ve Visual Basic kodu sağlayıcıları .NET Framework 2.0 derlemelerde içeriyor ancak sürüm 3.5 derleyicileri desteklemek üzere güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="52f3f-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="52f3f-136">Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2.0 derleyicileri için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52f3f-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="52f3f-137">Kullanabileceğiniz `<providerOption>` öğesi 3.5 hedef derleyici sürüm olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="52f3f-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="52f3f-138">Bunu yapmak için "CompilerVersion" belirtme `name` özniteliği ve için "v3.5" `value` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="52f3f-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="52f3f-139">Küçük bir "v" sürüm numarasıyla gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="52f3f-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="52f3f-140">Sürüm belirtimi genel ekleyerek yapabileceğiniz `<providerOption>` .NET Framework 2.0 Machine.config veya kök Web.config dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="52f3f-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="52f3f-141">Machine.config dosyasındaki 3.5 için varsayılan derleyici sürümü güncelleştirirseniz, uygulama başına temelinde 2.0 dön kullanarak değiştirebilirsiniz `<providerOption>` uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="52f3f-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="52f3f-142">CodeDOM kodu sağlayıcısı Implementers alan oluşturucu sağlayarak özel seçenekleri işlenebilecek bir `providerOptions` türünde parametresi <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="52f3f-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52f3f-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="52f3f-143">Example</span></span>  
 <span data-ttu-id="52f3f-144">Aşağıdaki örnek, C# kod sağlayıcının 3.5 sürümünün kullanılacağını belirtin gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="52f3f-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52f3f-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52f3f-145">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="52f3f-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="52f3f-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="52f3f-147">\<derleyicileri > öğesi</span><span class="sxs-lookup"><span data-stu-id="52f3f-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="52f3f-148">Tam olarak nitelenmiş tür adlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="52f3f-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="52f3f-149">compiler Ögesi (ASP.NET Ayarlar Şeması) derleyicileri</span><span class="sxs-lookup"><span data-stu-id="52f3f-149">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)

---
description: 'Daha fazla bilgi edinin: <providerOption> öğesi'
title: <providerOption> Öğesi
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 1fdca58830e8563ef28cbca28857127252928fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699044"
---
# <a name="provideroption-element"></a><span data-ttu-id="8ec6d-103">\<providerOption> Öğesi</span><span class="sxs-lookup"><span data-stu-id="8ec6d-103">\<providerOption> Element</span></span>

<span data-ttu-id="8ec6d-104">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-104">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="8ec6d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ec6d-105">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ec6d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ec6d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8ec6d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ec6d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ec6d-108">Attributes</span></span>  
  
|<span data-ttu-id="8ec6d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ec6d-109">Attribute</span></span>|<span data-ttu-id="8ec6d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ec6d-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8ec6d-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="8ec6d-112">Seçeneğin adını belirtir; Örneğin, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="8ec6d-112">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="8ec6d-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8ec6d-114">Seçenek için değeri belirtir; Örneğin, "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="8ec6d-114">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ec6d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ec6d-115">Child Elements</span></span>  

 <span data-ttu-id="8ec6d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ec6d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ec6d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8ec6d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ec6d-118">Element</span></span>|<span data-ttu-id="8ec6d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ec6d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ec6d-120">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="8ec6d-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="8ec6d-121">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-121">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8ec6d-122">\<system.codedom> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="8ec6d-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="8ec6d-123">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-123">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="8ec6d-124">\<compilers> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="8ec6d-124">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="8ec6d-125">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-125">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="8ec6d-126">\<compiler> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="8ec6d-126">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="8ec6d-127">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-127">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ec6d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ec6d-128">Remarks</span></span>  

 <span data-ttu-id="8ec6d-129">.NET Framework sürüm 3,5 ' de, Kod Belge Nesne Modeli (CodeDOM) kod sağlayıcıları öğesini kullanarak sağlayıcıya özgü seçenekleri destekleyebilir `<providerOption>` .</span><span class="sxs-lookup"><span data-stu-id="8ec6d-129">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="8ec6d-130">.NET Framework 3,5, güncelleştirilmiş .NET Framework 2,0 derlemelerini içerir ve yeni türler içeren yeni sürüm 3,5 derlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-130">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="8ec6d-131">Microsoft C# ve Visual Basic kod sağlayıcıları .NET Framework 2,0 Derlemeleriyle bulunur, ancak sürüm 3,5 derleyicileri destekleyecek şekilde güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-131">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="8ec6d-132">Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2,0 derleyicileri için kod üretir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-132">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="8ec6d-133">`<providerOption>`Hedef derleyici sürümünü 3,5 olarak değiştirmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-133">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="8ec6d-134">Bunu yapmak için, özniteliği için "CompilerVersion" `name` ve öznitelik için "v 3.5" belirtin `value` .</span><span class="sxs-lookup"><span data-stu-id="8ec6d-134">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="8ec6d-135">Sürüm numarasından önce küçük bir "v" olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-135">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="8ec6d-136">`<providerOption>`.NET Framework 2,0 Machine.config veya kök Web.config dosyasına öğesini ekleyerek sürüm belirtimini Global hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-136">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="8ec6d-137">Machine.config dosyasında varsayılan derleyici sürümünü 3,5 olarak güncelleştirirseniz, `<providerOption>` uygulama yapılandırma dosyasındaki öğesini kullanarak uygulama başına temelinde yeniden 2,0 olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-137">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="8ec6d-138">CodeDOM kod sağlayıcısı uygulayıcıları, türünde bir parametre alan bir Oluşturucu sağlayarak özel seçenekleri işleyebilir `providerOptions` <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="8ec6d-138">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec6d-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ec6d-139">Example</span></span>  

 <span data-ttu-id="8ec6d-140">Aşağıdaki örnek, C# kod sağlayıcısının 3,5 sürümünün kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-140">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ec6d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec6d-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="8ec6d-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="8ec6d-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8ec6d-143">\<compilers> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="8ec6d-143">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="8ec6d-144">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="8ec6d-144">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="8ec6d-145">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ec6d-145">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

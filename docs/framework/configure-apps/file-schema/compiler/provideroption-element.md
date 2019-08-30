---
title: <providerOption> Öğesi
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 8d90364e34aa15bbd38e82ec70ec44616d7360f8
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167662"
---
# <a name="provideroption-element"></a><span data-ttu-id="8c7f1-102">\<providerOption > öğesi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-102">\<providerOption> Element</span></span>
<span data-ttu-id="8c7f1-103">Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
[<span data-ttu-id="8c7f1-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="8c7f1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8c7f1-105">&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c7f1-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="8c7f1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyiciler >** ](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c7f1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>  
<span data-ttu-id="8c7f1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Derleyici >** ](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c7f1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>  
<span data-ttu-id="8c7f1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**</span><span class="sxs-lookup"><span data-stu-id="8c7f1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7f1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c7f1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c7f1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c7f1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c7f1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8c7f1-112">Attributes</span></span>  
  
|<span data-ttu-id="8c7f1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8c7f1-113">Attribute</span></span>|<span data-ttu-id="8c7f1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c7f1-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8c7f1-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="8c7f1-116">Seçeneğin adını belirtir; Örneğin, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="8c7f1-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="8c7f1-117">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="8c7f1-118">Seçenek için değeri belirtir; Örneğin, "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="8c7f1-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c7f1-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c7f1-119">Child Elements</span></span>  
 <span data-ttu-id="8c7f1-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c7f1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c7f1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8c7f1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8c7f1-122">Element</span></span>|<span data-ttu-id="8c7f1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c7f1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c7f1-124">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="8c7f1-125">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8c7f1-126">\<System. CodeDom > öğesi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="8c7f1-127">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="8c7f1-128">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="8c7f1-129">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="8c7f1-130">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="8c7f1-131">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c7f1-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c7f1-132">Remarks</span></span>  
 <span data-ttu-id="8c7f1-133">.NET Framework sürüm 3,5 ' de, kod belge nesne modeli (CodeDom) kod sağlayıcıları `<providerOption>` öğesini kullanarak sağlayıcıya özgü seçenekleri destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="8c7f1-134">.NET Framework 3,5, güncelleştirilmiş .NET Framework 2,0 derlemelerini içerir ve yeni türler içeren yeni sürüm 3,5 derlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="8c7f1-135">Microsoft C# ve Visual Basic kod sağlayıcıları .NET Framework 2,0 Derlemeleriyle bulunur, ancak sürüm 3,5 derleyicileri destekleyecek şekilde güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="8c7f1-136">Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2,0 derleyicileri için kod üretir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="8c7f1-137">Hedef derleyici sürümünü 3,5 `<providerOption>` olarak değiştirmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="8c7f1-138">Bunu yapmak için, özniteliği için "CompilerVersion" `name` ve `value` öznitelik için "v 3.5" belirtin.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="8c7f1-139">Sürüm numarasından önce küçük bir "v" olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="8c7f1-140">.NET Framework 2,0 Machine. config veya root Web. config `<providerOption>` dosyasına öğesini ekleyerek sürüm belirtimini Global hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="8c7f1-141">Machine. config dosyasında varsayılan derleyici sürümünü 3,5 olarak güncelleştirirseniz, uygulama yapılandırma dosyasındaki `<providerOption>` öğesini kullanarak uygulama başına temelinde yeniden 2,0 olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="8c7f1-142">CodeDOM kod sağlayıcısı uygulayıcıları, türünde `providerOptions` <xref:System.Collections.Generic.IDictionary%602>bir parametre alan bir Oluşturucu sağlayarak özel seçenekleri işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c7f1-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c7f1-143">Example</span></span>  
 <span data-ttu-id="8c7f1-144">Aşağıdaki örnek, C# kod sağlayıcısının 3,5 sürümünün kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c7f1-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c7f1-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="8c7f1-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="8c7f1-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8c7f1-147">\<derleyiciler > öğesi</span><span class="sxs-lookup"><span data-stu-id="8c7f1-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="8c7f1-148">Tam Olarak Nitelenmiş Tür Adlarını Belirtme</span><span class="sxs-lookup"><span data-stu-id="8c7f1-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="8c7f1-149">[derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c7f1-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>

---
title: Derleyici ve Dil Sağlayıcısı Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: 4900c391ae94447cdf4be331a27f6f3398e9129a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659713"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="e02d5-102">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e02d5-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="e02d5-103">Derleyici ve dil sağlayıcısı ayarları, kullanılabilir dil sağlayıcıları için derleyici yapılandırma öğelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="e02d5-104">Her derleyici yapılandırma öğesi kod sağlayıcısı türü adını, derleyici parametrelerini, desteklenen dil adlarını ve desteklenen dosya uzantılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="e02d5-105">.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e02d5-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e02d5-106">Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarları ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e02d5-107">Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e02d5-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="e02d5-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="e02d5-108">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="e02d5-109">\<System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="e02d5-109">\<system.codedom></span></span>](system-codedom-element.md)  
  
 [<span data-ttu-id="e02d5-110">\<derleyiciler ></span><span class="sxs-lookup"><span data-stu-id="e02d5-110">\<compilers></span></span>](compilers-element.md)  
  
 [<span data-ttu-id="e02d5-111">\<Derleyici ></span><span class="sxs-lookup"><span data-stu-id="e02d5-111">\<compiler></span></span>](compiler-element.md)  
  
|<span data-ttu-id="e02d5-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="e02d5-112">Element</span></span>|<span data-ttu-id="e02d5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e02d5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e02d5-114">\<System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="e02d5-114">\<system.codedom></span></span>](system-codedom-element.md)|<span data-ttu-id="e02d5-115">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="e02d5-116">\<derleyiciler ></span><span class="sxs-lookup"><span data-stu-id="e02d5-116">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="e02d5-117">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-117">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="e02d5-118">\<Derleyici ></span><span class="sxs-lookup"><span data-stu-id="e02d5-118">\<compiler></span></span>](compiler-element.md)|<span data-ttu-id="e02d5-119">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e02d5-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e02d5-120">Example</span></span>  
 <span data-ttu-id="e02d5-121">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e02d5-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler  
          language="c#;cs;csharp"  
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""  
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e02d5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e02d5-122">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e02d5-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e02d5-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e02d5-124">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="e02d5-124">\<compiler> Element</span></span>](compiler-element.md)

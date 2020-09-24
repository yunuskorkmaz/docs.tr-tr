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
ms.openlocfilehash: 457e90c92530e04070575e42e3fc282ce45b3d03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153956"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="1fdd4-102">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1fdd4-102">Compiler and Language Provider Settings Schema</span></span>

<span data-ttu-id="1fdd4-103">Derleyici ve dil sağlayıcısı ayarları, kullanılabilir dil sağlayıcıları için derleyici yapılandırma öğelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="1fdd4-104">Her derleyici yapılandırma öğesi kod sağlayıcısı türü adını, derleyici parametrelerini, desteklenen dil adlarını ve desteklenen dosya uzantılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="1fdd4-105">.NET Framework, makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="1fdd4-106">Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> .</span><span class="sxs-lookup"><span data-stu-id="1fdd4-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="1fdd4-107"><xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)
  
|<span data-ttu-id="1fdd4-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="1fdd4-108">Element</span></span>|<span data-ttu-id="1fdd4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fdd4-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|<span data-ttu-id="1fdd4-110">Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-110">Specifies compiler configuration settings for available language providers.</span></span>|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="1fdd4-111">Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-111">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[\<compiler>](compiler-element.md)|<span data-ttu-id="1fdd4-112">Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-112">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1fdd4-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1fdd4-113">Example</span></span>  

 <span data-ttu-id="1fdd4-114">Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-114">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1fdd4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fdd4-115">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="1fdd4-116">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1fdd4-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1fdd4-117">\<compiler> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="1fdd4-117">\<compiler> Element</span></span>](compiler-element.md)

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
ms.openlocfilehash: fe08ac5dc0600e0861bb349ce99875af8658eb4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675279"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="05dbb-102">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="05dbb-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="05dbb-103">Compiler configuration öğeleri kullanılabilir dil sağlayıcıları için derleyici ve dil sağlayıcısı ayarları belirtin.</span><span class="sxs-lookup"><span data-stu-id="05dbb-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="05dbb-104">Her derleyici yapılandırma öğesi kodu belirtir. sağlayıcı türü adı, derleyici parametreler, desteklenen dil adları ve dosya uzantıları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05dbb-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="05dbb-105">.NET Framework ilk derleyici ayarları makine yapılandırma dosyasındaki (Machine.config) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05dbb-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="05dbb-106">Geliştiriciler ve derleyici satıcıları ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="05dbb-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="05dbb-107">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarlarını bir bilgisayardaki program aracılığıyla listeleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05dbb-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="05dbb-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="05dbb-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="05dbb-109">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="05dbb-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="05dbb-110">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="05dbb-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="05dbb-111">\<Derleyici ></span><span class="sxs-lookup"><span data-stu-id="05dbb-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="05dbb-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="05dbb-112">Element</span></span>|<span data-ttu-id="05dbb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05dbb-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05dbb-114">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="05dbb-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="05dbb-115">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="05dbb-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="05dbb-116">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="05dbb-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="05dbb-117">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="05dbb-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="05dbb-118">\<Derleyici ></span><span class="sxs-lookup"><span data-stu-id="05dbb-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="05dbb-119">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="05dbb-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05dbb-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="05dbb-120">Example</span></span>  
 <span data-ttu-id="05dbb-121">Aşağıdaki örnek, tipik bir derleyici yapılandırma öğesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="05dbb-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05dbb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05dbb-122">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="05dbb-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="05dbb-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="05dbb-124">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="05dbb-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)

---
title: "Derleyici ve Dil Sağlayıcısı Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3e020fcc63c0eff38dc602aacae31a6e0d2d2fe5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="6ec2e-102">Derleyici ve Dil Sağlayıcısı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6ec2e-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="6ec2e-103">Derleyici ve dil sağlayıcısı ayarları compiler configuration öğeleri için kullanılabilen dil sağlayıcısı belirtin.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="6ec2e-104">Her derleyici yapılandırma öğesi kod belirtir sağlayıcı türü adı, derleyici parametreleri, desteklenen dil adları ve dosya uzantılarını desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="6ec2e-105">.NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6ec2e-106">Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6ec2e-107">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="6ec2e-108">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="6ec2e-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="6ec2e-109">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="6ec2e-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="6ec2e-110">\<derleyicileri ></span><span class="sxs-lookup"><span data-stu-id="6ec2e-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="6ec2e-111">\<Derleyici ></span><span class="sxs-lookup"><span data-stu-id="6ec2e-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="6ec2e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="6ec2e-112">Element</span></span>|<span data-ttu-id="6ec2e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec2e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ec2e-114">\<System.codeDom ></span><span class="sxs-lookup"><span data-stu-id="6ec2e-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="6ec2e-115">Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="6ec2e-116">\<derleyicileri ></span><span class="sxs-lookup"><span data-stu-id="6ec2e-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="6ec2e-117">Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="6ec2e-118">\<Derleyici ></span><span class="sxs-lookup"><span data-stu-id="6ec2e-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="6ec2e-119">Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ec2e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ec2e-120">Example</span></span>  
 <span data-ttu-id="6ec2e-121">Aşağıdaki örnek tipik derleyici yapılandırma öğesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ec2e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ec2e-122">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="6ec2e-123">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6ec2e-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6ec2e-124">\<Derleyici > öğesi</span><span class="sxs-lookup"><span data-stu-id="6ec2e-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)

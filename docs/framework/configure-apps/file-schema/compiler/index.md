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
# <a name="compiler-and-language-provider-settings-schema"></a>Derleyici ve Dil Sağlayıcısı Ayarları Şeması
Derleyici ve dil sağlayıcısı ayarları compiler configuration öğeleri için kullanılabilen dil sağlayıcısı belirtin. Her derleyici yapılandırma öğesi kod belirtir sağlayıcı türü adı, derleyici parametreleri, desteklenen dil adları ve dosya uzantılarını desteklenir.  
  
 .NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarları tanımlar. Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.  
  
 [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.codeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<Derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.codeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|  
|[\<derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.|  
|[\<Derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tipik derleyici yapılandırma öğesi gösterilmektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)

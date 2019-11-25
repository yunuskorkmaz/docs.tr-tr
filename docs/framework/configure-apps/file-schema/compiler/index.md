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
ms.openlocfilehash: 5b1f9684ad26d4a03769af287fc8b0c0c7c4cc1a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088678"
---
# <a name="compiler-and-language-provider-settings-schema"></a>Derleyici ve Dil Sağlayıcısı Ayarları Şeması
Derleyici ve dil sağlayıcısı ayarları, kullanılabilir dil sağlayıcıları için derleyici yapılandırma öğelerini belirtir. Her derleyici yapılandırma öğesi kod sağlayıcısı türü adını, derleyici parametrelerini, desteklenen dil adlarını ve desteklenen dosya uzantılarını belirtir.  
  
.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar. Geliştiriciler ve derleyici satıcıları, yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulamasının yapılandırma ayarlarını ekleyebilir. Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
[ **\<configuration >** ](../configuration-element.md) \
[**System. codedom >\<** ](system-codedom-element.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyiciler >** ](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyicisi >** ](compiler-element.md)
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[System. CodeDom > \<](system-codedom-element.md)|Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.|  
|[\<derleyiciler >](compilers-element.md)|Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [\<derleyici >](compiler-element.md) öğesi içerir.|  
|[\<derleyicisi >](compiler-element.md)|Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Yapılandırma Dosyası Şeması](../index.md)
- [\<derleyici > öğesi](compiler-element.md)

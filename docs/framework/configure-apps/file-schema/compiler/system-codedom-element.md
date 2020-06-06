---
title: <system.codedom> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155394"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Öğesi
Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="net-framework-version-20"></a>.NET Framework sürüm 2,0  
 [\<system.codedom>](system-codedom-element.md)Öğesi, ve gibi .NET Framework yüklenen varsayılan sağlayıcılara ek olarak bir bilgisayara yüklenen dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> . [\<compilers>](compilers-element.md)Öğe sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor. Her [\<compiler>](compiler-element.md) öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarlarını makine yapılandırma dosyasına (Machine. config) ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> . <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki derleyici yapılandırma ayarları tarafından tanımlanan varsayılan dil sağlayıcılarını ve dil sağlayıcılarını programlama yoluyla numaralandırmak için yöntemini kullanın.  
  
> [!NOTE]
> .NET Framework sürüm 1,0 ve 1,1 ' de, .NET Framework tarafından sağlanan varsayılan dil sağlayıcıları [\<compilers>](compilers-element.md) öğesinde tanımlanmıştır. .NET Framework sürüm 2,0 ' de, varsayılan dil sağlayıcıları [\<compilers>](compilers-element.md) öğesinde tanımlanmaz, ancak yöntemi kullanılarak numaralandırılabilir <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> .  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework sürümleri 1,0 ve 1,1  
 [\<system.codedom>](system-codedom-element.md)Öğesi, bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir. [\<compilers>](compilers-element.md)Öğe sıfır veya daha fazla [\<compiler>](compiler-element.md) öğe içeriyor. Her [\<compiler>](compiler-element.md) öğe, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 .NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar. Geliştiriciler ve derleyici satıcıları, yeni bir uygulama için yapılandırma ayarları ekleyebilir <xref:System.CodeDom.Compiler.CodeDomProvider> . <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yöntemini kullanın.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tipik bir derleyici yapılandırmasını gösterir.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Yapılandırma dosyası şeması](../index.md)
- [Derleyici ve Dil Sağlayıcısı Ayarları Şeması](index.md)
- [\<compiler>Dosyalarında](compiler-element.md)

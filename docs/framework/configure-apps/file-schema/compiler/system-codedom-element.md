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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155394"
---
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
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
|[\<derleyiciler>](compilers-element.md)|Derleyici yapılandırma elemanları için kapsayıcı; sıfır veya daha fazla [ \<derleyici>](compiler-element.md) öğeleri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma>](../configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="net-framework-version-20"></a>.NET Çerçeve Sürüm 2.0  
 [ \<System.codedom>](system-codedom-element.md) öğesi gibi <xref:Microsoft.CSharp.CSharpCodeProvider> .NET Framework ile yüklü varsayılan sağlayıcılarıek bir bilgisayarda yüklü dil sağlayıcıları için derleyici <xref:Microsoft.VisualBasic.VBCodeProvider>yapılandırma ayarları içerir. [ \<Derleyiciler>](compilers-element.md) öğesi sıfır veya daha fazla [ \<derleyici>](compiler-element.md) öğeleri içerir. Her [ \<derleyici>](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için makine yapılandırma dosyasına (Machine.config) yapılandırma ayarları ekleyebilir. Bilgisayardaki <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> derleyici yapılandırma ayarları tarafından tanımlanan varsayılan dil sağlayıcılarını ve dil sağlayıcılarını programlı olarak sayısal olarak sayısalolarak sayısallandırmak için yöntemi kullanın.  
  
> [!NOTE]
> .NET Framework sürümleri 1.0 ve 1.1'de, .NET Framework tarafından sağlanan varsayılan dil sağlayıcıları [ \<derleyiciler>](compilers-element.md) öğesinde tanımlanır. .NET Framework sürüm 2.0'da, varsayılan dil sağlayıcıları [ \<derleyicilerde>](compilers-element.md) öğesinde tanımlanmaz, <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> ancak yöntem kullanılarak numaralandırılabilir.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Çerçeve Sürümleri 1.0 ve 1.1  
 System.codedom>öğesi, bilgisayardaki dil sağlayıcılarıiçin derleyici yapılandırma ayarlarını içerir. [ \<](system-codedom-element.md) [ \<Derleyiciler>](compilers-element.md) öğesi sıfır veya daha fazla [ \<derleyici>](compiler-element.md) öğeleri içerir. Her [ \<derleyici>](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 .NET Framework, makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarlarını tanımlar. Geliştiriciler ve derleyici satıcıları yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarları ekleyebilir. Bilgisayardaki <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı olarak sayısal olarak sayısalolarak sayısallandırmak için yöntemi kullanın.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tipik bir derleyici yapılandırmasını göstermektedir.  
  
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
- [Yapılandırma Dosyası Şeması](../index.md)
- [Derleyici ve Dil Sağlayıcısı Ayarları Şeması](index.md)
- [\<derleyici> Element](compiler-element.md)

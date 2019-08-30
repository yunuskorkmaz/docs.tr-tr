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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168912"
---
# <a name="systemcodedom-element"></a>\<System. CodeDom > öğesi
Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. CodeDom >**  
  
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
|[\<derleyiciler >](compilers-element.md)|Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="net-framework-version-20"></a>.NET Framework sürüm 2,0  
 <xref:Microsoft.CSharp.CSharpCodeProvider> [ System.CodeDom>öğesi,vegibi.NETFrameworkyüklenmişvarsayılansağlayıcılaraekolarakbirbilgisayarayüklenendilsağlayıcılarının\<](system-codedom-element.md) derleyici yapılandırma ayarlarını içerir. <xref:Microsoft.VisualBasic.VBCodeProvider>. Derleyiciler > öğesi sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içeriyor. [ \<](compilers-element.md) [ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarlarını makine yapılandırma dosyasına (Machine. config) ekleyebilir. Bir bilgisayardaki derleyici yapılandırma ayarları tarafından tanımlanan varsayılan dil sağlayıcılarını ve dil sağlayıcılarını programlama yoluyla numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>  
  
> [!NOTE]
> 1,0 ve 1,1 .NET Framework sürümlerinde, .NET Framework tarafından sağlanan varsayılan dil sağlayıcıları [ \<compilers >](compilers-element.md) öğesinde tanımlanmıştır. .NET Framework sürüm 2,0 ' de, varsayılan dil sağlayıcıları [ \<compilers >](compilers-element.md) öğesinde tanımlanmaz, ancak <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> yöntemi kullanılarak Numaralandırılabilir.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework sürümleri 1,0 ve 1,1  
 System. CodeDom > öğesi bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir. [ \<](system-codedom-element.md) Derleyiciler > öğesi sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içeriyor. [ \<](compilers-element.md) [ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 .NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar. Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider> bir uygulama için yapılandırma ayarları ekleyebilir. Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>  
  
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
- [Yapılandırma Dosyası Şeması](../index.md)
- [Derleyici ve Dil Sağlayıcısı Ayarları Şeması](index.md)
- [\<Derleyici > öğesi](compiler-element.md)

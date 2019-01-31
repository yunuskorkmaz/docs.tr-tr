---
title: < System.codedom > öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: e2c65044b99e2d5fda7025f24d1d4c4082ded4ec
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268229"
---
# <a name="systemcodedom-element"></a>\<System.codeDom > öğesi
Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.  
  
 \<Yapılandırma > öğesi  
\<System.codeDom > öğesi  
  
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
|[\<System.codeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="net-framework-version-20"></a>.NET framework sürüm 2.0  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) öğesi .NET Framework ile yüklenmiş gibi varsayılan sağlayıcı yanı sıra bir bilgisayarda yüklü olan dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir <xref:Microsoft.CSharp.CSharpCodeProvider> ve <xref:Microsoft.VisualBasic.VBCodeProvider>. [ \<Derleyiciler >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) sıfır veya daha fazla öğe içeriyor [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri. Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için belirli bir dil sağlayıcısı compiler configuration öznitelikleri belirtir.  
  
 Geliştiriciler ve derleyici satıcıları ekleyebilirsiniz yapılandırma ayarları makine yapılandırma dosyası (Machine.config) için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> programlı olarak varsayılan dil sağlayıcısı ve derleyici yapılandırma ayarlarını bir bilgisayar üzerinde tarafından tanımlanan dil sağlayıcıları numaralandırmak için yöntem.  
  
> [!NOTE]
>  .NET Framework sürümleri 1.0 ve 1.1 .NET Framework tarafından sağlanan sağlayıcıları tanımlanır varsayılan dil olarak [ \<derleyiciler >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi. .NET Framework sürüm 2. 0'da, varsayılan dil sağlayıcıları içinde tanımlanmamış [ \<derleyiciler >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi, ancak kullanarak numaralandırılabilir <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> yöntemi.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework sürümleri 1.0 ve 1.1  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) öğesi bir bilgisayarda dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir. [ \<Derleyiciler >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) sıfır veya daha fazla öğe içeriyor [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri. Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için belirli bir dil sağlayıcısı compiler configuration öznitelikleri belirtir.  
  
 .NET Framework ilk derleyici ayarları makine yapılandırma dosyasındaki (Machine.config) tanımlar. Geliştiriciler ve derleyici satıcıları ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarlarını bir bilgisayardaki program aracılığıyla listeleme yöntemi.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe, makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tipik bir derleyici yapılandırması gösterilmektedir.  
  
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
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Derleyici ve Dil Sağlayıcısı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)

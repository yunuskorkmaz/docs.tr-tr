---
title: "&lt;System.codeDom&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8b223ab6ab742c5b7d3b3d2f5640e99835afe268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemcodedomgt-element"></a>&lt;System.codeDom&gt; öğesi
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
|[\<derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="net-framework-version-20"></a>.NET framework sürüm 2.0  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) öğesi .NET Framework ile gibi yüklenen varsayılan sağlayıcıları yanı sıra bir bilgisayarda yüklü olan dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir <xref:Microsoft.CSharp.CSharpCodeProvider> ve <xref:Microsoft.VisualBasic.VBCodeProvider>. [ \<Derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) sıfır veya daha fazla öğe içeriyor [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri. Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için özgün dil sağlayıcısı compiler configuration öznitelikleri belirtir.  
  
 Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarlarını makine yapılandırma dosyası (Machine.config) yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> varsayılan dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda tarafından tanımlanan dil sağlayıcısı program aracılığıyla listeleme yöntemi.  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1, .NET Framework tarafından sağlanan sağlayıcıları tanımlanır varsayılan dil [ \<derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi. .NET Framework sürüm 2. 0'da, varsayılan dil sağlayıcısı içinde tanımlanmamış [ \<derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi, ancak kullanarak numaralandırılan <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> yöntemi.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework sürüm 1.0 ve 1.1  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) öğesi bir bilgisayar üzerinde dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir. [ \<Derleyicileri >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) sıfır veya daha fazla öğe içeriyor [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri. Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için özgün dil sağlayıcısı compiler configuration öznitelikleri belirtir.  
  
 .NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarları tanımlar. Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tipik derleyici yapılandırma gösterilmektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Derleyici ve dil sağlayıcısı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)

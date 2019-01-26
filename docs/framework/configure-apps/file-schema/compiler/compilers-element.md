---
title: '&lt;derleyiciler&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 7d9deda5e0ffeb95483eebbbb0a63831db08ac0b
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083372"
---
# <a name="ltcompilersgt-element"></a>&lt;derleyiciler&gt; öğesi
Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğeleri.  
  
 \<Yapılandırma >  
\<System.codeDom >  
\<System.codeDom > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ \<Derleyiciler >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) öğesi bir bilgisayarda dil sağlayıcıları için derleyici yapılandırma ayarlarını içerir. Her [ \<derleyici >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) öğesi için belirli bir dil sağlayıcısı compiler configuration öznitelikleri belirtir.  
  
 .NET Framework, makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ve dil sağlayıcısı ayarları tanımlar. Geliştiriciler ve derleyici satıcıları ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarlarını bir bilgisayardaki program aracılığıyla listeleme yöntemi.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe, makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tipik bir derleyici yapılandırma öğesi gösterir.  
  
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
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Derleyici ve Dil Sağlayıcısı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)

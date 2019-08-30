---
title: <compilers> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 5232c5bd2d4fad8104d156bfa86141ceb7f0dd93
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167697"
---
# <a name="compilers-element"></a>\<derleyiciler > öğesi
Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla [ \<derleyici >](compiler-element.md) öğesi içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<derleyiciler >**  
  
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
|[\<Derleyici > öğesi](compiler-element.md)|Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma > öğesi](../configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<System. CodeDom > öğesi](system-codedom-element.md)|Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyiciler > öğesi bir bilgisayardaki dil sağlayıcılarının derleyici yapılandırma ayarlarını içerir. [ \<](compilers-element.md) [ Her\<derleyici >](compiler-element.md) öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.  
  
 .NET Framework, makine yapılandırma dosyasında (Machine. config) ilk derleyici ve dil sağlayıcısı ayarlarını tanımlar. Geliştiriciler ve derleyici satıcıları, yeni <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> bir uygulama için yapılandırma ayarları ekleyebilir. Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için yönteminikullanın.<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.  
  
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
- [Derleyici ve Dil Sağlayıcısı Ayarları Şeması](index.md)
- [\<Derleyici > öğesi](compiler-element.md)

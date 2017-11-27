---
title: "&lt;Derleyici&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8d2562bb37413cd07b4548bbf2bad0b6a9aedbc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilergt-element"></a>&lt;Derleyici&gt; öğesi
Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.  
  
 \<yapılandırma öğesi >  
\<System.codeDom öğesi >  
\<compilers öğesi >  
\<Derleyici > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`compilerOptions`|İsteğe bağlı öznitelik.<br /><br /> Derleme için ek derleyici özgü bağımsız değişkenlerini belirtir. Değerleri `compilerOptions` özniteliği derleyici için derleyici seçenekleri konudaki genellikle listelenir. Visual Studio 2005 belgelerinde derleyici seçenekleri "derleyici seçenekleri" dizinindeki arayarak bulabilirsiniz.|  
|`extension`|Gerekli öznitelik.<br /><br /> Dosya adı uzantıları için dil sağlayıcısı kaynak dosyalar tarafından kullanılan noktalı virgülle ayrılmış bir listesini sağlar. Örneğin, ".cs".|  
|`language`|Gerekli öznitelik.<br /><br /> Dil sağlayıcısı tarafından desteklenen dil adlarını noktalı virgülle ayrılmış bir listesini sağlar. Örneğin, "c#; cs; csharp".|  
|`type`|Gerekli öznitelik.<br /><br /> Sağlayıcı uygulaması içeren derlemenin adını içeren dil sağlayıcısı türü adını belirtir. Tür adı tanımlanan gereksinimleri karşılaması gerekir [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`warningLevel`|İsteğe bağlı öznitelik.<br /><br /> Varsayılan derleyici uyarı düzeyini belirtir; dil sağlayıcısı olarak hatalar derleme uyarıları değerlendirir düzeyini belirler.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<providerOption > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Derleyici sürüm öznitelikleri için dil sağlayıcısı belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|  
|[\<derleyicileri > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren `<compiler>` öğeleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her `<compiler>` öğesi için özgün dil sağlayıcısı compiler configuration öznitelikleri belirtir. Sağlayıcı genişletir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil; `<compiler>` öğe, derleyici ve dil sağlayıcısı Kod Oluşturucusu ayarlarını tanımlar.  
  
 .NET Framework makine yapılandırma dosyasındaki (Machine.config) ilk derleyici ayarları tanımlar. Geliştiriciler ve derleyici satıcılar ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarları bir bilgisayarda program aracılığıyla listeleme yöntemi.  
  
 Uygulama veya Web yapılandırma dosyası derleyici öğeleri tamamlayabilir veya makine yapılandırma dosyasındaki ayarları geçersiz kılar. Birden fazla sağlayıcı uygulaması aynı dil adı veya aynı dosya uzantısı için yapılandırılmışsa, son eşleşen yapılandırma tüm önceki yapılandırılmış sağlayıcılarını dil adı veya dosya uzantısı geçersiz kılar.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.  
  
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
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<derleyicileri > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Tam olarak nitelenmiş tür adlarını belirtme](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [compiler Ögesi (ASP.NET Ayarlar Şeması) derleyicileri](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)

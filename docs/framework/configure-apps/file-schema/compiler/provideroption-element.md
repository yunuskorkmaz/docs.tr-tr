---
title: "&lt;providerOption&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f28b7b43f2f782744a0dbc81bd0b91bbbcd8abba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltprovideroptiongt-element"></a>&lt;providerOption&gt; öğesi
Derleyici sürüm öznitelikleri için dil sağlayıcısı belirtir.  
  
 \<yapılandırma öğesi >  
\<system.codedom Element>  
\<compilers Element>  
\<Derleyici > öğesi  
\<providerOption > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli öznitelik.<br /><br /> Seçeneğin adı belirtir; Örneğin, "CompilerVersion".|  
|`value`|Gerekli öznitelik.<br /><br /> Seçeneği için bir değer belirtir; Örneğin, "v3.5".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|  
|[\<derleyicileri > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazla bilgi içeren `<compiler>` öğeleri.|  
|[\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3.5, kod belge nesne modeli (CodeDOM) kod sağlayıcıları sağlayıcıya özel seçenekleri kullanarak destekleyebilir `<providerOption>` öğesi.  
  
 .NET Framework 3.5 güncelleştirilmiş .NET Framework 2.0 bütünleştirilmiş kodları bulunur ve yeni türlerini içeren yeni sürüm 3.5 derlemeleri sağlar. Microsoft C# ve Visual Basic kodu sağlayıcıları .NET Framework 2.0 derlemelerde içeriyor ancak sürüm 3.5 derleyicileri desteklemek üzere güncelleştirilmiştir. Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2.0 derleyicileri için kod oluşturur. Kullanabileceğiniz `<providerOption>` öğesi 3.5 hedef derleyici sürüm olarak değiştirin. Bunu yapmak için "CompilerVersion" belirtme `name` özniteliği ve için "v3.5" `value` özniteliği. Küçük bir "v" sürüm numarasıyla gelmelidir.  
  
 Sürüm belirtimi genel ekleyerek yapabileceğiniz `<providerOption>` .NET Framework 2.0 Machine.config veya kök Web.config dosyasında öğesi. Machine.config dosyasındaki 3.5 için varsayılan derleyici sürümü güncelleştirirseniz, uygulama başına temelinde 2.0 dön kullanarak değiştirebilirsiniz `<providerOption>` uygulama yapılandırma dosyasında öğesi.  
  
 CodeDOM kodu sağlayıcısı Implementers alan oluşturucu sağlayarak özel seçenekleri işlenebilecek bir `providerOptions` türünde parametresi <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# kod sağlayıcının 3.5 sürümünün kullanılacağını belirtin gösterilmiştir.  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<derleyicileri > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [compiler Ögesi (ASP.NET Ayarlar Şeması) derleyicileri](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)

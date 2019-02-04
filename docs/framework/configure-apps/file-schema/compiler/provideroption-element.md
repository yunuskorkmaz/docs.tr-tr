---
title: <providerOption> Öğesi
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: bb29ba8721c3aa13fad4410208b1276bdfa761c1
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675276"
---
# <a name="provideroption-element"></a>\<providerOption > öğesi
Derleyici sürümü öznitelikleri için dil sağlayıcısı belirtir.  
  
 \<yapılandırma öğesi >  
\<system.codedom Element>  
\<compilers öğesi >  
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
|`name`|Gerekli öznitelik.<br /><br /> Seçenek adını belirtir. Örneğin, "CompilerVersion".|  
|`value`|Gerekli öznitelik.<br /><br /> Seçeneği için bir değer belirtir. Örneğin, "v3.5".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|  
|[\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren `<compiler>` öğeleri.|  
|[\<Derleyici > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3.5, kod belge nesne modeli (CodeDOM) kod sağlayıcıları sağlayıcıya özel seçenekleri kullanarak destekleyebilir `<providerOption>` öğesi.  
  
 .NET Framework 3.5 güncelleştirilmiş .NET Framework 2.0 derlemeleri içerir ve yeni türleri içeren yeni sürüm 3.5 derlemeler sağlar. Microsoft C# ve Visual Basic kod sağlayıcıları, .NET Framework 2.0 derlemelerinde toplanır, ancak sürüm 3.5 derleyicileri desteklemek üzere güncelleştirilmiştir. Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2.0 derleyicileri için kod oluşturur. Kullanabileceğiniz `<providerOption>` hedef derleyici sürümü 3.5 değiştirmek için öğesi. Bunu yapmak için "CompilerVersion" belirtin `name` özniteliği ve "v3.5" `value` özniteliği. Bir küçük harf "v" sürüm numarasıyla gelmelidir.  
  
 Sürüm belirtimi genel ekleyerek yapabileceğiniz `<providerOption>` .NET Framework 2.0 Machine.config veya Web.config dosyası kök öğesi. Varsayılan derleyici sürümü 3.5 Machine.config dosyasında güncelleştirirseniz, bunu uygulama başına temelinde 2.0 dön kullanarak değiştirebilirsiniz `<providerOption>` uygulama yapılandırma dosyasında öğesi.  
  
 CodeDOM kod sağlayıcısı uygulayıcılar, alan bir oluşturucu sağlayarak özel seçenekleri işlenebilecek bir `providerOptions` türünde parametre <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# kod sağlayıcının 3.5 sürümünün kullanılması gerektiğini belirtmek gösterilmektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [derleme (ASP.NET Settings Schema) yönelik derleyiciler için derleyici öğesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))

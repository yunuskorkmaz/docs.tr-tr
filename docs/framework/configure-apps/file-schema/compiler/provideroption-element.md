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
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155407"
---
# <a name="provideroption-element"></a>\<providerOption> Öğesi
Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<derleyiciler>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<derleyici>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

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
|`name`|Gerekli öznitelik.<br /><br /> Seçeneğin adını belirtir; örneğin, "CompilerVersion".|  
|`value`|Gerekli öznitelik.<br /><br /> Opsiyonun değerini belirtir; örneğin, "v3.5".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma> Element](../configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<system.codedom> Element](system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|  
|[\<derleyiciler> Element](compilers-element.md)|Derleyici yapılandırma elemanları için kapsayıcı; sıfır veya `<compiler>` daha fazla öğe içerir.|  
|[\<derleyici> Element](compiler-element.md)|Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3.5'te, Code Document Object Model (CodeDOM) kod `<providerOption>` sağlayıcıları, öğeyi kullanarak sağlayıcıya özgü seçenekleri destekleyebilir.  
  
 .NET Framework 3.5 güncelleştirilmiş .NET Framework 2.0 derlemelerini içerir ve yeni türler içeren yeni sürüm 3.5 derlemeleri sağlar. Microsoft C# ve Visual Basic kod sağlayıcıları .NET Framework 2.0 derlemelerinde bulunur, ancak sürüm 3.5 derleyicilerini destekleyecek şekilde güncelleştirilmiştir. Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2.0 derleyicileri için kod oluşturur. `<providerOption>` Hedef derleyici sürümünü 3,5 olarak değiştirmek için öğeyi kullanabilirsiniz. Bunu yapmak için öznitelik için "DerleyiciSürümü" ve öznitelik `name` için `value` "v3.5" belirtin. Sürüm numarasından daha küçük bir "v" ile önce olmalısınız.  
  
 `<providerOption>` .NET Framework 2.0 Machine.config veya root Web.config dosyasına öğeyi ekleyerek sürüm belirtimini genel hale getirebilirsiniz. Varsayılan derleyici sürümünü Machine.config dosyasında 3,5 olarak güncellerseniz, uygulama yapılandırma dosyasındaki öğeyi `<providerOption>` kullanarak uygulama başına olarak 2.0 olarak değiştirebilirsiniz.  
  
 CodeDOM kod sağlayıcı uygulayıcıları türü `providerOptions` <xref:System.Collections.Generic.IDictionary%602>bir parametre alır bir oluşturucu sağlayarak özel seçenekleri işleyebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# kod sağlayıcısının 3.5 sürümünün nasıl kullanılması gerektiğini gösterir.  
  
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
- [Yapılandırma Dosyası Şeması](../index.md)
- [\<derleyiciler> Element](compilers-element.md)
- [Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [derleyici Öğesi derleme için (ASP.NET Ayarlar Şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))

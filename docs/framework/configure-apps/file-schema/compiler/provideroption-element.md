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
ms.openlocfilehash: 8d90364e34aa15bbd38e82ec70ec44616d7360f8
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167662"
---
# <a name="provideroption-element"></a>\<providerOption > öğesi
Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. CodeDom >** ](system-codedom-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyiciler >** ](compilers-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Derleyici >** ](compiler-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<providerOption >**  
  
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
|`name`|Gerekli öznitelik.<br /><br /> Seçeneğin adını belirtir; Örneğin, "CompilerVersion".|  
|`value`|Gerekli öznitelik.<br /><br /> Seçenek için değeri belirtir; Örneğin, "v 3.5".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma > öğesi](../configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|[\<System. CodeDom > öğesi](system-codedom-element.md)|Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.|  
|[\<derleyiciler > öğesi](compilers-element.md)|Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğe içeriyor.|  
|[\<Derleyici > öğesi](compiler-element.md)|Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 3,5 ' de, kod belge nesne modeli (CodeDom) kod sağlayıcıları `<providerOption>` öğesini kullanarak sağlayıcıya özgü seçenekleri destekleyebilir.  
  
 .NET Framework 3,5, güncelleştirilmiş .NET Framework 2,0 derlemelerini içerir ve yeni türler içeren yeni sürüm 3,5 derlemeleri sağlar. Microsoft C# ve Visual Basic kod sağlayıcıları .NET Framework 2,0 Derlemeleriyle bulunur, ancak sürüm 3,5 derleyicileri destekleyecek şekilde güncelleştirilmiştir. Varsayılan olarak, güncelleştirilmiş kod sağlayıcıları sürüm 2,0 derleyicileri için kod üretir. Hedef derleyici sürümünü 3,5 `<providerOption>` olarak değiştirmek için öğesini kullanabilirsiniz. Bunu yapmak için, özniteliği için "CompilerVersion" `name` ve `value` öznitelik için "v 3.5" belirtin. Sürüm numarasından önce küçük bir "v" olması gerekir.  
  
 .NET Framework 2,0 Machine. config veya root Web. config `<providerOption>` dosyasına öğesini ekleyerek sürüm belirtimini Global hale getirebilirsiniz. Machine. config dosyasında varsayılan derleyici sürümünü 3,5 olarak güncelleştirirseniz, uygulama yapılandırma dosyasındaki `<providerOption>` öğesini kullanarak uygulama başına temelinde yeniden 2,0 olarak değiştirebilirsiniz.  
  
 CodeDOM kod sağlayıcısı uygulayıcıları, türünde `providerOptions` <xref:System.Collections.Generic.IDictionary%602>bir parametre alan bir Oluşturucu sağlayarak özel seçenekleri işleyebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C# kod sağlayıcısının 3,5 sürümünün kullanılması gerektiğini belirtir.  
  
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
- [\<derleyiciler > öğesi](compilers-element.md)
- [Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))

---
title: <compiler> Öğesi
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 46676f25597f85596598d6f67c98930971cb0447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088050"
---
# <a name="compiler-element"></a>\<derleyici > öğesi

Bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir.

[ **\<configuration >** ](../configuration-element.md) \
[**System. codedom >\<** ](system-codedom-element.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<derleyiciler >** ](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<derleyicisi >**

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
|`compilerOptions`|İsteğe bağlı öznitelik.<br /><br /> Derleme için derleyiciye özgü ek bağımsız değişkenleri belirtir. `compilerOptions` özniteliği için değerler, genellikle derleyicinin derleyici seçenekleri konusunda listelenir.|
|`extension`|Gerekli öznitelik.<br /><br /> Dil sağlayıcısı için kaynak dosyalar tarafından kullanılan, noktalı virgülle ayrılmış dosya adı uzantılarının bir listesini sağlar. Örneğin, ". cs".|
|`language`|Gerekli öznitelik.<br /><br /> Dil sağlayıcısı tarafından desteklenen dil adlarının noktalı virgülle ayrılmış bir listesini sağlar. Örneğin, "c#; CS; CSharp".|
|`type`|Gerekli öznitelik.<br /><br /> Sağlayıcı uygulamasını içeren derlemenin adı da dahil olmak üzere, dil sağlayıcısının tür adını belirtir. Tür adı, [tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)tanımlanan gereksinimlere uymalıdır.|
|`warningLevel`|İsteğe bağlı öznitelik.<br /><br /> Varsayılan derleyici uyarı düzeyini belirtir; Dil sağlayıcısının derleme uyarılarını hata olarak değerlendirme düzeyini belirler.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<providerOption > öğesi](provideroption-element.md)|Bir dil sağlayıcısı için derleyici sürüm özniteliklerini belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<Yapılandırma > öğesi](../configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|[System. CodeDom > öğesi \<](system-codedom-element.md)|Kullanılabilir dil sağlayıcılarının derleyici yapılandırma ayarlarını belirtir.|
|[\<derleyiciler > öğesi](compilers-element.md)|Derleyici yapılandırma öğeleri için kapsayıcı; sıfır veya daha fazla `<compiler>` öğesi içerir.|

## <a name="remarks"></a>Açıklamalar

Her `<compiler>` öğesi, belirli bir dil sağlayıcısı için derleyici yapılandırma özniteliklerini belirtir. Sağlayıcı, belirli bir dil için <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfını genişletir; `<compiler>` öğesi, dil sağlayıcısı için derleyici ve kod Oluşturucu ayarlarını tanımlar.

.NET Framework, makine yapılandırma dosyasındaki (Machine. config) ilk derleyici ayarlarını tanımlar. Geliştiriciler ve derleyici satıcıları, yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulamasının yapılandırma ayarlarını ekleyebilir. Bir bilgisayardaki dil sağlayıcısını ve derleyici yapılandırma ayarlarını programlı bir şekilde numaralandırmak için <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> yöntemini kullanın.

Uygulama veya Web yapılandırma dosyasındaki derleyici öğeleri, makine yapılandırma dosyasındaki ayarları tamamlayabilir veya geçersiz kılabilir. Aynı dil adı veya aynı dosya uzantısı için birden fazla sağlayıcı uygulamanız yapılandırılmışsa, son eşleştirme yapılandırması söz konusu dil adı veya dosya uzantısı için önceden yapılandırılmış tüm sağlayıcıları geçersiz kılar.

## <a name="configuration-file"></a>Yapılandırma Dosyası

Bu öğe makine yapılandırma dosyasında ve uygulama yapılandırma dosyasında kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek tipik bir derleyici yapılandırma öğesini göstermektedir:

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Yapılandırma Dosyası Şeması](../index.md)
- [\<derleyiciler > öğesi](compilers-element.md)
- [Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [derleme için derleyiciler için derleyici öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))

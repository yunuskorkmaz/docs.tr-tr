---
title: '&lt;Derleyici&gt; öğesi'
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
ms.openlocfilehash: cc0cac18b46abd2c9738420ca635a5d81c2c4b83
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083814"
---
# <a name="ltcompilergt-element"></a>&lt;Derleyici&gt; öğesi

Compiler configuration öznitelikleri için dil sağlayıcısı belirtir.

\<yapılandırma öğesi > \<system.codedom öğesi > \<compilers öğesi > \<derleyici > öğesi

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
|`compilerOptions`|İsteğe bağlı öznitelik.<br /><br /> Derleme için ek derleyici özel bağımsız değişkenler belirtir. Değerleri `compilerOptions` özniteliği derleyicisi için derleyici seçeneklerini konularında genellikle listelenir.|
|`extension`|Gerekli öznitelik.<br /><br /> Dosya adı uzantıları için dil sağlayıcısı kaynak kodları tarafından kullanılan noktalı virgülle ayrılmış bir listesini sağlar. Örneğin, ".cs".|
|`language`|Gerekli öznitelik.<br /><br /> Dil sağlayıcısı tarafından desteklenen dil adları noktalı virgülle ayrılmış bir listesini sağlar. Örneğin, "c#; cs; csharp".|
|`type`|Gerekli öznitelik.<br /><br /> Sağlayıcısı uygulamasını içeren derlemenin adı dahil olmak üzere, bir dil sağlayıcısı türü adını belirtir. Tür adı tanımlanan gereksinimlerini karşılaması gerekir [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|
|`warningLevel`|İsteğe bağlı öznitelik.<br /><br /> Varsayılan derleyici uyarı düzeyini belirtir. ve dil sağlayıcısı derleme uyarılarını hata olarak değerlendirir düzeyini belirler.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<providerOption > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Derleyici sürümü öznitelikleri için dil sağlayıcısı belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|[\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Kullanılabilir dil sağlayıcıları için derleyici yapılandırma ayarlarını belirtir.|
|[\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Compiler configuration öğeleri için kapsayıcı; sıfır veya daha fazlasını içeren `<compiler>` öğeleri.|

## <a name="remarks"></a>Açıklamalar

Her `<compiler>` öğesi için belirli bir dil sağlayıcısı compiler configuration öznitelikleri belirtir. Sağlayıcı genişletir <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> sınıfı belirli bir dil; `<compiler>` öğe, derleyici ve dil sağlayıcısı için kod Oluşturucu ayarları tanımlar.

.NET Framework ilk derleyici ayarları makine yapılandırma dosyasındaki (Machine.config) tanımlar. Geliştiriciler ve derleyici satıcıları ekleyebilirsiniz yapılandırma ayarları için yeni bir <xref:System.CodeDom.Compiler.CodeDomProvider> uygulaması. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> dil sağlayıcısı ve derleyici yapılandırma ayarlarını bir bilgisayardaki program aracılığıyla listeleme yöntemi.

Bir uygulama ya da Web yapılandırma dosyası derleyici öğeleri tamamlayabilir veya makine yapılandırma dosyasındaki ayarları geçersiz kılar. Son eşleşen yapılandırma sağlayıcısı uygulamasında birden fazla aynı dil adı veya dosya uzantısına için yapılandırılmışsa, bu dil adı veya dosya uzantısı için önceki tüm yapılandırılmış sağlayıcılarını geçersiz kılar.

## <a name="configuration-file"></a>Yapılandırma Dosyası

Bu öğe, makine yapılandırma dosyası ve uygulama yapılandırma dosyasında kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, tipik bir derleyici yapılandırma öğesi gösterilmektedir:

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
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<System.codeDom > öğesi](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [derleme (ASP.NET Settings Schema) yönelik derleyiciler için derleyici öğesi](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))

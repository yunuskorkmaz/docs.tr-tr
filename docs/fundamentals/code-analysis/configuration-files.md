---
title: Kod analizi kuralları için yapılandırma dosyaları
description: Kod analizi kurallarını yapılandırmak için farklı yapılandırma dosyaları hakkında bilgi edinin.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0d64df42ffb1763afed3e883c4f043755e158489
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633994"
---
# <a name="configuration-files-for-code-analysis-rules"></a>Kod analizi kuralları için yapılandırma dosyaları

Kod analizi kuralları çeşitli [yapılandırma seçeneklerine](configuration-options.md)sahiptir. Bu seçenekleri aşağıdaki çözümleyici yapılandırma dosyalarından birinde anahtar-değer çiftleri olarak belirtirsiniz:

- [EditorConfig](#editorconfig) Dosya: dosya tabanlı veya klasör tabanlı yapılandırma seçenekleri.
- [Global analiz Zerconfig](#global-analyzerconfig) dosyası: proje düzeyi yapılandırma seçenekleri.

## EditorConfig

[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) dosyalar, **belirli kaynak dosyalara veya klasörlere uygulanan seçenekleri** sağlamak için kullanılır. Seçenekler, uygulanabilir dosya ve klasörleri tanımlamak için bölüm üstbilgileri altına yerleştirilir. Yapılandırmak istediğiniz her kural için bir giriş ekleyin ve bunu karşılık gelen dosya uzantısı bölümüne yerleştirin, örneğin, `[*.cs]` .

```ini
[*.cs]
<option_name> = <option_value>
```

Yukarıdaki örnekte, `[*.cs]` `.cs` alt klasörler dahil olmak üzere geçerli klasörde dosya uzantısına sahip tüm C# dosyalarını seçmek için bir editorconfig bölüm üst bilgisi vardır. Sonraki giriş, `<option_name> = <option_value>` tüm C# dosyalarına uygulanacak bir çözümleyici seçeneğidir.

Dosyayı EditorConfig ilgili dizine yerleştirerek bir klasöre, projeye veya tüm depoya dosya kuralları uygulayabilirsiniz. Bu seçenekler, derleme zamanında analiz yürütülürken ve Visual Studio 'da kodu düzenlerken uygulanır.

Eğer girinti boyutu gibi düzenleyici ayarları için mevcut bir *. editorconfig* dosyanız varsa veya sondaki boşluğu kırpıp kırpmak için, kod analizi yapılandırma seçeneklerinizi aynı dosyaya yerleştirebilirsiniz.

> [!TIP]
> Visual Studio, bu dosyalardan birini projenize eklemenin kolay hale getiren bir *. editorconfig* öğesi şablonu sağlar. Daha fazla bilgi için bkz. [ EditorConfig bir projeye dosya ekleme](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

### <a name="example"></a>Örnek

Aşağıda, EditorConfig seçenekleri ve kural önem derecesini yapılandırmak için örnek bir dosya verilmiştir:

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a>Küresel analiz Zerconfig

.NET 5 SDK ile başlayarak (Visual Studio 2019 sürüm 16,8 ve sonraki sürümlerinde desteklenir), çözümleyici seçeneklerini genel _analiz Zeri yapılandırma_ dosyalarıyla de yapılandırabilirsiniz. Bu dosyalar, dosya adlarından veya dosya yollarından bağımsız olarak **bir projedeki tüm kaynak dosyalara uygulanan seçenekleri** sağlamak için kullanılır.

[EditorConfig](#editorconfig)Dosyaların aksine, genel yapılandırma dosyaları, girinti boyutu ya da sondaki boşluğu kırpıp kırpılıp Kırpılanmayacağı gibi, IDEs için düzenleyici stil ayarlarını yapılandırmak için kullanılamaz. Bunun yerine, yalnızca proje düzeyi çözümleyici yapılandırma seçeneklerini belirtmek için tasarlanırlar.

### <a name="format"></a>Biçimlendir

EditorConfigİlgili dosya ve klasörleri tanımlamak için gibi bölüm üst bilgileri olması gereken dosyaların aksine, `[*.cs]` genel analiz zerconfig dosyaları bölüm üst bilgilerine sahip değildir. Bunun yerine, `is_global = true` normal dosyalardan ayırt edilebilmesi için formun en üst düzey bir girişi gerekir EditorConfig . Bu, dosyadaki tüm seçeneklerin Projenin tamamına uygulanacağını gösterir. Örnek:

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a>Adlandırma

EditorConfigAdlandırılmış olması gereken dosyaların aksine `.editorconfig` , genel yapılandırma dosyalarının belirli bir ad veya uzantıya sahip olması gerekmez. Ancak, bu dosyaları olarak ayarlarsanız, `.globalconfig` alt klasörler dahil olmak üzere geçerli klasör içindeki tüm C# ve Visual Basic projelerine örtülü olarak uygulanır. Aksi takdirde, `GlobalAnalyzerConfigFiles` öğeyi MSBuild proje dosyanıza açıkça eklemeniz gerekir:

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> `is_global = true`Dosya adlandırılsa bile en üst düzey giriş gereklidir `.globalconfig` .

### <a name="example"></a>Örnek

Aşağıda, proje düzeyinde seçenekleri ve kural önem derecesini yapılandırmak için örnek bir genel analiz Zerconfig dosyası verilmiştir:

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a>Önceliği

Hem EditorConfig dosyalar hem de Global analist yapılandırma dosyaları her seçenek için bir anahtar-değer çifti belirtir. Aynı anahtara ancak farklı değerlere sahip birden fazla giriş olduğunda çakışmalar oluşur.

### <a name="general-options"></a>Genel seçenekler

Seçenekler arasında çakışmalar meydana geldiğinde, çakışmaları çözmek için aşağıdaki öncelik kuralları kullanılır:

- Aynı yapılandırma dosyasındaki çakışan girişler: dosyanın daha sonra WINS olarak görünen giriş. Bu, tek bir EditorConfig dosyadaki ve aynı zamanda tek bir genel analiz Zeri yapılandırma dosyasında bulunan çakışan girişler için geçerlidir.

- İki dosyada çakışan girişler EditorConfig : dosya EditorConfig sisteminde daha derin olan ve dolayısıyla daha uzun bir dosya yoluna sahip olan giriş.

- İki genel analiz Zeri yapılandırma dosyasında çakışan girişler: bir derleyici uyarısı bildirilir ve her iki giriş de yok sayılır.

- Bir EditorConfig dosyadaki ve genel analiz Zeri yapılandırma dosyasında çakışan girişler: EditorConfig dosyadaki giriş kazanır.

### <a name="severity-options"></a>Önem derecesi seçenekleri

Önceki [genel öncelik kuralları](#general-options) yapılandırma dosyalarında belirtilen tüm seçenekler için geçerlidir. [Önem derecesi yapılandırma](configuration-options.md#severity-level) seçenekleri için aşağıdaki ek öncelik kuralları geçerlidir:

- Komut satırında, derleyici seçenekleri (veya) olarak belirtilen önem derecesi seçenekleri, `/nowarn` `/warnaserror` ve genel analiz Zeri yapılandırma dosyalarında belirtilen [önem derecesi yapılandırma](configuration-options.md#severity-level) seçeneklerini her zaman geçersiz kılar EditorConfig .

- Önem derecesi seçenekleri bir [RuleSet](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) dosyası ile de belirtilebilir. Ancak, RuleSets dosyaları EditorConfig ve genel analiz Zeri yapılandırma dosyalarında kullanım dışı bırakılmıştır. [RuleSet dosyalarını eşdeğer bir EditorConfig dosyaya dönüştürmeniz](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)önerilir. Bir RuleSet dosyası ve EditorConfig ya da Global analist yapılandırma dosyalarından çakışan önem derecesine yönelik öncelik _tanımsızdır_.

- Farklı anahtarlarla ilgili önem derecesi seçeneklerinin öncelik kuralları hakkında bilgi için, örneğin, tek bir kural için farklı önem dereceleri belirtildiğinde ve kuralın altında bulunduğu kategori için, bkz. [Kod Analizi Için yapılandırma seçenekleri](configuration-options.md#precedence).

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig vs genel analiz Zerconfig tasarım sorunu](https://github.com/dotnet/roslyn/issues/47707)

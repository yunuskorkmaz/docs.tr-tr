---
title: Kod analizi kurallarını yapılandırma
description: Bir çözümleyici yapılandırma dosyasında kod analizi kurallarını yapılandırmayı öğrenin.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: c1992b32e5159e9bf7ae4d00b92a5baa7f7c1b8c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876623"
---
# <a name="configuration-options-for-code-analysis"></a>Kod analizi için yapılandırma seçenekleri

Kod analizi kuralları çeşitli yapılandırma seçeneklerine sahiptir. Bu seçenekler, bir [çözümleyici yapılandırma dosyasında](configuration-files.md) sözdizimi kullanılarak anahtar-değer çiftleri olarak belirtilir `<option key> = <option value>` .

Yapılandıracağımız en yaygın seçenek, bir [kuralın önem derecesine](#severity-level)sahiptir. [Kod kalitesi kuralları](quality-rules/index.md) ve [kod stili kuralları](style-rules/index.md)da dahil olmak üzere tüm çözümleyici kuralları için önem derecesini yapılandırabilirsiniz. Örneğin, bir kuralı uyarı olarak etkinleştirmek için aşağıdaki anahtar-değer çiftini bir EditorConfig dosyasına ekleyebilirsiniz.

`dotnet_diagnostic.<rule ID>.severity = warning`

Kural davranışını özelleştirmek için ek seçenekler de yapılandırabilirsiniz:

- Kod kalitesi kuralları, davranışı yapılandırmak için [ek seçeneklere](code-quality-rule-options.md) sahiptir; Örneğin, bir kuralın hangi yöntem adına uygulanacağını.
- Kod stili kuralları [özel kod stili seçeneklerine](code-style-rule-options.md)sahiptir.
- Üçüncü taraf çözümleyici kuralları, özel anahtar adları ve değer biçimleri ile kendi yapılandırma seçeneklerini tanımlayabilir.

Bir [çözümleyici yapılandırma dosyasında](configuration-files.md) belirli bir kuralın önem derecesini yapılandırmak için sözdizimi aşağıdaki gibidir:

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a>Genel seçenekler

Bu seçenekler bir bütün olarak kod analizi için geçerlidir. Yalnızca tek bir kurala veya kural kümesine uygulanamaz.

### <a name="exclude-generated-code"></a>Üretilen kodu hariç tut

`generated_code = true | false` [Yapılandırma dosyanıza](configuration-files.md)bir giriş ekleyerek, oluşturulan kod olarak değerlendirilecek ek dosya ve klasörler yapılandırabilirsiniz. .NET Code Analyzer uyarıları, tasarımcı tarafından oluşturulan dosyalar gibi oluşturulan kod dosyalarında (kullanıcıların herhangi bir ihlali onarmak için düzenleyemeyen) yararlı değildir. Çoğu durumda, kod Çözümleyicileri oluşturulan kod dosyalarını atlar ve bu dosyalarda ihlal bildirmez.

Varsayılan olarak, belirli dosya uzantılarına sahip dosyalar veya otomatik olarak oluşturulan dosya üstbilgileri oluşturulan kod dosyaları olarak kabul edilir. Örneğin, veya ile biten bir dosya adı `.designer.cs` `.generated.cs` üretilen kod olarak kabul edilir. Bu yapılandırma seçeneği, ek adlandırma desenleri belirtmenize olanak tanır.

Örneğin, adı biten tüm dosyaları `.MyGenerated.cs` oluşturulan kodla işlemek için aşağıdaki girişi ekleyin:

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a>Kurala özgü seçenekler

Kurala özgü seçenekler tek bir kurala, bir dizi kurala veya tüm kurallara uygulanabilir. Kurala özgü seçenekler şunlardır:

- [Kural önem derecesi düzeyi](#severity-level)
- [*Kod kalitesi* kurallarına özgü seçenekler](code-quality-rule-options.md)

### <a name="severity-level"></a>Önem derecesi

Aşağıdaki tabloda, [kod kalitesi](quality-rules/index.md) ve [kod stili](style-rules/index.md) kuralları da dahil olmak üzere tüm çözümleyici kuralları için yapılandırabileceğiniz farklı kural önem dereceleri gösterilmektedir.

| Önem derecesi yapılandırma değeri | Derleme zamanı davranışı |
|-|-|
| `error` | İhlaller derleme *hataları* olarak görünür ve yapıların başarısız olmasına neden olur.|
| `warning` | İhlaller derleme *uyarıları* olarak görünür, ancak yapıların başarısız olmasına neden olmaz (uyarıları hata olarak değerlendirmek için bir seçeneğe sahip olmadığınız sürece). |
| `suggestion` | İhlaller derleme *iletileri* olarak ve VISUAL Studio IDE 'de öneri olarak görünür. |
| `silent` | İhlaller kullanıcıya görünür değil. |
| `none` | Kural tamamen bastırılır. |
| `default` | Kuralın varsayılan önem derecesi kullanılır. Her .NET sürümü için varsayılan önem dereceleri, [Roslyn-çözümleyiciler](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)deposunda listelenmiştir. Bu tabloda, "devre dışı" karşılık gelir `none` , "Hidden" öğesine karşılık gelir `silent` ve "bilgi" öğesine karşılık gelir `suggestion` . |

> [!TIP]
> Visual Studio 'da kural oluşturma işlemlerinin nasıl yapılacağı hakkında bilgi için bkz. [önem düzeyleri](/visualstudio/ide/editorconfig-language-conventions#severity-levels).

#### <a name="scope"></a>Kapsam

Tek bir kural için kural önem derecesini ayarlamak için aşağıdaki sözdizimini kullanın.

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

Bir [kural kategorisinin](categories.md)varsayılan kural önem derecesini ayarlamak için aşağıdaki sözdizimini kullanın. Her kuralın kategorisi, tek kural başvuru sayfalarında sağlanır, örneğin, [CA1000](quality-rules/ca1000.md).

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

Tüm çözümleyici kuralları için varsayılan kural önem derecesini ayarlamak için aşağıdaki sözdizimini kullanın.

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

> [!IMPORTANT]
> Bir kural *kategorisi* ya da *Tüm* kurallar için tek bir girdiyle birden çok kural için önem düzeyini yapılandırdığınızda, önem derecesi yalnızca [Varsayılan olarak etkinleştirilen](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)kurallar için geçerlidir. Varsayılan olarak devre dışı bırakılan kuralları etkinleştirmek için şunlardan birini yapmanız gerekir:
>
> - `dotnet_diagnostic.<rule ID>.severity = <severity>`Her kural için bir açık yapılandırma girişi ekleyin.
> - ' İ ayarlayarak *Tüm* kuralları [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) etkinleştirin `AllEnabledByDefault` .

#### <a name="precedence"></a>Önceliği

Aynı kural KIMLIĞINE uygulanabilecek birden fazla önem derecesi yapılandırma girişi varsa, öncelik aşağıdaki sırada seçilir:

- KIMLIĞE göre tek bir kural için bir giriş, bir kategorinin girdisinden önceliklidir.
- Kategori için bir giriş, tüm çözümleyici kuralları için bir girdiden önceliklidir.

Aşağıdaki örneği göz önünde bulundurun; burada [CA1822](/visualstudio/code-quality/ca1822) "Performance" kategorisine sahiptir:

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

Yukarıdaki örnekte, üç önem derecesine sahip olan tüm girişler CA1822 için geçerlidir. Bununla birlikte, belirtilen öncelik kurallarını kullanarak, sonraki girişler üzerinde ilk kural KIMLIĞI tabanlı giriş kazanır. Bu örnekte, CA1822 etkili bir önem derecesine sahip olur `error` . "Performans" kategorisindeki tüm diğer kuralların önem derecesi olacaktır `warning` .

Dosya içi önceliğe nasıl karar verdiği hakkında daha fazla bilgi için [yapılandırma dosyaları makalesinin öncelik bölümüne](configuration-files.md#precedence)bakın.

---
title: Kod kalitesi kuralı yapılandırma seçenekleri
description: Kod kalitesi kuralları için ek yapılandırma seçeneklerini belirtmeyi öğrenin.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2984e73c554e8a1e1b32df9460933f86cc41be
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96588875"
---
# <a name="code-quality-rule-configuration-options"></a>Kod kalitesi kuralı yapılandırma seçenekleri

*Kod kalitesi* kuralları, [önem derecesini yapılandırmanın](configuration-options.md#severity-level)yanı sıra ek yapılandırma seçeneklerine sahiptir. Örneğin, her bir kod kalitesi Çözümleyicisi yalnızca kod tabanınızın belirli bölümlerine uygulanacak şekilde yapılandırılabilir. Bu seçenekleri, kural önem dereceleri [EditorConfig](https://editorconfig.org) ve genel düzenleyici tercihlerini belirttiğiniz aynı dosyaya anahtar-değer çiftleri ekleyerek belirlersiniz.

## <a name="option-scopes"></a>Seçenek kapsamları

Her bir iyileştirme seçeneği, kural kategorisi (örneğin, güvenlik veya tasarım) veya belirli bir kural için tüm kurallar için yapılandırılabilir.

### <a name="all-rules"></a>Tüm kurallar

*Tüm* kurallar için bir seçeneği yapılandırmak için sözdizimi aşağıdaki gibidir:

|Syntax|Örnek|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kuralların kategorisi

Bir kural *kategorisi* (adlandırma, tasarım veya performans gibi) için bir seçenek yapılandırmanın sözdizimi aşağıdaki gibidir:

|Syntax|Örnek|
|-|-|
| dotnet_code_quality. RuleCategory. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Belirli kural

*Belirli* bir kural için bir seçeneği yapılandırmanın sözdizimi aşağıdaki gibidir:

|Syntax|Örnek|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options"></a>Seçenekler

Bu bölümde, kullanılabilir seçeneklerin bazıları listelenir. Kullanılabilir seçeneklerin tam listesini görmek için bkz. [çözümleyici yapılandırması](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md).

### <a name="api_surface"></a>api_surface

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| API yüzeyinin analiz edileceği bölüm | `public`<br/>`internal` veya `friend`<br/>`private`<br/>`all`<br/><br/>Birden çok değeri virgülle ayırın (,) | `public` | [CA1000](quality-rules/ca1000.md) [CA1003](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md)<br/>[CA1012](quality-rules/ca1012.md) [CA1024](quality-rules/ca1024.md) [CA1027](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)<br/>[CA1030](quality-rules/ca1030.md) [CA1036](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)<br/>[CA1043](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)<br/>[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) [CA1058](quality-rules/ca1058.md)<br/>[CA1063](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)<br/>[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [CA1717](quality-rules/ca1717.md)<br/>[CA1720](quality-rules/ca1720.md) [CA1721](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [CA1801](quality-rules/ca1801.md)<br/>[CA1802](quality-rules/ca1802.md) [CA1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)<br/>[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [CA2234](quality-rules/ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Değer döndürmeyen zaman uyumsuz yöntemlerin yoksayılıp yoksayılmayacağı | `true`<br/>`false` | `false` | [CA2007](quality-rules/ca2007.md) |

> [!NOTE]
> Bu seçenek `skip_async_void_methods` önceki bir sürümde adlandırılmıştı.

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Kuraldan tek karakterlik [tür parametrelerinin](../../csharp/programming-guide/generics/generic-type-parameters.md) dışlanıp dışlanmayacağı `S` , örneğin `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](quality-rules/ca1715.md) |

> [!NOTE]
> Bu seçenek `allow_single_letter_type_parameters` önceki bir sürümde adlandırılmıştı.

### <a name="output_kind"></a>output_kind

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Bu tür derlemeyi üreten bir projedeki kodun analiz edilmesi gerektiğini belirtir | Sabit listesinin bir veya daha fazla alanı <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Birden çok değeri virgülle ayırın (,) | Tüm çıktı türleri | [CA2007](quality-rules/ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Çözümlenmesi gereken API 'Ler için gerekli değiştiriciler belirtir | Aşağıdaki izin verilen değiştirici tablosundan bir veya daha fazla değer<br/><br/>Birden çok değeri virgülle ayırın (,) | Her kurala bağlıdır | [CA1802](quality-rules/ca1802.md) |

| İzin verilen değiştirici | Özet |
| --- | --- |
| `none` | Değiştirici gereksinimi yok |
| `static` veya `Shared` | Şöyle bildirilmelidir `static` ( `Shared` Visual Basic) |
| `const` | Şöyle bildirilmelidir `const` |
| `readonly` | Şöyle bildirilmelidir `readonly` |
| `abstract` | Şöyle bildirilmelidir `abstract` |
| `virtual` | Şöyle bildirilmelidir `virtual` |
| `override` | Şöyle bildirilmelidir `override` |
| `sealed` | Şöyle bildirilmelidir `sealed` |
| `extern` | Şöyle bildirilmelidir `extern` |
| `async` | Şöyle bildirilmelidir `async` |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Uzantı yöntemlerinin parametresi için analizin atlanıp engellenip engellenmeyeceğini belirtir `this` | `true`<br/>`false` | `false` | [CA1062](quality-rules/ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Metoda geçirilen bağımsız değişkenleri doğrulayan null denetim doğrulama yöntemlerinin adları null değil | İzin verilen yöntem adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca Yöntem adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm yöntemler dahil)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `M:` | Hiçbiri | [CA1062](quality-rules/ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Ek dize biçimlendirme yöntemlerinin adları | İzin verilen yöntem adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca Yöntem adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm yöntemler dahil)<br/> -Simgenin [belge kimliği biçimindeki](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `M:` | Hiçbiri | [CA2241](quality-rules/ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Tür ve türetilmiş tüm türleri analiz için hariç tutulan türlerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca tür adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm türleri içerir)<br/> -Simgenin [belge kimliği biçimindeki](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `T:` | Hiçbiri | [CA1303](quality-rules/ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Analiz için dışlanan simgelerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm semboller dahil)<br/> -Simgenin [belge kimliği biçiminde](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)tam nitelikli adlar. Her sembol adı, `M:` metotlar için önek, `T:` türlerin öneki ve `N:` ad alanları için önek gibi bir sembol türü öneki gerektirir.<br/> - `.ctor` oluşturucular ve `.cctor` statik oluşturucular için | Hiçbiri | [CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [CA2000](quality-rules/ca2000.md) [CA2100](quality-rules/ca2100.md) [CA2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)<br/>[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)<br/>[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [CA3002](quality-rules/ca3002.md) [CA3003](quality-rules/ca3003.md) [CA3004](quality-rules/ca3004.md)<br/>[CA3005](quality-rules/ca3005.md) [CA3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [CA3010](quality-rules/ca3010.md)<br/>[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)<br/>[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](quality-rules/ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Analiz bağlamında izin verilmeyen simgelerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm semboller dahil)<br/> -Simgenin [belge kimliği biçiminde](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format)tam nitelikli adlar. Her sembol adı, `M:` metotlar için önek, `T:` türlerin öneki ve `N:` ad alanları için önek gibi bir sembol türü öneki gerektirir.<br/> - `.ctor` oluşturucular ve `.cctor` statik oluşturucular için | Hiçbiri | [CA1031](quality-rules/ca1031.md) |

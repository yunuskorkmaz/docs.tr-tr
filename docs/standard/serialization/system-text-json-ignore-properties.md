---
title: İle özellikleri yoksayma System.Text.Json
description: .NET ' te ile serileştirilirken özellikleri nasıl yoksaymayı öğrenin System.Text.Json .
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ed7ef8509d6660bbbbaf194a87aa9d4815143507
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440011"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a>İle özellikleri yoksayma System.Text.Json

C# nesnelerini JavaScript Nesne Gösterimi (JSON) olarak serileştirilirken, varsayılan olarak tüm ortak özellikler serileştirilir. Sonuçta ortaya çıkan JSON 'da görünmesini istemiyorsanız, birkaç seçeneğiniz vardır. Bu makalede, çeşitli ölçütlere göre özellikleri yok saymayı öğreneceksiniz:

::: zone pivot="dotnet-5-0"

* [Bireysel Özellikler](#ignore-individual-properties)
* [Tüm salt okunurdur özellikleri](#ignore-all-read-only-properties)
* [Tüm null değerli özellikler](#ignore-all-null-value-properties)
* [Tüm varsayılan değer özellikleri](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Bireysel Özellikler](#ignore-individual-properties)
* [Tüm salt okunurdur özellikleri](#ignore-all-read-only-properties)
* [Tüm null değerli özellikler](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a>Tek tek özellikleri yoksay

Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
[[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğinin özelliğini ayarlayarak koşullu dışlama belirtebilirsiniz `Condition` . <xref:System.Text.Json.Serialization.JsonIgnoreCondition>Sabit listesi aşağıdaki seçenekleri sağlar:

* `Always` -Özellik her zaman yok sayılır. Hayır `Condition` belirtilmişse, bu seçenek kabul edilir.
* `Never` -Özelliği `DefaultIgnoreCondition` ,, `IgnoreReadOnlyProperties` ve genel ayarlarından bağımsız olarak her zaman serileştirilmiş ve seri durumdan çıkarılmış olur `IgnoreReadOnlyFields` .
* `WhenWritingDefault` -Bir başvuru türü `null` , null yapılabilir bir değer türü `null` veya değer türü ise, bu özellik serileştirme üzerinde yok sayılır `default` .
* `WhenWritingNull` -Bir başvuru türü `null` veya null yapılabilir bir değer türü ise, bu özellik serileştirme üzerinde yok sayılır `null` .

Aşağıdaki örnek, [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğinin özelliğinin kullanımını gösterir `Condition` :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a>Tüm salt okunurdur özellikleri yoksay

Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur. Serileştirilirken tüm salt okunurdur özellikleri yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Bu seçenek yalnızca serileştirme için geçerlidir. Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.

::: zone pivot="dotnet-5-0"
Bu seçenek yalnızca özellikler için geçerlidir. [Alanları serileştirilirken](system-text-json-how-to.md#include-fields)salt okunurdur alanları yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.
::: zone-end

## <a name="ignore-all-null-value-properties"></a>Tüm null değer özelliklerini yoksay

::: zone pivot="dotnet-5-0"
Tüm null değer özelliklerini yok saymak için, <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
Serileştirilirken tüm null değer özelliklerini yok saymak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> `true` Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:

| Özellik             | Değer                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a>Tüm varsayılan değer özelliklerini yoksay

::: zone pivot="dotnet-5-0"
Değer türü özelliklerindeki varsayılan değerlerin serileştirmesini engellemek için, <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

Bu <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> ayar aynı zamanda null değer başvuru türü ve null yapılabilir değer türü özelliklerinin serileştirmesini önler.

::: zone pivot="dotnet-core-3-1"
.NET Core 3,1 ' deki değer türü varsayılanlarına sahip özelliklerin serileştirmesini önleyen yerleşik bir yol yoktur `System.Text.Json` .
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JsonSerializerOptions örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Geçersiz JSON 'a izin ver](system-text-json-invalid-json.md)
* [Tutamaç taşması JSON](system-text-json-handle-overflow.md)
* [Döngüsel başvuruları koru](system-text-json-preserve-references.md)
* [Değişmez türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)

---
title: İle bazı geçersiz JSON türlerine izin verme System.Text.Json
description: .NET 'teki JSON 'dan serileştirirken ve seri durumdan çıkarılırken yorumlara, sondaki virgüller ve tırnak içine alınmış numaralara nasıl izin vereceğinizi öğrenin.
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
ms.openlocfilehash: 60cbb98bb65ee5c1ffdd3043e42a04004530a115
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440010"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a>İle bazı geçersiz JSON türlerine izin verme System.Text.Json

Bu makalede, JSON 'da açıklamalara, sondaki virgüller ve tırnak içine alınmış sayılara ve sayıların dize olarak nasıl yazılacağını öğreneceksiniz.

## <a name="allow-comments-and-trailing-commas"></a>Yorumlara ve sondaki virgülleri izin ver

Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez. JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak ayarlayın `JsonCommentHandling.Skip` .
Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` . Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a>Tırnak işaretleri halinde izin ver veya yaz

::: zone pivot="dotnet-5-0"

Bazı serileştiriciler sayıları JSON dizeleri (tırnak işaretleriyle çevrelenmiş) olarak kodlayabilir.

Örnek:

```json
{
    "DegreesCelsius": "23"
}
```

Onun yerine:

```json
{
    "DegreesCelsius": 23
}
```

Tırnak işaretleri içindeki sayıları seri hale getirmek veya giriş nesnesi grafiğinin tamamına tırnak içinde kabul etmek için <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi ayarlayın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

`System.Text.Json`ASP.NET Core aracılığıyla dolaylı olarak kullandığınızda, ASP.NET Core [Web varsayılan seçeneklerini](xref:System.Text.Json.JsonSerializerDefaults.Web)belirttiğinden, serisi kaldırılırken tırnak işaretli sayılara izin verilir.

Belirli özellikler, alanlar veya türler için tırnak işaretli sayılara izin vermek veya yazmak için [[Jsonnumberhandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) özniteliğini kullanın.
::: zone-end

::: zone pivot="dotnet-core-3-1"
`System.Text.Json` .NET Core 3,1, tırnak işaretleriyle çevrelenen sayıları serileştirmek veya seri durumdan çıkarmayı desteklemez. Daha fazla bilgi için bkz. [tekliflere Izin verme veya yazma numaraları](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JsonSerializerOptions örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksay](system-text-json-ignore-properties.md)
* [Tutamaç taşması JSON](system-text-json-handle-overflow.md)
* [Döngüsel başvuruları koru](system-text-json-preserve-references.md)
* [Değişmez türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)

---
title: İle eşleşme büyük/küçük harf duyarsız Özellik adı etkinleştirme System.Text.Json
description: .NET 'teki JSON 'a serileştirirken ve seri durumdan çıkarılırken büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4bd57d32120f51ffd1ff09c9817edbafa28a3f19
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440008"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a>İle eşleşme büyük/küçük harf duyarsız Özellik adı etkinleştirme System.Text.Json

Bu makalede, ad alanıyla büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi nasıl etkinleştireceğinizi öğreneceksiniz `System.Text.Json` .

## <a name="case-insensitive-property-matching"></a>Büyük/küçük harfe duyarsız Özellik eşleştirme

Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar. Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :

> [!NOTE]
> [Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) , büyük/küçük harfe duyarlıdır.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir. Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JsonSerializerOptions örneğini oluşturma](system-text-json-configure-options.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksay](system-text-json-ignore-properties.md)
* [Geçersiz JSON 'a izin ver](system-text-json-invalid-json.md)
* [Tutamaç taşması JSON](system-text-json-handle-overflow.md)
* [Döngüsel başvuruları koru](system-text-json-preserve-references.md)
* [Değişmez türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)

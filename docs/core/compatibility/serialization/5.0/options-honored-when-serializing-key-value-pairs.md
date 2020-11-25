---
title: 'Son değişiklik: PropertyNamingPolicy, Propertynamecaseduyarsız ve encoder seçenekleri anahtar-değer çiftleri için kabul edilir'
description: Bir anahtar-değer çifti örneğinin anahtar ve değer özellik adlarını serileştirilirken ve seri durumdan çıkarılırken, PropertyNamingPolicy, Propertynamecaseduyarsız ve kodlayıcı seçeneklerinin kabul edildiği .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 5d75cb7feea32cc4b942e5261c5b609e00a5082c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761633"
---
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a>Anahtar-değer çiftlerini serileştirmek ve seri durumdan çıkarılırken PropertyNamingPolicy, Propertynamecaseduyarsız ve kodlayıcı seçenekleri kabul edilir

<xref:System.Text.Json.JsonSerializer> Şimdi, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> <xref:System.Text.Json.JsonSerializerOptions.Encoder> <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> bir örneğin ve özellik adlarını serileştirilirken, ve seçeneklerini görürsünüz <xref:System.Collections.Generic.KeyValuePair%602> . Ayrıca, <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> örneklerin serisini kaldırırken ve seçeneklerini de kabul eder <xref:System.Collections.Generic.KeyValuePair%602> .

## <a name="change-description"></a>Açıklamayı Değiştir

### <a name="serialization"></a>Serileştirme

.NET Core 3. x sürümlerinde ve [ NuGet paketindekiSystem.Text.Js](https://www.nuget.org/packages/System.Text.Json)4.6.0-4.7.2 sürümlerinde, <xref:System.Collections.Generic.KeyValuePair%602> örneklerin özellikleri herhangi bir ve seçenekten bağımsız olarak her zaman "Key" ve "Value" olarak serileştirilir <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> . Aşağıdaki kod örneği, <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> belirtilen özellik adlandırma ilkesi tarafından önerilse de, Serileştirmeden sonra, ve özelliklerinin nasıl Camel bir şekilde olduğunu gösterir. *not*

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

.NET 5,0 ' den başlayarak, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> ve <xref:System.Text.Json.JsonSerializerOptions.Encoder> seçenekleri, örnekleri serileştirilirken kabul edilir <xref:System.Collections.Generic.KeyValuePair%602> . Aşağıdaki kod örneği, <xref:System.Collections.Generic.KeyValuePair%602.Key> ve <xref:System.Collections.Generic.KeyValuePair%602.Value> özelliklerinin, belirtilen özellik adlandırma ilkesine uygun olarak serileştirme sonrasında nasıl Camel olduğunu gösterir.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a>Seri

.NET Core 3. x sürümlerinde ve [ NuGet paketindekiSystem.Text.Js](https://www.nuget.org/packages/System.Text.Json)4.7. x SÜRÜMLERINDE, <xref:System.Text.Json.JsonException> JSON Özellik adları tam olarak `Key` ve `Value` Örneğin büyük harfle başlamadıklarında oluşturulur. Özel durum, belirtilen bir özellik adlandırma ilkesi açıkça izin veriyorsa bile oluşturulur.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

.NET 5,0 ' den başlayarak, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> ve <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> seçenekleri kullanılarak seri durumdan çıkarılırken kabul edilir <xref:System.Text.Json.JsonSerializer> . Örneğin, aşağıdaki kod parçacığı, <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> belirtilen özellik adlandırma ilkesi izin verdiğinden, küçük harf ve özellik adlarının başarıyla serisini kaldırma işlemi gösterir.

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

Önceki sürümlerle seri hale getirilen yüklere uyum sağlamak için, "Key" ve "Value", serisi kaldırılırken eşleşmesi için özel olarak tasarlanmıştır. <xref:System.Collections.Generic.KeyValuePair%602.Key>Ve <xref:System.Collections.Generic.KeyValuePair%602.Value> özellik adları, aşağıdaki kod örneğinde yer almayan bir seçeneğe göre Camel değildir <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> .

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="reason-for-change"></a>Değişiklik nedeni

Önemli müşteri geri bildirimi, kullanılması <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> gerektiğini belirtti. <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> <xref:System.Text.Json.JsonSerializerOptions.Encoder> <xref:System.Collections.Generic.KeyValuePair%602> Tüm DIĞER düz eski CLR nesneleri (POCO) ile aynı şekilde işlenebilmesi için, ve seçenekleri de kabul edilir.

## <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik sizin için kesintiye uğradıysanız, istenen semantiğini uygulayan [özel bir dönüştürücü](../../../../standard/serialization/system-text-json-converters-how-to.md) kullanabilirsiniz.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->

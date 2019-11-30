---
ms.openlocfilehash: 7c39fe7ffd59fa7a5564bb45f32a6a2fbe0ddb33
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568127"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a>Utf8JsonWriter içindeki `(string)null` semantiğinin değiştirilmesi

.NET Core 3,0 Preview 7 ' de, null dize <xref:System.Text.Json.Utf8JsonWriter>boş dize olarak kabul edilir. .NET Core 3,0 Preview 8 ' den itibaren, null dize bir özellik adı olarak kullanıldığında bir özel durum oluşturur ve bir değer olarak kullanıldığında JSON null belirtecini yayar.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 7 ' de `null` dize, özellik adlarını yazarken ve değer yazarken `""` olarak değerlendirilir.  

.NET Core 3,0 Preview 8 ' den başlayarak `null` Özellik adı bir `ArgumentNullException`oluşturur ve bir `null` değeri <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> veya <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>çağrısı olarak değerlendirilir.

Aşağıdaki kodu göz önünde bulundurun:

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

.NET Core 3,0 Preview 7 ile çalıştırırsanız, yazıcı aşağıdaki çıktıyı üretir:

```js
[{"":"","prop2":""},""]
```

.NET Core 3,0 Preview 8 ' den itibaren, `writer.WriteString(propertyName1, propertyValue1)` çağrısı bir <xref:System.ArgumentNullException>oluşturur.  `propertyName1 = null` `propertyName1 = string.Empty`ile değiştirilirse çıktı şu şekilde olur:

```js
[{"":null,"prop2":null},null]
```

Bu değişiklik, `null` değerleri için çağrı beklentilerini daha iyi hizalamak üzere yapılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Özellik adlarını ve değerlerini <xref:System.Text.Json.Utf8JsonWriter> sınıfıyla yazarken:

- `null` olmayan dizelerin Özellik adı olarak kullanıldığından emin olun.

- Önceki davranış isteniyorsa, null birleşim çağırma kullanın; Örneğin, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.

- Bir `null` dize değeri için `null` değişmez değer yazılması istenmediğinde, null birleşim çağırma kullanın; Örneğin, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->

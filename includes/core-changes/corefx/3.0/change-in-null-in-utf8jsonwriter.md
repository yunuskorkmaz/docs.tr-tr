---
ms.openlocfilehash: c9547cdc2f127cf13a3610118a26736930fcd8bd
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021627"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a>Utf8JsonWriter `(string)null` semantik değişikliği

.NET Core 3.0 Preview 7'de null string ' <xref:System.Text.Json.Utf8JsonWriter>deki boş dize olarak kabul edilir. .NET Core 3.0 Preview 8 ile başlayarak, null string özellik adı olarak kullanıldığında bir özel durum atar ve değer olarak kullanıldığında JSON null belirteci yakar.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview `null` 7'de, `""` dize hem özellik adlarını yazarken hem de değerler yazarken işlem gördü.  

.NET Core 3.0 Preview 8 `null` ile başlayarak, bir özellik `ArgumentNullException`adı bir ,' atar ve bir `null` değer bir çağrı <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> olarak kabul edilir veya <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.

Aşağıdaki kodu inceleyin:

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

.NET Core 3.0 Preview 7 ile çalıştırılırsa, yazar aşağıdaki çıktıyı üretir:

```js
[{"":"","prop2":""},""]
```

.NET Core 3.0 Preview 8 ile `writer.WriteString(propertyName1, propertyValue1)` başlayarak, bir . <xref:System.ArgumentNullException>  Ile `propertyName1 = null` `propertyName1 = string.Empty`değiştirilirse, çıktı şimdi olacaktır:

```js
[{"":null,"prop2":null},null]
```

Bu değişiklik, arayan ların değerlere `null` yönelik beklentileriyle daha iyi uyumlu hale getirilebilmek için yapıldı.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 8

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Text.Json.Utf8JsonWriter> Sınıfla özellik adları ve değerleri yazarken:

- `null` Olmayan dizeleri özellik adları olarak kullanıldığından emin olun.

- Önceki davranış isteniyorsa, null coalescing çağrı kullanın; örneğin, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.

- Bir `null` `null` dize değeri için bir edebi yazma istif değilse, null coalescing çağırma kullanın; örneğin, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.

#### <a name="category"></a>Kategori

Çekirdek .NET kitaplıkları

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

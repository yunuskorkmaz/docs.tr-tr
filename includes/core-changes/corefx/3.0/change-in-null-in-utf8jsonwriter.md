---
ms.openlocfilehash: 7c39fe7ffd59fa7a5564bb45f32a6a2fbe0ddb33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568127"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="6cfc5-101">Utf8JsonWriter `(string)null` semantik değişikliği</span><span class="sxs-lookup"><span data-stu-id="6cfc5-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="6cfc5-102">.NET Core 3.0 Preview 7'de null string ' <xref:System.Text.Json.Utf8JsonWriter>deki boş dize olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="6cfc5-103">.NET Core 3.0 Preview 8 ile başlayarak, null string özellik adı olarak kullanıldığında bir özel durum atar ve değer olarak kullanıldığında JSON null belirteci yakar.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6cfc5-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="6cfc5-104">Change description</span></span>

<span data-ttu-id="6cfc5-105">.NET Core 3.0 Preview `null` 7'de, `""` dize hem özellik adlarını yazarken hem de değerler yazarken işlem gördü.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="6cfc5-106">.NET Core 3.0 Preview 8 `null` ile başlayarak, bir özellik `ArgumentNullException`adı bir ,' atar ve bir `null` değer bir çağrı <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> olarak kabul edilir veya <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6cfc5-107">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="6cfc5-107">Consider the following code:</span></span>

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

<span data-ttu-id="6cfc5-108">.NET Core 3.0 Preview 7 ile çalıştırılırsa, yazar aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6cfc5-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="6cfc5-109">.NET Core 3.0 Preview 8 ile `writer.WriteString(propertyName1, propertyValue1)` başlayarak, bir . <xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="6cfc5-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="6cfc5-110">Ile `propertyName1 = null` `propertyName1 = string.Empty`değiştirilirse, çıktı şimdi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="6cfc5-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="6cfc5-111">Bu değişiklik, arayan ların değerlere `null` yönelik beklentileriyle daha iyi uyumlu hale getirilebilmek için yapıldı.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6cfc5-112">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="6cfc5-112">Version introduced</span></span>

<span data-ttu-id="6cfc5-113">3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="6cfc5-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6cfc5-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6cfc5-114">Recommended action</span></span>

<span data-ttu-id="6cfc5-115"><xref:System.Text.Json.Utf8JsonWriter> Sınıfla özellik adları ve değerleri yazarken:</span><span class="sxs-lookup"><span data-stu-id="6cfc5-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="6cfc5-116">`null` Olmayan dizeleri özellik adları olarak kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="6cfc5-117">Önceki davranış isteniyorsa, null coalescing çağrı kullanın; örneğin, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="6cfc5-118">Bir `null` `null` dize değeri için bir edebi yazma istif değilse, null coalescing çağırma kullanın; örneğin, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span><span class="sxs-lookup"><span data-stu-id="6cfc5-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="6cfc5-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="6cfc5-119">Category</span></span>

<span data-ttu-id="6cfc5-120">CoreFx</span><span class="sxs-lookup"><span data-stu-id="6cfc5-120">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cfc5-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6cfc5-121">Affected APIs</span></span>

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

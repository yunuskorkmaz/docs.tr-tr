---
ms.openlocfilehash: 13da0ef6155d65fbc894c5747cc36bb3483ba518
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721701"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="444ef-101">Utf8JsonWriter içindeki semantiğinin değişikliği `(string)null`</span><span class="sxs-lookup"><span data-stu-id="444ef-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="444ef-102">.NET Core 3,0 Preview 7 ' de, null dize içinde boş dize olarak kabul edilir <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="444ef-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="444ef-103">.NET Core 3,0 Preview 8 ' den itibaren, null dize bir özellik adı olarak kullanıldığında bir özel durum oluşturur ve bir değer olarak kullanıldığında JSON null belirtecini yayar.</span><span class="sxs-lookup"><span data-stu-id="444ef-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="444ef-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="444ef-104">Change description</span></span>

<span data-ttu-id="444ef-105">.NET Core 3,0 Preview 7 ' de, `null` dize `""` özellik adlarını yazarken ve değer yazılırken her ikisi de olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="444ef-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="444ef-106">.NET Core 3,0 Preview 8 ' den itibaren, bir `null` özellik adı bir oluşturur `ArgumentNullException` ve bir `null` değer veya çağrısı olarak değerlendirilir <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="444ef-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="444ef-107">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="444ef-107">Consider the following code:</span></span>

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

<span data-ttu-id="444ef-108">.NET Core 3,0 Preview 7 ile çalıştırırsanız, yazıcı aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="444ef-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="444ef-109">.NET Core 3,0 Preview 8 ' den itibaren çağrısı `writer.WriteString(propertyName1, propertyValue1)` bir oluşturur <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="444ef-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="444ef-110">`propertyName1 = null`İle değiştirilirse `propertyName1 = string.Empty` , çıkış şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="444ef-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="444ef-111">Bu değişiklik, değerler için çağrı beklentileri ile daha iyi uyum sağlamak üzere yapılmıştır `null` .</span><span class="sxs-lookup"><span data-stu-id="444ef-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="444ef-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="444ef-112">Version introduced</span></span>

<span data-ttu-id="444ef-113">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="444ef-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="444ef-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="444ef-114">Recommended action</span></span>

<span data-ttu-id="444ef-115">Sınıf ile özellik adlarını ve değerleri yazarken <xref:System.Text.Json.Utf8JsonWriter> :</span><span class="sxs-lookup"><span data-stu-id="444ef-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="444ef-116">Dizelerin olmayan bir `null` özellik adı olarak kullanıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="444ef-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="444ef-117">Önceki davranış isteniyorsa, null birleşim çağırma kullanın; Örneğin, `writer.WriteString(propertyName1 ?? "", propertyValue1)` .</span><span class="sxs-lookup"><span data-stu-id="444ef-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="444ef-118">`null`Bir `null` dize değeri için değişmez değer yazmak istenmediğinde, null birleşim çağırma kullanın; örneğin, `writer.WriteString(propertyName2, propertyValue2 ?? "")` .</span><span class="sxs-lookup"><span data-stu-id="444ef-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="444ef-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="444ef-119">Category</span></span>

<span data-ttu-id="444ef-120">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="444ef-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="444ef-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="444ef-121">Affected APIs</span></span>

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

#### Affected APIs

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

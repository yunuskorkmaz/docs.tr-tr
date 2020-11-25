---
title: 'Son değişiklik: seri durumdan çıkarma tek karakterli dize gerektiriyor'
description: JsonSerializer. serisini kaldırma, tek karakterli bir dize gerektirdiğinde, .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 780f2928d776ecb6db9a7fc05a720e889eb363e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761650"
---
# <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="77f3f-103">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="77f3f-103">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="77f3f-104">Tür parametresi olduğunda <xref:System.Char> , için dize bağımsız değişkeni, <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> seri durumdan çıkarma işleminin başarılı olması için tek bir karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="77f3f-104">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

## <a name="change-description"></a><span data-ttu-id="77f3f-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="77f3f-105">Change description</span></span>

<span data-ttu-id="77f3f-106">Önceki .NET sürümlerinde, ' a çok karakterli bir dize geçirirseniz <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ve tür parametresi ise, <xref:System.Char> seri kaldırma başarılı olur ve yalnızca ilk karakter seri durumdan çıkarıldır.</span><span class="sxs-lookup"><span data-stu-id="77f3f-106">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="77f3f-107">.NET 5,0 ve üzeri sürümlerde, tür parametresi olduğunda <xref:System.Char> , tek karakterli bir dize dışında bir şey geçirilmesi bir oluşturulmasına neden olur <xref:System.Text.Json.JsonException> .</span><span class="sxs-lookup"><span data-stu-id="77f3f-107">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="77f3f-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="77f3f-108">Version introduced</span></span>

<span data-ttu-id="77f3f-109">5.0</span><span class="sxs-lookup"><span data-stu-id="77f3f-109">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="77f3f-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="77f3f-110">Reason for change</span></span>

<span data-ttu-id="77f3f-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> tek bir JSON değerini temsil eden metni, genel tür parametresiyle belirtilen tür örneğine ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="77f3f-111"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="77f3f-112">Ayrıştırma yalnızca belirtilen yük belirtilen genel tür parametresi için geçerliyse başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="77f3f-112">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="77f3f-113"><xref:System.Char>Değer türü için, geçerli bir yük tek bir karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="77f3f-113">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="77f3f-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="77f3f-114">Recommended action</span></span>

<span data-ttu-id="77f3f-115">Kullanarak bir dize bir tür içine ayrıştırılırken <xref:System.Char> <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> , dizenin tek bir karakter içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="77f3f-115">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="77f3f-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="77f3f-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->

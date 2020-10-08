---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844518"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="3a30c-101">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="3a30c-101">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="3a30c-102">Tür parametresi olduğunda <xref:System.Char> , için dize bağımsız değişkeni, <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> seri durumdan çıkarma işleminin başarılı olması için tek bir karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3a30c-102">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a30c-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3a30c-103">Change description</span></span>

<span data-ttu-id="3a30c-104">Önceki .NET sürümlerinde, ' a çok karakterli bir dize geçirirseniz <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ve tür parametresi ise, <xref:System.Char> seri kaldırma başarılı olur ve yalnızca ilk karakter seri durumdan çıkarıldır.</span><span class="sxs-lookup"><span data-stu-id="3a30c-104">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="3a30c-105">.NET 5,0 ve üzeri sürümlerde, tür parametresi olduğunda <xref:System.Char> , tek karakterli bir dize dışında bir şey geçirilmesi bir oluşturulmasına neden olur <xref:System.Text.Json.JsonException> .</span><span class="sxs-lookup"><span data-stu-id="3a30c-105">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a><span data-ttu-id="3a30c-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3a30c-106">Version introduced</span></span>

<span data-ttu-id="3a30c-107">5.0</span><span class="sxs-lookup"><span data-stu-id="3a30c-107">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a30c-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3a30c-108">Reason for change</span></span>

<span data-ttu-id="3a30c-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> tek bir JSON değerini temsil eden metni, genel tür parametresiyle belirtilen tür örneğine ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="3a30c-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="3a30c-110">Ayrıştırma yalnızca belirtilen yük belirtilen genel tür parametresi için geçerliyse başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="3a30c-110">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="3a30c-111"><xref:System.Char>Değer türü için, geçerli bir yük tek bir karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="3a30c-111">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a30c-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3a30c-112">Recommended action</span></span>

<span data-ttu-id="3a30c-113">Kullanarak bir dize bir tür içine ayrıştırılırken <xref:System.Char> <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> , dizenin tek bir karakter içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3a30c-113">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

#### <a name="category"></a><span data-ttu-id="3a30c-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="3a30c-114">Category</span></span>

<span data-ttu-id="3a30c-115">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="3a30c-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a30c-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3a30c-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->

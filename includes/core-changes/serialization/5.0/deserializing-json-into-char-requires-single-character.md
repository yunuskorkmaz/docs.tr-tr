---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844518"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a>JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir

Tür parametresi olduğunda <xref:System.Char> , için dize bağımsız değişkeni, <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> seri durumdan çıkarma işleminin başarılı olması için tek bir karakter içermelidir.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, ' a çok karakterli bir dize geçirirseniz <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ve tür parametresi ise, <xref:System.Char> seri kaldırma başarılı olur ve yalnızca ilk karakter seri durumdan çıkarıldır.

.NET 5,0 ve üzeri sürümlerde, tür parametresi olduğunda <xref:System.Char> , tek karakterli bir dize dışında bir şey geçirilmesi bir oluşturulmasına neden olur <xref:System.Text.Json.JsonException> .

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> tek bir JSON değerini temsil eden metni, genel tür parametresiyle belirtilen tür örneğine ayrıştırır. Ayrıştırma yalnızca belirtilen yük belirtilen genel tür parametresi için geçerliyse başarılı olur. <xref:System.Char>Değer türü için, geçerli bir yük tek bir karakter dizesidir.

#### <a name="recommended-action"></a>Önerilen eylem

Kullanarak bir dize bir tür içine ayrıştırılırken <xref:System.Char> <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> , dizenin tek bir karakter içerdiğinden emin olun.

#### <a name="category"></a>Kategori

Serileştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->

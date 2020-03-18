---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147594"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText.Encode yöntemleri ek bir JavaScriptEncoder argüman var

.NET Core 3.0 Preview 8 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> ile başlayarak, yöntemler isteğe bağlı <xref:System.Text.Encodings.Web.JavaScriptEncoder> bir bağımsız değişken içerir.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 yeni bir tür içerir, xref:System.Text.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>. .NET Core 3.0 Preview 8 ile <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> başlayarak, tüm yöntem aşırı <xref:System.Text.Encodings.Web.JavaScriptEncoder> yüklemelerinin imzası isteğe bağlı bir parametre içerecek şekilde değiştirildi. Bu değişiklik, farklı veya özel bir kodlayıcıya izin vermek için yapıldı.

.NET Core `Encode` 3.0 Preview 7'deki yöntemlerin imzası:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

.NET Core `Encode` 3.0 Önizleme 8 ve sonraki sürümlerinde aynı yöntemlerin imzası:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a>Sürüm tanıtıldı

.NET Core 3.0 Önizleme 8

#### <a name="recommended-action"></a>Önerilen eylem

Bu yalnızca ikili bir kırılma değişikliğidir; .NET Core 3.0 Preview 8 veya daha sonraki bir sürüm karşı bir derleme herhangi bir çalışma zamanı sorunları giderecektir.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->

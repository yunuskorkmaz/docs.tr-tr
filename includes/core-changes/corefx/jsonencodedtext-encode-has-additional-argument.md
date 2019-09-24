---
ms.openlocfilehash: 377f22409558c21d1c57f6214c13572dedf9e419
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217075"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır

.NET Core 3,0 Preview 8 ' <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> den itibaren Yöntemler isteğe bağlı <xref:System.Text.Encodings.Web.JavaScriptEncoder> bir bağımsız değişken içerir.

#### <a name="details"></a>Ayrıntılar

.NET Core 3,0 yeni bir tür içerir: XREF: System. Text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType >. .NET Core 3,0 Preview 8 ' den itibaren, tüm <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> yöntem aşırı yüklemelerinin imzası isteğe bağlı <xref:System.Text.Encodings.Web.JavaScriptEncoder> bir parametre içerecek şekilde değiştirilmiştir. Bu değişiklik, farklı veya özel bir kodlayıcı için izin vermek üzere yapılmıştır.

.NET Core 3,0 Preview `Encode` 7 ' deki yöntemlerin imzası şunlardır:

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

.NET Core 3,0 Preview 8 `Encode` ve sonraki sürümlerinde aynı yöntemlerin imzası:

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

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Bu yalnızca ikili bir son değişiklik. .NET Core 3,0 Preview 8 veya sonraki bir sürüme yönelik yeniden derleme, çalışma zamanı sorunlarını düzeltir.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->

---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568249"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır

.NET Core 3,0 Preview 8 ' den başlayarak <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> Yöntemler isteğe bağlı bir <xref:System.Text.Encodings.Web.JavaScriptEncoder> bağımsız değişkeni içerir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 yeni bir tür içerir: XREF: System. Text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType >. .NET Core 3,0 Preview 8 ' den itibaren, tüm <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin imzası isteğe bağlı bir <xref:System.Text.Encodings.Web.JavaScriptEncoder> parametresi içerecek şekilde değiştirilmiştir. Bu değişiklik, farklı veya özel bir kodlayıcı için izin vermek üzere yapılmıştır.

.NET Core 3,0 Preview 7 ' deki `Encode` yöntemlerinin imzası:

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

.NET Core 3,0 Preview 8 ve sonraki sürümlerindeki aynı `Encode` yöntemlerinin imzası:

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

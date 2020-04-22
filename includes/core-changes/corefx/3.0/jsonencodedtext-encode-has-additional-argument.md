---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021566"
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

Çekirdek .NET kitaplıkları

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

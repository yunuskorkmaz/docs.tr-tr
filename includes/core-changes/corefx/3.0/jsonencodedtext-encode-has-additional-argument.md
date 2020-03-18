---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147594"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="124bb-101">JsonEncodedText.Encode yöntemleri ek bir JavaScriptEncoder argüman var</span><span class="sxs-lookup"><span data-stu-id="124bb-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="124bb-102">.NET Core 3.0 Preview 8 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> ile başlayarak, yöntemler isteğe bağlı <xref:System.Text.Encodings.Web.JavaScriptEncoder> bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="124bb-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="124bb-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="124bb-103">Change description</span></span>

<span data-ttu-id="124bb-104">.NET Core 3.0 yeni bir tür içerir, xref:System.Text.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="124bb-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="124bb-105">.NET Core 3.0 Preview 8 ile <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> başlayarak, tüm yöntem aşırı <xref:System.Text.Encodings.Web.JavaScriptEncoder> yüklemelerinin imzası isteğe bağlı bir parametre içerecek şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="124bb-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="124bb-106">Bu değişiklik, farklı veya özel bir kodlayıcıya izin vermek için yapıldı.</span><span class="sxs-lookup"><span data-stu-id="124bb-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="124bb-107">.NET Core `Encode` 3.0 Preview 7'deki yöntemlerin imzası:</span><span class="sxs-lookup"><span data-stu-id="124bb-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="124bb-108">.NET Core `Encode` 3.0 Önizleme 8 ve sonraki sürümlerinde aynı yöntemlerin imzası:</span><span class="sxs-lookup"><span data-stu-id="124bb-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="124bb-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="124bb-109">Version introduced</span></span>

<span data-ttu-id="124bb-110">.NET Core 3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="124bb-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="124bb-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="124bb-111">Recommended action</span></span>

<span data-ttu-id="124bb-112">Bu yalnızca ikili bir kırılma değişikliğidir; .NET Core 3.0 Preview 8 veya daha sonraki bir sürüm karşı bir derleme herhangi bir çalışma zamanı sorunları giderecektir.</span><span class="sxs-lookup"><span data-stu-id="124bb-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="124bb-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="124bb-113">Category</span></span>

<span data-ttu-id="124bb-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="124bb-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="124bb-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="124bb-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->

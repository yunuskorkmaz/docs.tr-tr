---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568249"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="31090-101">JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır</span><span class="sxs-lookup"><span data-stu-id="31090-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="31090-102">.NET Core 3,0 Preview 8 ' den başlayarak <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> Yöntemler isteğe bağlı bir <xref:System.Text.Encodings.Web.JavaScriptEncoder> bağımsız değişkeni içerir.</span><span class="sxs-lookup"><span data-stu-id="31090-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="31090-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="31090-103">Change description</span></span>

<span data-ttu-id="31090-104">.NET Core 3,0 yeni bir tür içerir: XREF: System. Text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType >.</span><span class="sxs-lookup"><span data-stu-id="31090-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31090-105">.NET Core 3,0 Preview 8 ' den itibaren, tüm <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin imzası isteğe bağlı bir <xref:System.Text.Encodings.Web.JavaScriptEncoder> parametresi içerecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="31090-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="31090-106">Bu değişiklik, farklı veya özel bir kodlayıcı için izin vermek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="31090-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="31090-107">.NET Core 3,0 Preview 7 ' deki `Encode` yöntemlerinin imzası:</span><span class="sxs-lookup"><span data-stu-id="31090-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="31090-108">.NET Core 3,0 Preview 8 ve sonraki sürümlerindeki aynı `Encode` yöntemlerinin imzası:</span><span class="sxs-lookup"><span data-stu-id="31090-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="31090-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="31090-109">Version introduced</span></span>

<span data-ttu-id="31090-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="31090-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="31090-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="31090-111">Recommended action</span></span>

<span data-ttu-id="31090-112">Bu yalnızca ikili bir son değişiklik. .NET Core 3,0 Preview 8 veya sonraki bir sürüme yönelik yeniden derleme, çalışma zamanı sorunlarını düzeltir.</span><span class="sxs-lookup"><span data-stu-id="31090-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="31090-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="31090-113">Category</span></span>

<span data-ttu-id="31090-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="31090-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31090-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="31090-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->

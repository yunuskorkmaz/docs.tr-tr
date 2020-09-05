---
ms.openlocfilehash: d9e1624bbeb91db63bc284b8eb52643938eb42e5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497575"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="0adfe-101">GlyphRun. ComputeInkBoundingBox () ve FormattedText. kapsam .NET Framework 4,5 ' den başlayarak farklı değerler döndürüyor</span><span class="sxs-lookup"><span data-stu-id="0adfe-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="0adfe-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0adfe-102">Details</span></span>

<span data-ttu-id="0adfe-103"><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> <xref:System.Windows.Media.FormattedText.Extent> .NET Framework 4,5 ' de yapılan geliştirmeler, .NET Framework 4,0 ' deki bazı durumlarda yer alan Glifler için kutuların çok küçük olduğu sorunları ele almak üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0adfe-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="0adfe-104">Bunun sonucunda, bazı sınırlayıcı kutular .NET Framework 4,5 ' den itibaren daha büyük olacaktır, bu da Kullanıcı arabirimi düzeninde hafif farklılıklar oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0adfe-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0adfe-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="0adfe-105">Suggestion</span></span>

<span data-ttu-id="0adfe-106">Bazı glif sınırlayıcı kutusu boyutlarının arttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0adfe-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="0adfe-107">Bu değişiklikler genellikle sunuyu ve isabet kutusu testini iyileştirir, ancak eski (pre-.NET 4,5) davranışı isteniyorsa, app.config dosyasına aşağıdaki giriş eklenerek kabul edilebilir:</span><span class="sxs-lookup"><span data-stu-id="0adfe-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="0adfe-108">Name</span><span class="sxs-lookup"><span data-stu-id="0adfe-108">Name</span></span>    | <span data-ttu-id="0adfe-109">Değer</span><span class="sxs-lookup"><span data-stu-id="0adfe-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0adfe-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0adfe-110">Scope</span></span>   |<span data-ttu-id="0adfe-111">Edge</span><span class="sxs-lookup"><span data-stu-id="0adfe-111">Edge</span></span>|
|<span data-ttu-id="0adfe-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0adfe-112">Version</span></span>|<span data-ttu-id="0adfe-113">4,5</span><span class="sxs-lookup"><span data-stu-id="0adfe-113">4.5</span></span>|
|<span data-ttu-id="0adfe-114">Tür</span><span class="sxs-lookup"><span data-stu-id="0adfe-114">Type</span></span>|<span data-ttu-id="0adfe-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="0adfe-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="0adfe-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0adfe-116">Affected APIs</span></span>

- <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType>
- <xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Media.GlyphRun.ComputeInkBoundingBox`
- `P:System.Windows.Media.FormattedText.Extent`

-->

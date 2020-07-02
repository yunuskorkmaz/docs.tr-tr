---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620687"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="b97f6-101">GlyphRun. ComputeInkBoundingBox () ve FormattedText. kapsam .NET Framework 4,5 ' den başlayarak farklı değerler döndürüyor</span><span class="sxs-lookup"><span data-stu-id="b97f6-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="b97f6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b97f6-102">Details</span></span>

<span data-ttu-id="b97f6-103"><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> <xref:System.Windows.Media.FormattedText.Extent> .NET Framework 4,5 ' de yapılan geliştirmeler, .NET Framework 4,0 ' deki bazı durumlarda yer alan Glifler için kutuların çok küçük olduğu sorunları ele almak üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b97f6-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="b97f6-104">Bunun sonucunda, bazı sınırlayıcı kutular .NET Framework 4,5 ' den itibaren daha büyük olacaktır, bu da Kullanıcı arabirimi düzeninde hafif farklılıklar oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b97f6-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b97f6-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b97f6-105">Suggestion</span></span>

<span data-ttu-id="b97f6-106">Bazı glif sınırlayıcı kutusu boyutlarının arttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b97f6-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="b97f6-107">Bu değişiklikler genellikle sunuyu ve isabet kutusu testini iyileştirir, ancak eski (pre-.NET 4,5) davranışı isteniyorsa, app.config dosyasına aşağıdaki giriş eklenerek kabul edilebilir:</span><span class="sxs-lookup"><span data-stu-id="b97f6-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b97f6-108">Name</span><span class="sxs-lookup"><span data-stu-id="b97f6-108">Name</span></span>    | <span data-ttu-id="b97f6-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b97f6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b97f6-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b97f6-110">Scope</span></span>   |<span data-ttu-id="b97f6-111">Edge</span><span class="sxs-lookup"><span data-stu-id="b97f6-111">Edge</span></span>|
|<span data-ttu-id="b97f6-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b97f6-112">Version</span></span>|<span data-ttu-id="b97f6-113">4,5</span><span class="sxs-lookup"><span data-stu-id="b97f6-113">4.5</span></span>|
|<span data-ttu-id="b97f6-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b97f6-114">Type</span></span>|<span data-ttu-id="b97f6-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b97f6-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b97f6-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b97f6-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: d9e1624bbeb91db63bc284b8eb52643938eb42e5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497575"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun. ComputeInkBoundingBox () ve FormattedText. kapsam .NET Framework 4,5 ' den başlayarak farklı değerler döndürüyor

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> <xref:System.Windows.Media.FormattedText.Extent> .NET Framework 4,5 ' de yapılan geliştirmeler, .NET Framework 4,0 ' deki bazı durumlarda yer alan Glifler için kutuların çok küçük olduğu sorunları ele almak üzere yapılmıştır. Bunun sonucunda, bazı sınırlayıcı kutular .NET Framework 4,5 ' den itibaren daha büyük olacaktır, bu da Kullanıcı arabirimi düzeninde hafif farklılıklar oluşmasına neden olur.

#### <a name="suggestion"></a>Öneri

Bazı glif sınırlayıcı kutusu boyutlarının arttığını unutmayın. Bu değişiklikler genellikle sunuyu ve isabet kutusu testini iyileştirir, ancak eski (pre-.NET 4,5) davranışı isteniyorsa, app.config dosyasına aşağıdaki giriş eklenerek kabul edilebilir:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType>
- <xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Media.GlyphRun.ComputeInkBoundingBox`
- `P:System.Windows.Media.FormattedText.Extent`

-->

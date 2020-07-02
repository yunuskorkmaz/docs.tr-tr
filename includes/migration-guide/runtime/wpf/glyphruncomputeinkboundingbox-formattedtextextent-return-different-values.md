---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620687"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|

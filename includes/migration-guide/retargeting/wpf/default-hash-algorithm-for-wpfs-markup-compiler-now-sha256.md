---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614927"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>WPF 'in biçimlendirme derleyicisi için varsayılan karma algoritması artık SHA256

#### <a name="details"></a>Ayrıntılar

WPF MarkupCompiler, XAML işaretleme dosyaları için derleme hizmetleri sağlar.  .NET Framework 4.7.1 ve önceki sürümlerde, sağlama toplamı için kullanılan varsayılan karma algoritma SHA1 ' dır. SHA1 ile ilgili en son güvenlik sorunları nedeniyle, bu varsayılan değer .NET Framework 4.7.2 ile başlayarak SHA256 olarak değiştirilmiştir.  Bu değişiklik, derleme sırasında biçimlendirme dosyaları için tüm sağlama toplamı üretimini etkiler.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.2 veya üstünü hedefleyen ve SHA1 karma davranışına geri dönmek isteyen bir geliştirici, aşağıdaki AppContext bayrağını ayarlamış olmalıdır.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

.NET 4.7.2 'ın altında bir Framework sürümünü hedeflerken SHA256 karmasını kullanmak isteyen bir geliştirici aşağıdaki AppContext bayrağını ayarlamanız gerekir.  .NET Framework yüklü sürümünün 4.7.2 veya daha büyük olması gerektiğini unutmayın.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Geçirgen |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614941"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Klavye odağı artık birden çok WinForms/WPF barındırma katmanında doğru şekilde taşınıyor

#### <a name="details"></a>Ayrıntılar

Bir WinForms denetimini barındıran bir WPF uygulamasını, WPF denetimlerini barındıran bir şekilde düşünün. Bu katmandaki ilk veya son denetim WPF ise, kullanıcılar WinForms katmanının dışına sekme yapamaz `System.Windows.Forms.Integration.ElementHost` . Bu değişiklik bu sorunu düzeltir ve kullanıcılar artık WinForms katmanının dışına sekme verebilir. Odaklanmayı kullanan otomatikleştirilmiş uygulamalar, WinForms katmanını hiçbir şekilde yok etmeme, artık beklendiği gibi çalışmayabilir.

#### <a name="suggestion"></a>Öneri

.NET 4.7.2 'in altında bir Framework sürümünü hedeflerken bu değişikliği kullanmak isteyen bir geliştirici, değişikliğin etkinleştirilmesi için aşağıdaki AppContext bayrakları kümesini false olarak ayarlayabilir.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Daha sonraki geliştirmeleri almak için WPF uygulamalarının tüm erken erişilebilirlik geliştirmelerini kabul etmelidir. Diğer bir deyişle, ve anahtarlarının her ikisi de, `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2` .NET 4.7.2 veya üzerini hedeflerken önceki Işlevselliği gerektiren Seta geliştiricisi olmalıdır değişikliğin devre dışı bırakılması Için aşağıdaki AppContext bayrağını True olarak ayarlayabilir.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

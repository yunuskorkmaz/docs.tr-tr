---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614968"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>Bir denetimin Içeriği olmadığında, RadioButton için WPF FocusVisual ve CheckBox artık doğru şekilde görüntülüyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ve önceki sürümlerde WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> tutarsız ve klasik ve yüksek karşıtlık temalarında yanlış odak görselleri.  Bu sorunlar, denetimlerin hiçbir içerik kümesi olmadığı durumlarda oluşur.  Bu, Temalar kafa karıştırıcı ve odak görselindeki geçişleri görebilir. .NET Framework 4.7.2, bu görseller artık Temalar arasında daha tutarlıdır ve klasik ve Yüksek Karşıtlık temalarda daha kolay görünür.

#### <a name="suggestion"></a>Öneri

.NET 4.7.1 'deki davranışa geri dönmek isteyen .NET Framework 4.7.2 hedefleyen bir geliştirici, aşağıdaki AppContext bayrağını ayarlaması gerekecektir.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

.NET 4.7.2 altında bir Framework sürümünü hedeflerken bu değişikliği kullanmak isteyen bir geliştirici aşağıdaki AppContext bayraklarını ayarlamanız gerekir. Tüm bayrakların uygun şekilde ayarlanması gerektiğini ve .NET Framework yüklü sürümünün 4.7.2 veya daha büyük olması gerektiğini unutmayın. En son geliştirmeleri almak için WPF uygulamalarının tüm önceki erişilebilirlik geliştirmelerini kabul etmek gerekir. Bunu yapmak için, ' Switch. UseLegacyAccessibilityFeatures ' ve ' Switch. UseLegacyAccessibilityFeatures. 2 ' AppContext anahtarlarının her ikisinin de false olarak ayarlandığından emin olun.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

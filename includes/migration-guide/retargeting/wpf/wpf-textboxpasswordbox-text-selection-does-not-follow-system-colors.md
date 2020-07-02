---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614982"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>WPF metin kutusu/PasswordBox metin seçimi sistem renklerini Izlemez

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ve önceki sürümlerinde, WPF `System.Windows.Controls.TextBox` ve `System.Windows.Controls.PasswordBox` yalnızca donatıcı katmanında bir metin seçimi işleyebilir. Bazı sistem temaları 'nda bu metin, bu şekilde okunabilir ve okunması zor hale gelir.  .NET Framework 4.7.2 ve sonraki sürümlerde, geliştiricilerin bu sorunu konuma almayı azaltır olan donatıcı olmayan bir seçim işleme düzenini etkinleştirme seçeneği vardır.

#### <a name="suggestion"></a>Öneri

Bu değişikliği kullanmak isteyen bir geliştirici aşağıdaki AppContext bayrağını uygun şekilde ayarlamanız gerekir.  Bu özelliği kullanmak için, yüklü .NET Framework sürümü 4.7.2 veya daha büyük olmalıdır. Donatıcı olmayan tabanlı seçimi etkinleştirmek için aşağıdaki AppContext bayrağını kullanın.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

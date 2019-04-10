---
ms.openlocfilehash: 4eac93d5cfea19cb83c66cd3fe35c1b0703c0cc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234043"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>İçerik denetimleri olduğunda Ortala radyo düğmesi ve onay kutusu artık WPF FocusVisual doğru görüntüler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerinde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> tutarsız ve klasik ve yüksek karşıtlık temalar, yanlış odak görseller vardır.  Bu sorunlar burada denetimleri herhangi bir içerik kümesi olmayan durumlarda oluşur.  Bu tema kafa karıştırıcı ve odak görsel arasında geçiş görmek sabit yapabilirsiniz. .NET Framework'teki 4.7.2 Bu görsel temalar arasında daha tutarlı ve klasik ve yüksek karşıtlıklı tema daha kolay görünür.|
|Öneri|.NET 4.7.1 davranışını geri almak isteyen .NET Framework'e 4.7.2 hedefleyen bir geliştirici aşağıdaki AppContext bayrağının ayarlanması gerekir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bu değişiklik sırasında bir aşağıda 4.7.2 .NET framework sürümünü hedefleme yararlanmak isteyen bir geliştirici aşağıdaki AppContext bayrakları ayarlamanız gerekir. Tüm bayraklar uygun şekilde ayarlamanız gerekir ve .NET Framework'ün yüklü sürümü 4.7.2 olmalıdır veya büyük. WPF uygulamaları ilişkin en son gelişmeleri almak için tüm önceki erişilebilirlik geliştirmeleri için katılım için gereklidir. Bunu yapmak için 'Switch.UseLegacyAccessibilityFeatures' ve 'Switch.UseLegacyAccessibilityFeatures.2' false olarak ayarlanmış olan iki AppContext anahtarları emin olun.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|

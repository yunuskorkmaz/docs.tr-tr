---
ms.openlocfilehash: 38c50244b1cee41bd95c232ac5d1691c59c55488
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760936"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>İçerik denetimleri olduğunda Ortala radyo düğmesi ve onay kutusu artık WPF FocusVisual doğru görüntüler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerinde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> tutarsız ve klasik ve yüksek karşıtlık temalar, yanlış odak görseller vardır.  Bu sorunlar burada denetimleri herhangi bir içerik kümesi olmayan durumlarda oluşur.  Bu tema kafa karıştırıcı ve odak görsel arasında geçiş görmek sabit yapabilirsiniz. .NET Framework'teki 4.7.2 Bu görsel temalar arasında daha tutarlı ve klasik ve yüksek karşıtlıklı tema daha kolay görünür.|
|Öneri|.NET 4.7.1 davranışını geri almak isteyen .NET Framework'e 4.7.2 hedefleyen bir geliştirici aşağıdaki AppContext bayrağının ayarlanması gerekir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bu değişiklik sırasında bir aşağıda 4.7.2 .NET framework sürümünü hedefleme yararlanmak isteyen bir geliştirici aşağıdaki AppContext bayrakları ayarlamanız gerekir. Tüm bayraklar uygun şekilde ayarlamanız gerekir ve .NET Framework'ün yüklü sürümü 4.7.2 olmalıdır veya büyük. WPF uygulamaları ilişkin en son gelişmeleri almak için tüm önceki erişilebilirlik geliştirmeleri için katılım için gereklidir. Bunu yapmak için 'Switch.UseLegacyAccessibilityFeatures' ve 'Switch.UseLegacyAccessibilityFeatures.2' false olarak ayarlanmış olan iki AppContext anahtarları emin olun.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|


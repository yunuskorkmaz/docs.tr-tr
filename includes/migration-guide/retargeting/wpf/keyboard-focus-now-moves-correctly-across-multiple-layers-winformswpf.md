---
ms.openlocfilehash: ae110d915241fe85453667e895ab54288302c20d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760895"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Klavye odağı artık doğru şekilde WinForms/WPF barındırma birden çok katmanda taşır

|   |   |
|---|---|
|Ayrıntılar|WPF denetimlerini sırayla barındıran bir WinForms denetimi barındıran WPF uygulaması göz önünde bulundurun. Kullanıcılar bu katmandaki ilk veya son denetim WPF ise dışında WinForms katman sekmesinde mümkün olmayabilir <code>System.Windows.Forms.Integration.ElementHost</code>. Bu değişiklik, bu sorunu giderir ve kullanıcılar artık dışında WinForms katman sekmesinde olanağına sahip olursunuz. Hiçbir zaman WinForms katman kaçış odaklanmak otomatik uygulamaları artık beklendiği gibi çalışmayabilir.|
|Öneri|Bu değişiklik sırasında bir aşağıda 4.7.2 .NET framework sürümünü hedefleme yararlanmak isteyen bir geliştirici false değişikliğin etkin aşağıdaki AppContext bayrakları kümesini ayarlayabilirsiniz.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>WPF uygulamaları sonraki geliştirmeleri almak için tüm erken erişilebilirlik geliştirmeleri ile mi etmeniz gerekir. Diğer bir deyişle, her ikisi de <code>Switch.UseLegacyAccessibilityFeatures</code> ve <code>Switch.UseLegacyAccessibilityFeatures.2</code> anahtarları .NET 4.7.2 hedefleyen sırasında önceki işlevselliğini gerektirir setA geliştiriciye olmalıdır veya büyük can true olması için devre dışı aşağıdaki AppContext bayrağını ayarlayın.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|


---
ms.openlocfilehash: 5df5afec17d400ed14fe9b4c03c2f754895f0dd7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378761"
---
### <a name="resizing-a-grid-can-cause-an-application-to-become-unresponsive"></a>Bir kılavuz yeniden boyutlandırma, uygulamanın yanıt veremez duruma gelmesine neden olabilir

|   |   |
|---|---|
|Ayrıntılar|Sonsuz bir döngüye düzenini sırasında oluşabilecek bir <code>T:System.Windows.Controls.Grid</code> aşağıdaki durumlarda:<ul><li>Satır tanımlarını içeren iki *-rows, hem bir MinHeight ve bir MaxHeight bildirme.</li><li>İçeriği *-satır karşılık gelen MaxHeight aşan değil</li><li>İlk MinHeight tarafından kullanılabilir kılavuz yüksekliği aşıldı (ve diğer tüm sabit veya satır otomatik)</li><li>Uygulama .NET Framework 4.7 hedefleyen veya 4.7 ayırma algoritmasını ayarlayarak kabul eder <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü ikiden fazla satır veya sütunlar için analojiktir durumda de gerçekleşir. .NET Framework 4.7.1 olan sorun çözüldüğünde.|
|Öneri|.NET Framework 4.7.1 yükseltin.  Alternatif olarak, 4.7 ayırma algoritmasını gerekmiyorsa şu yapılandırma ayarı kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

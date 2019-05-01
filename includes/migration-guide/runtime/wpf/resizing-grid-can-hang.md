---
ms.openlocfilehash: 63101fb127c84de21d165994bba85a2753e97344
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665187"
---
### <a name="resizing-a-grid-can-hang"></a>Bir kılavuz yeniden boyutlandırma askıda kalabilir

|   |   |
|---|---|
|Ayrıntılar|Sonsuz bir döngüye düzenini sırasında oluşabilecek bir <code>T:System.Windows.Controls.Grid</code> aşağıdaki durumlarda:<ul><li>Satır tanımlarını içeren iki *-rows, hem bir MinHeight ve bir MaxHeight bildirme.</li><li>İçeriği *-satır karşılık gelen MaxHeight aşan değil</li><li>İlk MinHeight tarafından kullanılabilir kılavuz yüksekliği aşıldı (ve diğer tüm sabit veya satır otomatik)</li><li>Uygulama .NET Framework 4.7 hedefleyen veya 4.7 ayırma algoritmasını ayarlayarak kabul eder <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü ikiden fazla satır veya sütunlar için analojiktir durumda de gerçekleşir. .NET Framework 4.7.1 olan sorun çözüldüğünde.|
|Öneri|.NET Framework 4.7.1 yükseltin.  Alternatif olarak, 4.7 ayırma algoritmasını gerekmiyorsa şu yapılandırma ayarı kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

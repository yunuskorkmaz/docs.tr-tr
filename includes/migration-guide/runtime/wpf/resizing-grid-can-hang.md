---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997737"
---
### <a name="resizing-a-grid-can-hang"></a>Izgara yeniden boyutlandırma asılabilir

|   |   |
|---|---|
|Ayrıntılar|Aşağıdaki koşullar altında bir düzenin <code>T:System.Windows.Controls.Grid</code> düzeni sırasında sonsuz bir döngü oluşabilir:<ul><li>Satır tanımları, her ikisi de MinHeight ve MaxHeight bildiren iki *satır içerir.</li><li>*-satırların içeriği ilgili MaxHeight'ı aşmaz</li><li>Izgara'nın kullanılabilir yüksekliği ilk MinHeight (artı diğer sabit veya Otomatik satırlar) tarafından aşılır</li><li>Uygulama .NET Framework 4.7'yi hedefler veya 4.7 ayırma algoritmasını ayarlayarak<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü ayrıca ikiden fazla satırda veya sütunlar için benzer durumda olur. Sorun .NET Framework 4.7.1'de giderilmiştir.|
|Öneri|.NET Framework 4.7.1'e yükseltin.  Alternatif olarak, 4.7 ayırma algoritmasına ihtiyacınız yoksa aşağıdaki yapılandırma ayarını kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Çalışma Zamanı|

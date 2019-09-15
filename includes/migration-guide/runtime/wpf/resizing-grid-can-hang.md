---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997737"
---
### <a name="resizing-a-grid-can-hang"></a>Bir kılavuzun yeniden boyutlandırılması askıda kalabilir

|   |   |
|---|---|
|Ayrıntılar|Aşağıdaki koşullarda bir <code>T:System.Windows.Controls.Grid</code> öğesinin düzeni sırasında sonsuz bir döngü meydana gelebilir:<ul><li>Satır tanımları, her ikisi de MinHeight ve MaxHeight bildiren iki * satırı içerir.</li><li>*-Rows içeriği karşılık gelen MaxHeight değerini aşamaz</li><li>Kılavuzun kullanılabilir yüksekliği ilk MinHeight (artı diğer tüm sabit veya otomatik satırlar) ile aşıldı</li><li>Uygulama, 4,7 .NET Framework veya ayarlarını yaparak 4,7 ayırma algoritmasında<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü aynı zamanda ikiden fazla satır veya sütun için büyük/küçük harf ile de gerçekleşir. Sorun .NET Framework 4.7.1 içinde düzeltildi.|
|Öneri|.NET Framework 4.7.1 ' ye yükseltin.  Alternatif olarak, 4,7 ayırma algoritmasına ihtiyacınız yoksa aşağıdaki yapılandırma ayarını kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

---
ms.openlocfilehash: 1e4c0ac1f0f9011f4b8fc136ec2e383d38567355
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83435401"
---
### <a name="resizing-a-grid-can-hang"></a>Bir kılavuzun yeniden boyutlandırılması askıda kalabilir

|   |   |
|---|---|
|Ayrıntılar|Aşağıdaki koşullarda bir öğesinin düzeni sırasında sonsuz bir döngü meydana gelebilir <code>T:System.Windows.Controls.Grid</code> :<ul><li>Satır tanımları \* , hem MinHeight hem de MaxHeight bildiren iki satır içerir.</li><li>\*-Satırların içeriği karşılık gelen MaxHeight değerini aşamaz</li><li>Kılavuzun kullanılabilir yüksekliği ilk MinHeight (artı diğer tüm sabit veya otomatik satırlar) ile aşıldı</li><li>Uygulama, 4,7 .NET Framework veya ayarlarını yaparak 4,7 ayırma algoritmasında<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü aynı zamanda ikiden fazla satır veya sütun için büyük/küçük harf ile de gerçekleşir. Sorun .NET Framework 4.7.1 içinde düzeltildi.|
|Öneri|.NET Framework 4.7.1 ' ye yükseltin.  Alternatif olarak, 4,7 ayırma algoritmasına ihtiyacınız yoksa aşağıdaki yapılandırma ayarını kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

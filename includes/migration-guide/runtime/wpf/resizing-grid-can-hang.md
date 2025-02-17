---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496815"
---
### <a name="resizing-a-grid-can-hang"></a>Bir kılavuzun yeniden boyutlandırılması askıda kalabilir

#### <a name="details"></a>Ayrıntılar

Aşağıdaki koşullarda bir öğesinin düzeni sırasında sonsuz bir döngü meydana gelebilir <code>T:System.Windows.Controls.Grid</code> :<ul><li>Satır tanımları \* , hem MinHeight hem de MaxHeight bildiren iki satır içerir.</li><li>\*-Satırların içeriği karşılık gelen MaxHeight değerini aşamaz</li><li>Kılavuzun kullanılabilir yüksekliği ilk MinHeight (artı diğer tüm sabit veya otomatik satırlar) ile aşıldı</li><li>Uygulama, 4,7 .NET Framework veya ayarlarını yaparak 4,7 ayırma algoritmasında <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Döngü aynı zamanda ikiden fazla satır veya sütun için büyük/küçük harf ile de gerçekleşir. Sorun .NET Framework 4.7.1 içinde düzeltildi.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.1 ' ye yükseltin.  Alternatif olarak, 4,7 ayırma algoritmasına ihtiyacınız yoksa aşağıdaki yapılandırma ayarını kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

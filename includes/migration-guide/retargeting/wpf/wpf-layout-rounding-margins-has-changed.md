---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804512"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>Kenar boşluklarının WPF düzeni yuvarlama değişti

|   |   |
|---|---|
|Ayrıntılar|Kenar boşluklarının yuvarlanma ve kenarlıklar ile bunların içindeki arka plan değişti. Bu değişikliğin bir sonucu olarak:<ul><li>Öğelerin genişliği veya yüksekliği en fazla bir piksel büyüyebilir veya küçülebilir.</li><li>Bir nesnenin yerleşimi en fazla bir piksel tarafından hareket edebilir.</li><li>Ortalanmış öğeler en fazla bir piksel ile dikey veya yatay kapalı merkezi olabilir.</li></ul>Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4.6'yı hedefleyen uygulamalar için etkinleştirilir.|
|Öneri|Bu değişiklik yüksek DPI'larda WPF denetimlerinin sağ veya alt kesiminin kırpma sını ortadan kaldırma eğiliminde olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET <code>&lt;runtime&gt;</code> Framework 4.6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu yeni davranışı seçebilir:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>.NET Framework 4.6'yı hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini <code>&lt;runtime&gt;</code> isteyen uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|

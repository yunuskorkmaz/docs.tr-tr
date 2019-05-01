---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093613"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF Düzen kenar boşluklarını yuvarlama değişti

|   |   |
|---|---|
|Ayrıntılar|Hangi kenar boşluklarını yuvarlanır ve Kenarlıklar ve arka plan bunları içinde şekilde değişti. Bu değişikliğin ardından:<ul><li>Öğelerin yükseklik ve genişlik büyütür veya en fazla bir piksel küçültür.</li><li>Bir nesne yerleşimini en fazla bir piksel taşıyabilirsiniz.</li><li>Ortalanmış öğeleri yatay veya dikey olarak en fazla bir piksel merkezin olabilir.</li></ul>Bu yeni bir düzen, varsayılan olarak, yalnızca .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.|
|Öneri|Bu yana sağında veya altında yüksek Dpı'larda WPF denetimleri, kırpma ortadan kaldırmak için bu değişikliği eğilimi gösterir, ancak .NET Framework 4.6 üzerinde çalışan .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz <code>&lt;runtime&gt;</code> app.config dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>.NET Framework 4.6 hedef ancak önceki yerleşimi algoritmasını kullanarak işlemek için WPF denetimleri isteyen uygulamalar bunu aşağıdaki satırı ekleyerek <code>&lt;runtime&gt;</code> app.config dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|

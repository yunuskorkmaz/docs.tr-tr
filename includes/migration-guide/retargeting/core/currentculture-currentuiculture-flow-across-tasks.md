---
ms.openlocfilehash: efe8a2dd98865f6a24b65ce0f08eb0c574b708f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804505"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>Görevler arasında GüncelKültür ve CurrentUICulture akışı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6'dan <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> başlayarak iş parçacığının <xref:System.Threading.ExecutionContext?displayProperty=name>, eşzamanlı işlemler boyunca akan depolanır. Bu, değişikliklerin <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> daha sonra eşzamanlı olarak çalıştırılan görevlere yansıtılacak veya yansıtılacağı anlamına gelir. Bu, önceki .NET Framework sürümlerinin (sıfırlanır <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> ve <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> tüm eşzamanlı görevlerde) davranışından farklıdır.|
|Öneri|Bu değişiklikten etkilenen uygulamalar, istenileni <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> açıkça ayarlayarak veya <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> bir async Görevi'ndeki ilk işlem olarak geçici olarak çalışabilir. Alternatif olarak, eski davranış (akan <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>değil) aşağıdaki uyumluluk anahtarı ayarlayarak içine tercih edilebilir:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Bu sorun WPF tarafından .NET Framework 4.6.2'de giderilmiştir. Ayrıca .NET Frameworks 4.6, 4.6.1 ile [KB 3139549](https://support.microsoft.com/kb/3139549)olarak sabitlenmiştir. .NET Framework 4.6 veya daha sonrasını hedefleyen uygulamalar, WPF uygulamalarında otomatik olarak doğru davranışı alır - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) Dispatcher işlemleri nde korunur.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|

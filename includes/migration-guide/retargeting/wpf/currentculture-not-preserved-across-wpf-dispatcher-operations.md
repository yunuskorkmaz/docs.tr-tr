---
ms.openlocfilehash: bd656478a55856e676853e57f3e7386ea0aa0211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614828"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture, WPF dağıtıcı işlemleri arasında korunmaz

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> Bu dağıtıcı işleminin sonunda, bir içinde yapılan veya yapılan değişiklikler <xref:System.Windows.Threading.Dispatcher?displayProperty=fullName> kaybedilir. Benzer şekilde, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> bir dağıtıcı işleminin dışında yapılan değişiklikler veya bu işlem yürütüldüğünde yansıtılmayabilir. Bu şekilde, bu durum <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ve değişikliklerin WPF <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> uygulamasındaki WPF Kullanıcı arabirimi geri çağırmaları ve diğer kodlar arasında akamayacağı anlamına gelir. Bunun nedeni, bu <xref:System.Threading.ExecutionContext?displayProperty=fullName> Sebepteki bir değişiklikten <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ve .NET Framework 4,6 ' i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> hedefleyen uygulamalarla başlayan yürütme bağlamında depolanmasıdır. WPF dağıtıcı işlemleri, işlemi başlatmak için kullanılan yürütme bağlamını depolar ve işlem tamamlandığında önceki bağlamı geri yükler. <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>Ve <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> artık bu bağlamın bir parçası olduğundan, bir dağıtıcı işleminin içindeki değişiklikler işlem dışında kalıcı olmaz.

#### <a name="suggestion"></a>Öneri

Bu değişiklikten etkilenen uygulamalar, istenen <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> veya <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> bir alana depolayarak ve doğru ve ayarlanmış tüm dağıtıcı işlem <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> GÖVDELERININ (UI olay geri çağırma işleyicileri dahil) iade edilirken soruna geçici bir çözüm alabilir <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> . Alternatif olarak, bu WPF 'in temelindeki ExecutionContext değişikliği yalnızca .NET Framework 4,6 veya daha yeni bir sürümü hedefleyen uygulamaları etkilediği için, .NET Framework 4.5.2 hedefleyerek bu kesmeyi önlenebilir. .NET Framework 4,6 veya üzeri hedeflenen uygulamalar, aşağıdaki uyumluluk anahtarını ayarlayarak bu sorunu geçici olarak da gerçekleştirebilir:

<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>

Bu sorun WPF tarafından .NET Framework 4.6.2 içinde düzeltildi. Ayrıca, .NET Framework 4,6 ' de 4.6.1 ile [KB 3139549](https://support.microsoft.com/kb/3139549)arasında düzeltilmiştir. .NET Framework 4,6 veya sonraki bir sürümü hedefleyen uygulamalar, otomatik olarak WPF uygulamalarında doğru davranış alır- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) dağıtıcı işlemleri genelinde korunacaktır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

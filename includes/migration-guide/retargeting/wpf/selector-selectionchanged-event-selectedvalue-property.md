---
ms.openlocfilehash: e6c93a1bc31c041f36fca3704bca32012a2b42ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858974"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Seçici SeçimiDeğiştirilen olay ve SelectedValue özelliği

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ile <xref:System.Windows.Controls.Primitives.Selector> başlayarak, seçimi <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> değiştiğinde <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayı yükseltmeden önce mülkünün değerini her zaman güncelleştirir. Bu, SelectedValue özelliğini, olayı yükseltmeden <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>önce güncelleştirilen diğer seçim özellikleriyle<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> tutarlı hale getirir.<p/>.NET Framework 4.7 ve önceki sürümlerinde, SelectedValue güncelleştirmesi çoğu durumda olaydan önce gerçekleşti, ancak seçim <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> değişikliğinin özelliğin değiştirilmesinden kaynaklanıyorsa olaydan sonra gerçekleşti.|
|Öneri|.NET Framework 4.7.1 veya sonraki leri hedefleyen uygulamalar bu değişikliği devre dışı bırakıp <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının bölümüne aşağıdakileri ekleyerek eski davranışı kullanabilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7 veya daha öncesini hedefleyen ancak .NET Framework 4.7.1 veya sonraki bölümlerinde çalışan <code>&lt;runtime&gt;</code> uygulamalar, uygulama .configuration dosyasının bölümüne aşağıdaki satırı ekleyerek yeni davranışı etkinleştirebilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

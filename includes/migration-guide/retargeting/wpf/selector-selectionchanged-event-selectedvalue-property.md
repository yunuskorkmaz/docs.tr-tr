---
ms.openlocfilehash: e6c93a1bc31c041f36fca3704bca32012a2b42ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759519"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Seçici SelectionChanged olayı ve SelectedValue özelliği

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1, ile başlayarak bir <xref:System.Windows.Controls.Primitives.Selector> her zaman değerini güncelleştirir, <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özel durumu oluşturulmadan önce özellik <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> kendi seçimi değiştiğinde olay. Bu SelectedValue özelliği diğer seçimi özellikleri ile tutarlı hale getirir (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> ve <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), hangi olayı tetiklenmeden önce güncelleştirilir.<p/>Çoğu durumda olayından önce .NET Framework 4.7 ve önceki sürümlerle SelectedValue güncelleştirme oldu, ancak seçim değişikliği değiştirerek açtıysa sonra olay meydana geldiği <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği.|
|Öneri|Daha sonra bu dışında seçebilirsiniz veya .NET Framework 4.7.1'i hedefleyen uygulamalar değiştirin ve aşağıdaki ekleyerek eski davranışı kullanmaya <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7 veya önceki ancak hedefleyen uygulamaları .NET Framework 4.7.1 üzerinde çalışan veya daha sonra yeni davranış aşağıdaki satırı ekleyerek etkinleştirmek üzere <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

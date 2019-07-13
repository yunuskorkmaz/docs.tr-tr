---
ms.openlocfilehash: e80748c183a10cac4ef66c96ab48458cd9baa806
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858935"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionChanged olayı ve SelectedContent özelliği

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1, ile başlayarak bir <xref:System.Windows.Controls.TabControl> değerini güncelleştirir, <xref:System.Windows.Controls.TabControl.SelectedContent> özel durumu oluşturulmadan önce özellik <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> kendi seçimi değiştiğinde olay. .NET Framework 4.7 ve önceki sürümlerinde SelectedContent güncelleştirme etkinlikten sonra oldu.|
|Öneri|Daha sonra bu dışında seçebilirsiniz veya .NET Framework 4.7.1'i hedefleyen uygulamalar değiştirin ve aşağıdaki ekleyerek eski davranışı kullanmaya <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7 veya önceki ancak hedefleyen uygulamaları .NET Framework 4.7.1 üzerinde çalışan veya daha sonra yeni davranış aşağıdaki satırı ekleyerek etkinleştirmek üzere <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|`Scope`|Küçük|
|Version|4.7.1|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|


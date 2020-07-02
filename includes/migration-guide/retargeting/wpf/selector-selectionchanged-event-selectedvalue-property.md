---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614940"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Seçici SelectionChanged olayı ve SelectedValue özelliği

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 başlayarak, bir, <xref:System.Windows.Controls.Primitives.Selector> seçimi değiştiğinde olayı oluşturmadan önce her zaman <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliğinin değerini günceller <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Bu, SelectedValue özelliğini, <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> olayı oluşturmadan önce güncellenen diğer seçim özellikleriyle (ve) tutarlı hale getirir.<p/>.NET Framework 4,7 ve önceki sürümlerde, SelectedValue 'nin güncelleştirilmesi çoğu durumda olaydan önce gerçekleşti, ancak seçim değişikliği özelliği değiştirilmediğinde olay sonrasında gerçekleşiyor <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> .

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.1 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski davranışı kullanabilir:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

.NET Framework 4,7 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışan uygulamalar, `<runtime>` uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yeni davranışı etkinleştirebilir:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>

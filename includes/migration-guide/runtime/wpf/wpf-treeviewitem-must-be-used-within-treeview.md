---
ms.openlocfilehash: 88e00454894c8404fd48e92404e35ae27fa056f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235796"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>TreeView içinde TreeViewItem WPF kullanılmalıdır

|   |   |
|---|---|
|Ayrıntılar|Bir değişiklik kullanımını kısıtlayan 4.5 içinde tanıtılan <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> öğeler dışında bir <xref:System.Windows.Controls.TreeView?displayProperty=name>. Bu, aşağıdaki koşullarda bildirimleri:<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name>ın visual üst bir panel değil. (A <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> için oluşturulan bir <xref:System.Windows.Controls.TreeView?displayProperty=name> üst öğe olarak bir paneli gerekir)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> Alt öğesi olan bir <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> gören &quot;öğeleri ana&quot; listesi denetimi (ListBox, DataGrid, ListView, vb.). Sanallaştırma etkinleştirilmesi gerekmez.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> Öğesi kaydırma işlemi, (<code>ScrollUnit=&quot;Item&quot;</code>).</li><li>Birisi çağırır <code>VirtualizingStackPanel.MakeVisible(v)</code> öğenin kaydırma <code>v</code> gelsin. Bu açıkça veya dolaylı olarak çeşitli şekillerde yapılabilir; belki de en yaygın şekilde yalnızca tıklayarak <code>v</code> klavye odağı vermek için.</li><li>Görsel üst zincirinden <code>v</code> için <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> geçtiği <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>.</li></ul>Diğer bir deyişle, görülür olduğunda bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> dışında kullanılan bir <xref:System.Windows.Controls.TreeView?displayProperty=name>, ve kullanıcı bir alt öğesi üzerinde <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> görünüme getirmek için. Varsa <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> odaklanabilir hiçbir alt öğeleri olan, hiçbir zaman bu sorunu görürsünüz. Bir örneği burada bu isabet bir durum olduğunda bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> DataTemplate köküdür. Bu sorunu isabet edildiğinde WPF Framework'te oluşan bir InvalidCastException yoktur.|
|Öneri|Bir düzeltme bu için kullanılabilir hale getirilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

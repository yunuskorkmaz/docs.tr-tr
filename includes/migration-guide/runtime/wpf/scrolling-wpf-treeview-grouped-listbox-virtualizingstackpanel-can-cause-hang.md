---
ms.openlocfilehash: 0887379fb23e9e66c6cc55a3774545162634c3f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805252"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Bir WPF TreeView veya bir VirtualizingStackPanel gruplandırılmış liste kutusunda kaydırma bir yanıt vermemesine neden olabilir

|   |   |
|---|---|
|Ayrıntılar|Bir WPF .NET Framework v4.5, kaydırma <xref:System.Windows.Controls.TreeView?displayProperty=name> görünüm penceresinin içinde kenar boşlukları varsa sanallaştırılmış bir yığın paneli askıda neden olabilir (bulunan öğeler arasındaki <xref:System.Windows.Controls.TreeView?displayProperty=name>, örneğin veya ItemsPresenter öğe). Kenar boşlukları olsa bile ek olarak, bazı durumlarda, farklı boyutta öğeleri görünümünde tutarsızlığa neden olabilir.|
|Öneri|Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir. Alternatif olarak, kenar boşlukları görünümü koleksiyonlardan kaldırılabilir (gibi <xref:System.Windows.Controls.TreeView?displayProperty=name>s) sanallaştırılmış yığın içindeki tüm öğeleri içeriyorsa panelleri aynı boyuttadır.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

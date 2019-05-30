---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379225"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a>Bir WPF TreeView veya bir VirtualizingStackPanel gruplandırılmış liste kutusunda kaydırma, yanıt vermeyen bir uygulamaya neden olabilir

|   |   |
|---|---|
|Ayrıntılar|Bir WPF .NET Framework 4.5, kaydırma <xref:System.Windows.Controls.TreeView?displayProperty=name> sanallaştırılmış bir yığın paneli uygulamanın görünüm penceresinin içinde kenar boşlukları varsa yanıt veremez duruma gelmesine neden olabilir (bulunan öğeler arasındaki <xref:System.Windows.Controls.TreeView?displayProperty=name>, örneğin veya ItemsPresenter öğe). Kenar boşlukları olsa bile ek olarak, bazı durumlarda, farklı boyutta öğeleri görünümünde tutarsızlığa neden olabilir.|
|Öneri|Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir. Alternatif olarak, kenar boşlukları görünümü koleksiyonlardan kaldırılabilir (gibi <xref:System.Windows.Controls.TreeView?displayProperty=name>s) sanallaştırılmış yığın içindeki tüm öğeleri içeriyorsa panelleri aynı boyuttadır.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

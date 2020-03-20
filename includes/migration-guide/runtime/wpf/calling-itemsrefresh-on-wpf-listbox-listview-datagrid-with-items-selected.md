---
ms.openlocfilehash: a14395895c6be586c862d1b49aa6bf6669e4203a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238025"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Öğeleri Arama.WPF ListBox, ListView veya DataGrid'de seçili öğelerle birlikte yinelenen öğelerin öğede görünmesine neden olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5'te ListBox.Items.Refresh adlarında, öğeler <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilirken koddan yenileyin, seçili öğelerin listede çoğaltılmasına neden olabilir. Benzer bir sorun <xref:System.Windows.Controls.ListView?displayProperty=name> ile <xref:System.Windows.Controls.DataGrid?displayProperty=name>oluşur ve . Bu, .NET Framework 4.6'da sabittir.|
|Öneri|Bu sorun, çağrılmadan önce <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> programlı bir şekilde unselecting öğeleri ve ardından arama tamamlandıktan sonra yeniden seçerek üzerinde çalışılabilir. Alternatif olarak, bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

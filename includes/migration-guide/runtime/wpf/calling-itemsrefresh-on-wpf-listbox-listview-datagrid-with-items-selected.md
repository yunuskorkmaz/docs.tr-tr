---
ms.openlocfilehash: a14395895c6be586c862d1b49aa6bf6669e4203a
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238025"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Bir WPF ListBox, ListView veya seçili öğeleri içeren DataGrid arama Items.Refresh öğesinde görünmesini yinelenen öğeleri neden olabilir

|   |   |
|---|---|
|Ayrıntılar|İçindeki öğeleri seçili durumdayken ListBox.Items.Refresh içinden kodu çağırma .NET Framework 4.5 içinde bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeler listesinde çoğaltılacak neden olabilir. İle benzer bir sorun oluşur <xref:System.Windows.Controls.ListView?displayProperty=name> ve <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Bu .NET Framework 4.6 sabittir.|
|Öneri|Bu sorunu geçici olarak öğelere geçmeden önce programlı şekilde seçimini tarafından çalışması <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> olarak adlandırılır ve aramayı tamamladıktan sonra sonra yeniden seçerek. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

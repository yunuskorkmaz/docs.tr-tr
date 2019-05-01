---
ms.openlocfilehash: de73145273ad5aa5c19de55525417cfc3305b86d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093621"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Bir WPF ListBox, ListView veya seçili öğeleri içeren DataGrid arama Items.Refresh öğesinde görünmesini yinelenen öğeleri neden olabilir

|   |   |
|---|---|
|Ayrıntılar|İçindeki öğeleri seçili durumdayken ListBox.Items.Refresh içinden kodu çağırma .NET Framework 4.5 içinde bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeler listesinde çoğaltılacak neden olabilir. İle benzer bir sorun oluşur <xref:System.Windows.Controls.ListView?displayProperty=name> ve <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Bu .NET Framework 4.6 sabittir.|
|Öneri|Bu sorunu geçici olarak program aracılığıyla öğeleri önce seçimini tarafından çalışması <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> olarak adlandırılır ve aramayı tamamladıktan sonra sonra yeniden seçerek. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

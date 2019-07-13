---
ms.openlocfilehash: 22c67c687f5581c181acc4aeab8910c4467fd424
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858627"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Bir WPF ListBox, ListView veya seçili öğeleri içeren DataGrid arama Items.Refresh öğesinde görünmesini yinelenen öğeleri neden olabilir

|   |   |
|---|---|
|Ayrıntılar|İçindeki öğeleri seçili durumdayken ListBox.Items.Refresh içinden kodu çağırma .NET Framework 4.5 içinde bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeler listesinde çoğaltılacak neden olabilir. İle benzer bir sorun oluşur <xref:System.Windows.Controls.ListView?displayProperty=name> ve <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Bu .NET Framework 4.6 sabittir.|
|Öneri|Bu sorunu geçici olarak öğelere geçmeden önce programlı şekilde seçimini tarafından çalışması <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> olarak adlandırılır ve aramayı tamamladıktan sonra sonra yeniden seçerek. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|`Scope`|Küçük|
|Version|4,5|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|


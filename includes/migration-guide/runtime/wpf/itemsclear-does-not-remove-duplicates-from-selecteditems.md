---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235924"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear çoğaltmaları SelectedItems kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|Yinelenen bir seçici (ile birden çok seçimin etkin) sahip olduğunu varsayın kendi <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> aynı öğe koleksiyonu - görünür birden çok kez.  Bunları kaldırmak (örneğin Items.Clear çağırarak) veri kaynağından öğeleri kaldırma başarısız <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; yalnızca ilk örneği kaldırılır. Ayrıca, art arda kullanılması <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (örneğin SelectedItems.Clear()) gibi sorunlarla <xref:System.ArgumentException?displayProperty=name>, çünkü <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> artık veri kaynağındaki öğeleri içerir.|
|Öneri|Mümkünse, .NET Framework 4.6.2 yükseltin.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

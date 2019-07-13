---
ms.openlocfilehash: 2f94ec58e6fdb56cfc5147e74b6ffd6bb657228d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857502"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear çoğaltmaları SelectedItems kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|Yinelenen bir seçici (ile birden çok seçimin etkin) sahip olduğunu varsayın kendi <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> aynı öğe koleksiyonu - görünür birden çok kez.  Bunları kaldırmak (örneğin Items.Clear çağırarak) veri kaynağından öğeleri kaldırma başarısız <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; yalnızca ilk örneği kaldırılır. Ayrıca, art arda kullanılması <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (örneğin SelectedItems.Clear()) gibi sorunlarla <xref:System.ArgumentException?displayProperty=name>, çünkü <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> artık veri kaynağındaki öğeleri içerir.|
|Öneri|Mümkünse, .NET Framework 4.6.2 yükseltin.|
|`Scope`|Küçük|
|Version|4,5|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|


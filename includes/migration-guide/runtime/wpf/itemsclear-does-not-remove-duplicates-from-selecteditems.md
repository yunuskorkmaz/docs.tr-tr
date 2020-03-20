---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857502"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear, Yinelenenleri SelectedItems'tan kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|Bir Seçici'nin (birden çok seçim etkinleştirilmiş) <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> koleksiyonunda yinelenenleri olduğunu varsayalım - aynı öğe birden çok kez görünür.  Bu öğeleri veri kaynağından kaldırmak (örneğin Items.Clear'i arayarak) <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>bu öğeleri kaldıramıyor; yalnızca ilk örnek kaldırılır. Ayrıca, daha sonra <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> kullanımı (örneğin, SelectedItems.Clear()) gibi <xref:System.ArgumentException?displayProperty=name>sorunlarla <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> karşılaşabilirsiniz , çünkü artık veri kaynağında olmayan öğeler içerir.|
|Öneri|Mümkünse .NET Framework 4.6.2'ye yükseltin.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

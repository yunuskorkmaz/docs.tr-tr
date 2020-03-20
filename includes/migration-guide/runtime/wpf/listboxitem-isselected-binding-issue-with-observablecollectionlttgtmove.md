---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238020"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem ObservableCollection&lt;T&gt;ile bağlayıcılık sorunu seçili . Hareket

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> Seçili <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> öğelerle bir <xref:System.Windows.Controls.ListBox?displayProperty=name> koleksiyona bağlı arama veya bir koleksiyonda, <xref:System.Windows.Controls.ListBox?displayProperty=name> gelecekteki öğe seçimi veya unselection ile düzensiz davranışlara neden olabilir.|
|Öneri|Arama <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> ve <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> yerine bu sorunu çözmek olacaktır. Alternatif olarak, bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

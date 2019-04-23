---
ms.openlocfilehash: b761cb699c4677f815835cdab9c6aa3039f5bb38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805226"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectiontmove"></a>ObservableCollection ListBoxItem IsSelected bağlama sorun\<T >. Taşıma

|   |   |
|---|---|
|Ayrıntılar|Çağırma <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> veya <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> bağlı bir koleksiyonda bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeleri gelecekteki seçimi veya unselection, beklenmeyen davranışlara yol açabilir <xref:System.Windows.Controls.ListBox?displayProperty=name> öğeleri.|
|Öneri|Çağırma <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> yerine <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bu sorunu geçici olarak çalışır. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238020"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ObservableCollection ListBoxItem IsSelected bağlama sorun&lt;T&gt;. Taşıma

|   |   |
|---|---|
|Ayrıntılar|Çağırma <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> veya <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> bağlı bir koleksiyonda bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeleri gelecekteki seçimi veya unselection, beklenmeyen davranışlara yol açabilir <xref:System.Windows.Controls.ListBox?displayProperty=name> öğeleri.|
|Öneri|Çağırma <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> yerine <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bu sorunu geçici olarak çalışır. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

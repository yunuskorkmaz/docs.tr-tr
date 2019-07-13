---
ms.openlocfilehash: 778b6973b0a08e89471f9a4aa31a077da2d30c16
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858517"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ObservableCollection ListBoxItem IsSelected bağlama sorun&lt;T&gt;. Taşıma

|   |   |
|---|---|
|Ayrıntılar|Çağırma <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> veya <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> bağlı bir koleksiyonda bir <xref:System.Windows.Controls.ListBox?displayProperty=name> seçilen öğeleri gelecekteki seçimi veya unselection, beklenmeyen davranışlara yol açabilir <xref:System.Windows.Controls.ListBox?displayProperty=name> öğeleri.|
|Öneri|Çağırma <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> yerine <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bu sorunu geçici olarak çalışır. Alternatif olarak, bu sorun içinde .NET Framework 4.6 düzeltildi ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|`Scope`|Küçük|
|Version|4,5|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|


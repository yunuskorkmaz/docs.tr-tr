---
ms.openlocfilehash: 196b6a13d32c7767b858d6d68ca775eb49324805
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496751"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem IsSelected bağlama sorunu ObservableCollection &lt; T &gt; . Geçiş

#### <a name="details"></a>Ayrıntılar

<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> Öğesi ile bağlantılı bir koleksiyon üzerinde veya seçili bir koleksiyon üzerinde çağırma <xref:System.Windows.Controls.ListBox?displayProperty=fullName> , gelecekteki seçim veya öğelerin seçimini kaldırma ile Erratic davranışına neden olabilir <xref:System.Windows.Controls.ListBox?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

<xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName>Ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> yerine çağırmak, <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> Bu sorunu geçici olarak çözmek için kullanılır. Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.ObjectModel.ObservableCollection`1.Move(System.Int32,System.Int32)``
- ``M:System.Collections.ObjectModel.ObservableCollection`1.MoveItem(System.Int32,System.Int32)``

-->

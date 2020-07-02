---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620699"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

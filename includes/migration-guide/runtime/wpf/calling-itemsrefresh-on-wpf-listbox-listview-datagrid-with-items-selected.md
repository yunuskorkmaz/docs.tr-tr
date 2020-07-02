---
ms.openlocfilehash: 710d1517397f423fa40cc0c4a26c3499aac6179e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620682"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Öğeleri çağırma. bir WPF ListBox, ListView veya DataGrid üzerinde seçili öğeler içeren DataGrid 'de yenileme yinelenen öğelerin öğede görünmesine neden olabilir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, ListBox. Items ' ı çağırma. bir öğesinde öğeler seçildiğinde koddan Yenile <xref:System.Windows.Controls.ListBox?displayProperty=fullName> Seçili öğelerin listede yinelenmesine neden olabilir. Ve ile benzer bir sorun <xref:System.Windows.Controls.ListView?displayProperty=fullName> oluşur <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> . Bu .NET Framework 4,6 ' de düzeltilir.

#### <a name="suggestion"></a>Öneri

Bu sorun, çağrılmadan önce öğeleri seçerek <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> ve ardından çağrı tamamlandıktan sonra yeniden seçmeye çalışan geçici bir çözüm olabilir. Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

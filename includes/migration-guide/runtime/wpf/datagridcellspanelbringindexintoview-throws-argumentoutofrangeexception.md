---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496315"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel. BringIndexIntoView, ArgumentOutOfRangeException oluşturur

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> sütun sanallaştırma etkinleştirildiğinde zaman uyumsuz olarak çalışır, ancak sütun genişlikleri henüz belirlenmemiştir.  Zaman uyumsuz çalışma yapılmadan önce sütunlar kaldırılırsa, bir <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> gerçekleşebilir.

#### <a name="suggestion"></a>Öneri

Aşağıdakilerden biri:<ol><li>.NET Framework 4,7 ' ye yükseltin.</li><li>.NET Framework 4.6.2 için en son bakım düzeltme ekini yükler.</li><li>Zaman uyumsuz yanıt tamamlanana kadar sütunları kaldırmaktan kaçının <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> .</li></ol>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->

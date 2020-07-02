---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622386"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel. BringIndexIntoView, ArgumentOutOfRangeException oluşturur

#### <a name="details"></a>Ayrıntılar

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>sütun sanallaştırma etkinleştirildiğinde zaman uyumsuz olarak çalışır, ancak sütun genişlikleri henüz belirlenmemiştir.  Zaman uyumsuz çalışma yapılmadan önce sütunlar kaldırılırsa, bir <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> gerçekleşebilir.

#### <a name="suggestion"></a>Öneri

Aşağıdakilerden biri:<ol><li>.NET Framework 4,7 ' ye yükseltin.</li><li>.NET Framework 4.6.2 için en son bakım düzeltme ekini yükler.</li><li>Zaman uyumsuz yanıt tamamlanana kadar sütunları kaldırmaktan kaçının <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> .</li></ol>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

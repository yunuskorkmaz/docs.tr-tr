---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802465"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView ArgumentOutOfRangeException atar

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>sütun sanallaştırması etkinleştirildiğinde ancak sütun genişlikleri henüz belirlenmediğinde eş senkronize çalışacaktır.  Eşsenkronize çalışma gerçekleşmeden önce sütunlar <xref:System.ArgumentOutOfRangeException?displayProperty=name> kaldırılırsa, bir oluşabilir.|
|Öneri|Aşağıdakilerden herhangi biri:<ol><li>.NET Framework 4.7'ye yükseltin.</li><li>.NET Framework 4.6.2 için en son servis yasını yükleyin.</li><li>Asynchronous yanıtı tamamlanana kadar <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> sütunları kaldırmaktan kaçının.</li></ol>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236087"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>ArgumentOutOfRangeException DataGridCellsPanel.BringIndexIntoView oluşturur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> Sütun sanallaştırma etkinleştirilmiş ancak sütun genişliklerini henüz karar olduğunda zaman uyumsuz olarak çalışır.  Zaman uyumsuz iş gerçekleşmeden önce sütunları kaldırılırsa bir <xref:System.ArgumentOutOfRangeException?displayProperty=name> ortaya çıkabilir.|
|Öneri|Aşağıdakilerden herhangi biri:<ol><li>.NET Framework 4.7 yükseltin.</li><li>En son hizmet düzeltme eki için .NET Framework 4.6.2 yükleyin.</li><li>Zaman uyumsuz yanıt kadar sütunları kaldırmayı önlemek <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> tamamlandı.</li></ol>|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

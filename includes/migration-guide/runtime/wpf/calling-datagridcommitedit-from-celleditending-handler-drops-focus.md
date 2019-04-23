---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805290"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Odak bıraktığı CellEditEnding işleyicisinden DataGrid.CommitEdit çağırma

|   |   |
|---|---|
|Ayrıntılar|Çağırma <xref:System.Windows.Controls.DataGrid.CommitEdit> birinden <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> olay işleyicileri neden <xref:System.Windows.Controls.DataGrid?displayProperty=name> odak kaybetmesine.|
|Öneri|.NET Framework yükselterek önlenebilir için .NET Framework 4.5.2, bu hata düzeltildi. Alternatif olarak, bunu açıkça yeniden seçerek önlenebilir <xref:System.Windows.Controls.DataGrid?displayProperty=name> arama sonra <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

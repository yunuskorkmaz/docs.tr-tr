---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803161"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>CellEditEnding işleyicisinden DataGrid.CommitEdit'i arama

|   |   |
|---|---|
|Ayrıntılar|'Olay <xref:System.Windows.Controls.DataGrid.CommitEdit> işleyicilerinden birinden arama odaklanmak <xref:System.Windows.Controls.DataGrid?displayProperty=name> kaybetmesine neden olur. <xref:System.Windows.Controls.DataGrid?displayProperty=name> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name>|
|Öneri|Bu hata .NET Framework 4.5.2'de sabitlenmiştir, böylece .NET Framework yükseltilerek önlenebilir. Alternatif olarak, <xref:System.Windows.Controls.DataGrid?displayProperty=name> aramadan <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>sonra açıkça yeniden seçilerek önlenebilir.|
|Kapsam|Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

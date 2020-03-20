---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858431"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>WPF DataGrid'in seçili öğelerine DataGrid'in Boşaltma Satır olayının işleyicisinden erişmek NullReferenceException'a neden olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5'teki bir hata nedeniyle, <xref:System.Windows.Controls.DataGrid> bir satırın kaldırılmasını içeren olaylar <xref:System.NullReferenceException?displayProperty=name> için olay işleyicileri <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> , <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 'lerin veya özelliklerin erişimi sırasında bir hatanın atılmasına neden olabilir.|
|Öneri|Bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

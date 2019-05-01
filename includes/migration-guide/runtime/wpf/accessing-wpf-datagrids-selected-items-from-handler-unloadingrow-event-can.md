---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093624"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Bir WPF DataGrid'in seçili öğeler bir DataGrid'in UnloadingRow olay işleyicisinden erişme NullReferenceException neden olabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5, olay işleyicileri için bir hata nedeniyle <xref:System.Windows.Controls.DataGrid> kapsayan bir satır kaldırılmasını olayların neden olabilecek bir <xref:System.NullReferenceException?displayProperty=name> eriştiklerinde durum için <xref:System.Windows.Controls.DataGrid>ait <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> veya <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> özellikleri.|
|Öneri|Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

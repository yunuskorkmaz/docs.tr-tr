---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805257"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="7441e-101">Bir WPF DataGrid'in seçili öğeler bir DataGrid'in UnloadingRow olay işleyicisinden erişme NullReferenceException neden olabilir</span><span class="sxs-lookup"><span data-stu-id="7441e-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7441e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7441e-102">Details</span></span>|<span data-ttu-id="7441e-103">.NET Framework 4.5, olay işleyicileri için bir hata nedeniyle <xref:System.Windows.Controls.DataGrid> kapsayan bir satır kaldırılmasını olayların neden olabilecek bir <xref:System.NullReferenceException?displayProperty=name> eriştiklerinde durum için <xref:System.Windows.Controls.DataGrid>ait <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> veya <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7441e-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="7441e-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7441e-104">Suggestion</span></span>|<span data-ttu-id="7441e-105">Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7441e-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="7441e-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7441e-106">Scope</span></span>|<span data-ttu-id="7441e-107">İkincil</span><span class="sxs-lookup"><span data-stu-id="7441e-107">Minor</span></span>|
|<span data-ttu-id="7441e-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7441e-108">Version</span></span>|<span data-ttu-id="7441e-109">4,5</span><span class="sxs-lookup"><span data-stu-id="7441e-109">4.5</span></span>|
|<span data-ttu-id="7441e-110">Tür</span><span class="sxs-lookup"><span data-stu-id="7441e-110">Type</span></span>|<span data-ttu-id="7441e-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="7441e-111">Runtime</span></span>|
|<span data-ttu-id="7441e-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7441e-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

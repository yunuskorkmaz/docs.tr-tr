---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858431"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="1f749-101">WPF DataGrid'in seçili öğelerine DataGrid'in Boşaltma Satır olayının işleyicisinden erişmek NullReferenceException'a neden olabilir</span><span class="sxs-lookup"><span data-stu-id="1f749-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1f749-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1f749-102">Details</span></span>|<span data-ttu-id="1f749-103">.NET Framework 4.5'teki bir hata nedeniyle, <xref:System.Windows.Controls.DataGrid> bir satırın kaldırılmasını içeren olaylar <xref:System.NullReferenceException?displayProperty=name> için olay işleyicileri <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> , <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> 'lerin veya özelliklerin erişimi sırasında bir hatanın atılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f749-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="1f749-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="1f749-104">Suggestion</span></span>|<span data-ttu-id="1f749-105">Bu sorun .NET Framework 4.6'da giderilmiştir ve .NET Framework'ün bu sürümüne yükseltilerek giderilebilir.</span><span class="sxs-lookup"><span data-stu-id="1f749-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="1f749-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1f749-106">Scope</span></span>|<span data-ttu-id="1f749-107">İkincil</span><span class="sxs-lookup"><span data-stu-id="1f749-107">Minor</span></span>|
|<span data-ttu-id="1f749-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1f749-108">Version</span></span>|<span data-ttu-id="1f749-109">4,5</span><span class="sxs-lookup"><span data-stu-id="1f749-109">4.5</span></span>|
|<span data-ttu-id="1f749-110">Tür</span><span class="sxs-lookup"><span data-stu-id="1f749-110">Type</span></span>|<span data-ttu-id="1f749-111">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="1f749-111">Runtime</span></span>|
|<span data-ttu-id="1f749-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1f749-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|

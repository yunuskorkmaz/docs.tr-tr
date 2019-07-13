---
ms.openlocfilehash: 4b87fb0161059eb9df919a64a9966c00177caf89
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858431"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="7e455-101">Bir WPF DataGrid'in seçili öğeler bir DataGrid'in UnloadingRow olay işleyicisinden erişme NullReferenceException neden olabilir</span><span class="sxs-lookup"><span data-stu-id="7e455-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7e455-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7e455-102">Details</span></span>|<span data-ttu-id="7e455-103">.NET Framework 4.5, olay işleyicileri için bir hata nedeniyle <xref:System.Windows.Controls.DataGrid> kapsayan bir satır kaldırılmasını olayların neden olabilecek bir <xref:System.NullReferenceException?displayProperty=name> eriştiklerinde durum için <xref:System.Windows.Controls.DataGrid>ait <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> veya <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7e455-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="7e455-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7e455-104">Suggestion</span></span>|<span data-ttu-id="7e455-105">Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7e455-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="7e455-106">`Scope`</span><span class="sxs-lookup"><span data-stu-id="7e455-106">Scope</span></span>|<span data-ttu-id="7e455-107">Küçük</span><span class="sxs-lookup"><span data-stu-id="7e455-107">Minor</span></span>|
|<span data-ttu-id="7e455-108">Version</span><span class="sxs-lookup"><span data-stu-id="7e455-108">Version</span></span>|<span data-ttu-id="7e455-109">4,5</span><span class="sxs-lookup"><span data-stu-id="7e455-109">4.5</span></span>|
|<span data-ttu-id="7e455-110">Type</span><span class="sxs-lookup"><span data-stu-id="7e455-110">Type</span></span>|<span data-ttu-id="7e455-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="7e455-111">Runtime</span></span>|
|<span data-ttu-id="7e455-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7e455-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|


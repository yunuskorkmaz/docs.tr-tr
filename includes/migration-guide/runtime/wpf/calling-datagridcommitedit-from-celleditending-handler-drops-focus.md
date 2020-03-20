---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803161"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="b31a8-101">CellEditEnding işleyicisinden DataGrid.CommitEdit'i arama</span><span class="sxs-lookup"><span data-stu-id="b31a8-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b31a8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b31a8-102">Details</span></span>|<span data-ttu-id="b31a8-103">'Olay <xref:System.Windows.Controls.DataGrid.CommitEdit> işleyicilerinden birinden arama odaklanmak <xref:System.Windows.Controls.DataGrid?displayProperty=name> kaybetmesine neden olur. <xref:System.Windows.Controls.DataGrid?displayProperty=name> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name></span><span class="sxs-lookup"><span data-stu-id="b31a8-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="b31a8-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b31a8-104">Suggestion</span></span>|<span data-ttu-id="b31a8-105">Bu hata .NET Framework 4.5.2'de sabitlenmiştir, böylece .NET Framework yükseltilerek önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b31a8-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="b31a8-106">Alternatif olarak, <xref:System.Windows.Controls.DataGrid?displayProperty=name> aramadan <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>sonra açıkça yeniden seçilerek önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b31a8-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="b31a8-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b31a8-107">Scope</span></span>|<span data-ttu-id="b31a8-108">Edge</span><span class="sxs-lookup"><span data-stu-id="b31a8-108">Edge</span></span>|
|<span data-ttu-id="b31a8-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b31a8-109">Version</span></span>|<span data-ttu-id="b31a8-110">4,5</span><span class="sxs-lookup"><span data-stu-id="b31a8-110">4.5</span></span>|
|<span data-ttu-id="b31a8-111">Tür</span><span class="sxs-lookup"><span data-stu-id="b31a8-111">Type</span></span>|<span data-ttu-id="b31a8-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b31a8-112">Runtime</span></span>|
|<span data-ttu-id="b31a8-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b31a8-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

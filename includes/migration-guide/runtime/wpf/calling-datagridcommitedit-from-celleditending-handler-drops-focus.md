---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235939"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="590d5-101">Odak bıraktığı CellEditEnding işleyicisinden DataGrid.CommitEdit çağırma</span><span class="sxs-lookup"><span data-stu-id="590d5-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="590d5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="590d5-102">Details</span></span>|<span data-ttu-id="590d5-103">Çağırma <xref:System.Windows.Controls.DataGrid.CommitEdit> birinden <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> olay işleyicileri neden <xref:System.Windows.Controls.DataGrid?displayProperty=name> odak kaybetmesine.</span><span class="sxs-lookup"><span data-stu-id="590d5-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="590d5-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="590d5-104">Suggestion</span></span>|<span data-ttu-id="590d5-105">.NET Framework yükselterek önlenebilir için .NET Framework 4.5.2, bu hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="590d5-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="590d5-106">Alternatif olarak, bunu açıkça yeniden seçerek önlenebilir <xref:System.Windows.Controls.DataGrid?displayProperty=name> arama sonra <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="590d5-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="590d5-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="590d5-107">Scope</span></span>|<span data-ttu-id="590d5-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="590d5-108">Edge</span></span>|
|<span data-ttu-id="590d5-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="590d5-109">Version</span></span>|<span data-ttu-id="590d5-110">4,5</span><span class="sxs-lookup"><span data-stu-id="590d5-110">4.5</span></span>|
|<span data-ttu-id="590d5-111">Tür</span><span class="sxs-lookup"><span data-stu-id="590d5-111">Type</span></span>|<span data-ttu-id="590d5-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="590d5-112">Runtime</span></span>|
|<span data-ttu-id="590d5-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="590d5-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

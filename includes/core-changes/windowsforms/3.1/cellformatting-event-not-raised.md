---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721475"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="e90f4-101">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="e90f4-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="e90f4-102"><xref:System.Windows.Forms.DataGridView>Şimdi bir fare ve klavye aracılığıyla seçildiğinde bir hücrenin metin ve hata araç ipuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e90f4-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="e90f4-103">Bir araç ipucu gösteriliyorsa, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e90f4-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e90f4-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e90f4-104">Change description</span></span>

<span data-ttu-id="e90f4-105">.NET Core 3,1 ' den önce, <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özelliği, `true` hücrenin bir fare tarafından nasıl ele alındığı zaman bir hücrenin metin ve hataları için bir araç ipucu gösterilmişti olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e90f4-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="e90f4-106">Klavye aracılığıyla bir hücre seçildiğinde araç ipuçları gösterilmez (örneğin, sekme tuşunu, kısayol tuşlarını veya ok gezintisini kullanarak).</span><span class="sxs-lookup"><span data-stu-id="e90f4-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="e90f4-107">Kullanıcı bir hücreyi düzenlediyseniz ve sonra <xref:System.Windows.Forms.DataGridView> hala düzenleme modundayken, özelliği ayarlanmış olmayan bir hücrenin üzerine gelindiğinde, hücrede <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView.CellFormatting> görüntülenecek hücre metnini biçimlendirmek için bir olay harekete geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e90f4-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="e90f4-108">.NET Core 3,1 ' den başlayarak erişilebilirlik standartlarını karşılamak için, özelliği, bir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> `true` hücrenin metin ve hataları yalnızca hücre üzerine gelindiğinde değil, ancak klavye aracılığıyla seçilme durumunda olmayan bir hücrenin metin ve hatalarının araç ipuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e90f4-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="e90f4-109">Bu değişikliğin bir sonucu olarak, <xref:System.Windows.Forms.DataGridView.CellFormatting> özellik kümesi olmayan hücreler *not* <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> düzenleme modunda olduğunda olay oluşturulmaz <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="e90f4-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="e90f4-110">Vurgulanan hücrenin içeriği hücrede görüntülenmek yerine bir araç ipucu olarak gösterildiğinden olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e90f4-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e90f4-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e90f4-111">Version introduced</span></span>

<span data-ttu-id="e90f4-112">3,1</span><span class="sxs-lookup"><span data-stu-id="e90f4-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e90f4-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e90f4-113">Recommended action</span></span>

<span data-ttu-id="e90f4-114"><xref:System.Windows.Forms.DataGridView.CellFormatting>Düzenleme modundayken olaya bağlı tüm kodu <xref:System.Windows.Forms.DataGridView> yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e90f4-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="e90f4-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="e90f4-115">Category</span></span>

<span data-ttu-id="e90f4-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e90f4-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e90f4-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e90f4-117">Affected APIs</span></span>

<span data-ttu-id="e90f4-118">Yok</span><span class="sxs-lookup"><span data-stu-id="e90f4-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->

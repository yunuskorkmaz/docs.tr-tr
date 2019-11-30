---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567364"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="a44af-101">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="a44af-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="a44af-102">Bir <xref:System.Windows.Forms.DataGridView>, bir fare ve klavye aracılığıyla seçildiğinde bir hücrenin metin ve hata araç ipuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a44af-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="a44af-103">Bir araç ipucu gösteriliyorsa <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="a44af-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a44af-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a44af-104">Change description</span></span>

<span data-ttu-id="a44af-105">.NET Core 3,1 ' den önce, `true` olarak ayarlanan <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özelliği olan bir <xref:System.Windows.Forms.DataGridView>, hücrenin bir fare ile üzerine gelindiğinde bir hücrenin metin ve hataları için bir araç ipucu gösterdi.</span><span class="sxs-lookup"><span data-stu-id="a44af-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="a44af-106">Klavye aracılığıyla bir hücre seçildiğinde araç ipuçları gösterilmez (örneğin, sekme tuşunu, kısayol tuşlarını veya ok gezintisini kullanarak).</span><span class="sxs-lookup"><span data-stu-id="a44af-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="a44af-107">Kullanıcı bir hücreyi düzenlediyseniz ve sonra <xref:System.Windows.Forms.DataGridView> hala düzenleme modundayken, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özelliği ayarlanmamış bir hücrenin üzerine gelindiğinde, hücrede görüntülenecek hücre metnini biçimlendirmek için <xref:System.Windows.Forms.DataGridView.CellFormatting> bir olay harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a44af-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="a44af-108">.NET Core 3,1 ' den başlayarak erişilebilirlik standartlarını karşılamak için, <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> özelliği `true` olarak ayarlanmış bir <xref:System.Windows.Forms.DataGridView>, bir hücrenin metin ve hatalarının yalnızca hücre üzerine gelindiğinde değil, ancak klavye aracılığıyla seçilme durumunda olmayan bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="a44af-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="a44af-109">Bu değişikliğin bir sonucu olarak, <xref:System.Windows.Forms.DataGridView> düzenleme modundayken, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özelliği ayarlanmış olmayan hücreler üzerine gelindiğinde <xref:System.Windows.Forms.DataGridView.CellFormatting> *olayı oluşturulmaz.*</span><span class="sxs-lookup"><span data-stu-id="a44af-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="a44af-110">Vurgulanan hücrenin içeriği hücrede görüntülenmek yerine bir araç ipucu olarak gösterildiğinden olay oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="a44af-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a44af-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a44af-111">Version introduced</span></span>

<span data-ttu-id="a44af-112">3,1</span><span class="sxs-lookup"><span data-stu-id="a44af-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a44af-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a44af-113">Recommended action</span></span>

<span data-ttu-id="a44af-114"><xref:System.Windows.Forms.DataGridView> düzenleme modundayken <xref:System.Windows.Forms.DataGridView.CellFormatting> olayına bağlı tüm kodları yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="a44af-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="a44af-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="a44af-115">Category</span></span>

<span data-ttu-id="a44af-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a44af-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a44af-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a44af-117">Affected APIs</span></span>

<span data-ttu-id="a44af-118">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="a44af-118">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

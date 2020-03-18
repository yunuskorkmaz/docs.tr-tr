---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567364"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="ad9e0-101">Araç ipucu gösterilirse CellFormatting olayı yükseltilmez</span><span class="sxs-lookup"><span data-stu-id="ad9e0-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="ad9e0-102">Şimdi, <xref:System.Windows.Forms.DataGridView> bir fare tarafından gezinildiğinde ve klavye den seçildiğinde hücrenin metin ve hata araç uçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="ad9e0-103">Bir araç ipucu gösterilirse, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay yükseltilmez.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ad9e0-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="ad9e0-104">Change description</span></span>

<span data-ttu-id="ad9e0-105">.NET Core 3.1'den <xref:System.Windows.Forms.DataGridView> önce, <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> hücre `true` fare tarafından havada yken hücre metni ve hataları için bir araç ucu gösterebilecek özellik ayarlanmış bir özellik.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="ad9e0-106">Bir hücre klavye den seçildiğinde (örneğin, Sekme tuşu, kısayol tuşları veya ok gezintisi kullanılarak) araç ipuçları gösterilmedi.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="ad9e0-107">Kullanıcı bir hücreyi düzenlediyse ve <xref:System.Windows.Forms.DataGridView> daha sonra, düzenleme modundayken, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özellik kümesi olmayan bir hücrenin <xref:System.Windows.Forms.DataGridView.CellFormatting> üzerinde gezinilmişse, hücremetnini hücrede görüntülenmek üzere biçimlendirmek için bir olay yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="ad9e0-108">.NET Core 3.1'den başlayarak erişilebilirlik <xref:System.Windows.Forms.DataGridView> standartlarını karşılamak <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> için, `true` hücrenin metniiçin araç ipuçlarını ve yalnızca hücre havada yken değil, klavye aracılığıyla seçildiğinde de hatalar için araç ipuçlarını gösteren bir özellik kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="ad9e0-109">Bu değişikliğin bir sonucu <xref:System.Windows.Forms.DataGridView.CellFormatting> olarak, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> özellik kümesi olmayan hücreler akışlı olduğunda <xref:System.Windows.Forms.DataGridView> olay *yükseltilmez.*</span><span class="sxs-lookup"><span data-stu-id="ad9e0-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="ad9e0-110">Havada gezinilen hücrenin içeriği hücrede görüntülenmek yerine bir araç ucu olarak gösterildiğinden, olay yükseltilmez.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ad9e0-111">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="ad9e0-111">Version introduced</span></span>

<span data-ttu-id="ad9e0-112">3.1</span><span class="sxs-lookup"><span data-stu-id="ad9e0-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ad9e0-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ad9e0-113">Recommended action</span></span>

<span data-ttu-id="ad9e0-114">Düzenleme modundayken <xref:System.Windows.Forms.DataGridView.CellFormatting> <xref:System.Windows.Forms.DataGridView> olaya bağlı olan herhangi bir kodu yeniden düzenleme.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="ad9e0-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="ad9e0-115">Category</span></span>

<span data-ttu-id="ad9e0-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad9e0-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad9e0-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ad9e0-117">Affected APIs</span></span>

<span data-ttu-id="ad9e0-118">API analizi ile tespit edilemez.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-118">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

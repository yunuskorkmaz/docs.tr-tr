---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274981"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="9263f-101">WinForms API'ler şimdi ArgumentNullException atmak</span><span class="sxs-lookup"><span data-stu-id="9263f-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="9263f-102">Bazı Windows Forms yöntemleri <xref:System.ArgumentNullException> şimdi null bağımsız değişkenler <xref:System.NullReferenceException>için bir atmak, daha önce bir attı .</span><span class="sxs-lookup"><span data-stu-id="9263f-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9263f-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="9263f-103">Change description</span></span>

<span data-ttu-id="9263f-104">Daha önce, bazı Windows <xref:System.NullReferenceException> Forms yöntemleri null bir argüman geçti eğer attı.</span><span class="sxs-lookup"><span data-stu-id="9263f-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="9263f-105">.NET 5.0'dan başlayarak, <xref:System.ArgumentNullException> bu yöntemler artık null bağımsız değişkenler için bir şey atar.</span><span class="sxs-lookup"><span data-stu-id="9263f-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="9263f-106">.NET <xref:System.ArgumentNullException> çalışma zamanının davranışına uygun bir atma.</span><span class="sxs-lookup"><span data-stu-id="9263f-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="9263f-107">Ayrıca, bir bağımsız değişkenin boş olduğunu ve hangi bağımsız değişken olduğunu açıkça ifade ederek hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="9263f-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9263f-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="9263f-108">Version introduced</span></span>

<span data-ttu-id="9263f-109">.NET 5.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="9263f-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="9263f-110">.NET 5.0 Önizleme 2</span><span class="sxs-lookup"><span data-stu-id="9263f-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9263f-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9263f-111">Recommended action</span></span>

<span data-ttu-id="9263f-112">Bu yöntemlerden herhangi birini ararsanız ve <xref:System.NullReferenceException> kodunuz şu <xref:System.ArgumentNullException> anda null bağımsız değişkenler için yakalarsa, bunun yerine bir yakalama.</span><span class="sxs-lookup"><span data-stu-id="9263f-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="9263f-113">Buna ek olarak, listelenen yöntemlere null bağımsız değişkenleri geçmesini önlemek için kodu güncelleştirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="9263f-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="9263f-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="9263f-114">Category</span></span>

<span data-ttu-id="9263f-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9263f-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9263f-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9263f-116">Affected APIs</span></span>

<span data-ttu-id="9263f-117">.NET 5.0 Önizleme 1'den başlayarak:</span><span class="sxs-lookup"><span data-stu-id="9263f-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="9263f-118">.NET 5.0 Önizleme 2'den başlayarak:</span><span class="sxs-lookup"><span data-stu-id="9263f-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="9263f-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(yalnızca <xref:System.IO.Stream> parametre için)</span><span class="sxs-lookup"><span data-stu-id="9263f-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->

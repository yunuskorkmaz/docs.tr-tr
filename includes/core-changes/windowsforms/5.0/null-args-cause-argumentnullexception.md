---
ms.openlocfilehash: 7a6b0b15de4295506ff03b8566c06010b918566c
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158415"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="12041-101">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="12041-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="12041-102">Bazı Windows Forms Yöntemler artık, daha <xref:System.ArgumentNullException> önce bir <xref:System.NullReferenceException>oluşturduklarında null bağımsız değişkenler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12041-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="12041-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="12041-103">Change description</span></span>

<span data-ttu-id="12041-104">Daha önce, belirli Windows Forms Yöntemler, <xref:System.NullReferenceException> null olan bir bağımsız değişken geçirtiyse bir oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="12041-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="12041-105">.NET 5,0 ' den başlayarak, bu yöntemler artık bunun <xref:System.ArgumentNullException> yerine null bağımsız değişkenler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12041-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="12041-106">.NET çalışma <xref:System.ArgumentNullException> zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="12041-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="12041-107">Ayrıca, bir bağımsız değişkenin null ve hangi bağımsız değişkeni olduğunu açıkça bir şekilde iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="12041-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12041-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="12041-108">Version introduced</span></span>

<span data-ttu-id="12041-109">.NET 5,0 Preview 1 </span><span class="sxs-lookup"><span data-stu-id="12041-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="12041-110">.NET 5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="12041-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12041-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="12041-111">Recommended action</span></span>

<span data-ttu-id="12041-112">Bu yöntemlerin herhangi birini çağırırsanız ve kodunuz Şu anda bir <xref:System.NullReferenceException> boş bağımsız değişken için yakalar, bunun yerine bir <xref:System.ArgumentNullException> kullanın.</span><span class="sxs-lookup"><span data-stu-id="12041-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="12041-113">Ayrıca, belirtilen yöntemlere null bağımsız değişkenlerin geçirilmesini engellemek için kodu güncellemeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="12041-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="12041-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="12041-114">Category</span></span>

<span data-ttu-id="12041-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12041-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12041-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="12041-116">Affected APIs</span></span>

<span data-ttu-id="12041-117">.NET 5,0 Preview 1 ' den başlayarak:</span><span class="sxs-lookup"><span data-stu-id="12041-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="12041-118">.NET 5,0 Preview 2 ' den itibaren:</span><span class="sxs-lookup"><span data-stu-id="12041-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="12041-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(yalnızca <xref:System.IO.Stream> parametre için)</span><span class="sxs-lookup"><span data-stu-id="12041-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

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

---
ms.openlocfilehash: 7d00145bac473bd1799643a723b9e7928a3cd9a2
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281360"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="58ea1-101">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="58ea1-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="58ea1-102">Bazı Windows Forms Yöntemler artık <xref:System.ArgumentNullException> , daha önce bir oluşturduklarında null bağımsız değişkenler oluşturur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="58ea1-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="58ea1-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="58ea1-103">Change description</span></span>

<span data-ttu-id="58ea1-104">Daha önce, belirli Windows Forms Yöntemler, <xref:System.NullReferenceException> null olan bir bağımsız değişken geçirtiyse bir oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="58ea1-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="58ea1-105">.NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentNullException> bunun yerine null bağımsız değişkenler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58ea1-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="58ea1-106"><xref:System.ArgumentNullException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="58ea1-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="58ea1-107">Ayrıca, bir bağımsız değişkenin null ve hangi bağımsız değişkeni olduğunu açıkça bir şekilde iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="58ea1-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="58ea1-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="58ea1-108">Version introduced</span></span>

<span data-ttu-id="58ea1-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="58ea1-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="58ea1-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="58ea1-110">Recommended action</span></span>

<span data-ttu-id="58ea1-111">Bu yöntemlerin herhangi birini çağırırsanız ve kodunuz Şu anda bir <xref:System.NullReferenceException> boş bağımsız değişken için yakalar, <xref:System.ArgumentNullException> bunun yerine bir kullanın.</span><span class="sxs-lookup"><span data-stu-id="58ea1-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="58ea1-112">Ayrıca, belirtilen yöntemlere null bağımsız değişkenlerin geçirilmesini engellemek için kodu güncellemeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="58ea1-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="58ea1-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="58ea1-113">Category</span></span>

<span data-ttu-id="58ea1-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58ea1-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="58ea1-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="58ea1-115">Affected APIs</span></span>

<span data-ttu-id="58ea1-116">Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="58ea1-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="58ea1-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="58ea1-117">Method</span></span> | <span data-ttu-id="58ea1-118">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="58ea1-118">Parameter name</span></span> | <span data-ttu-id="58ea1-119">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="58ea1-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="58ea1-120">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="58ea1-121">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="58ea1-122">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="58ea1-123">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="58ea1-124">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="58ea1-125">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="58ea1-126">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="58ea1-127">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ea1-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="58ea1-128">Önizleme 2</span><span class="sxs-lookup"><span data-stu-id="58ea1-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="58ea1-129">Önizleme 2</span><span class="sxs-lookup"><span data-stu-id="58ea1-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="58ea1-130">Preview 5</span><span class="sxs-lookup"><span data-stu-id="58ea1-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="58ea1-131">Preview 5</span><span class="sxs-lookup"><span data-stu-id="58ea1-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="58ea1-132">Preview 5</span><span class="sxs-lookup"><span data-stu-id="58ea1-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="58ea1-133">Preview 5</span><span class="sxs-lookup"><span data-stu-id="58ea1-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="58ea1-134">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="58ea1-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="58ea1-135">`owner`, `value`</span></span> | <span data-ttu-id="58ea1-136">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="58ea1-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="58ea1-137">`owner`, `value`</span></span> | <span data-ttu-id="58ea1-138">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="58ea1-139">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="58ea1-140">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="58ea1-141">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="58ea1-142">Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="58ea1-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="58ea1-143">Önizleme 7</span><span class="sxs-lookup"><span data-stu-id="58ea1-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="58ea1-144">`key``null`veya boş</span><span class="sxs-lookup"><span data-stu-id="58ea1-144">`key` is `null` or empty</span></span> | <span data-ttu-id="58ea1-145">Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="58ea1-145">Preview 8</span></span> |

<!-- 

#### Affected APIs

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
- `M:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`

-->

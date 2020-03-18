---
ms.openlocfilehash: 10811a90887624a731c58d557e1dd196ae2c9207
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76508556"
---
### <a name="removed-controls"></a><span data-ttu-id="591d8-101">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="591d8-101">Removed controls</span></span>

<span data-ttu-id="591d8-102">.NET Core 3.1'den başlayarak, bazı Windows Forms denetimleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="591d8-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="591d8-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="591d8-103">Change description</span></span>

<span data-ttu-id="591d8-104">.NET Core 3.1'den başlayarak, çeşitli Windows Forms denetimleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="591d8-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="591d8-105">.NET Framework 2.0'da daha iyi tasarım ve desteğe sahip yedek denetimler tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="591d8-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="591d8-106">Amortismana alınan denetimler daha önce tasarımcı araç kutularından kaldırılmış, ancak yine de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="591d8-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="591d8-107">Aşağıdaki türler artık kullanılamıyor:</span><span class="sxs-lookup"><span data-stu-id="591d8-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.Design.IMenuEditorService>

#### <a name="version-introduced"></a><span data-ttu-id="591d8-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="591d8-108">Version introduced</span></span>

<span data-ttu-id="591d8-109">3.1</span><span class="sxs-lookup"><span data-stu-id="591d8-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="591d8-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="591d8-110">Recommended action</span></span>

<span data-ttu-id="591d8-111">Kaldırılan her denetimin önerilen değiştirme denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="591d8-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="591d8-112">Aşağıdaki tabloya bakın:</span><span class="sxs-lookup"><span data-stu-id="591d8-112">Refer to the following table:</span></span>

| <span data-ttu-id="591d8-113">Kaldırılan denetim (API)</span><span class="sxs-lookup"><span data-stu-id="591d8-113">Removed control (API)</span></span> | <span data-ttu-id="591d8-114">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="591d8-114">Recommended replacement</span></span> | <span data-ttu-id="591d8-115">Kaldırılan İlişkili API'ler</span><span class="sxs-lookup"><span data-stu-id="591d8-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="591d8-116">DataGrid</span><span class="sxs-lookup"><span data-stu-id="591d8-116">DataGrid</span></span> | <span data-ttu-id="591d8-117">Datagridview</span><span class="sxs-lookup"><span data-stu-id="591d8-117">DataGridView</span></span> | <span data-ttu-id="591d8-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span><span class="sxs-lookup"><span data-stu-id="591d8-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="591d8-119">ToolBar</span><span class="sxs-lookup"><span data-stu-id="591d8-119">ToolBar</span></span> | <span data-ttu-id="591d8-120">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="591d8-120">ToolStrip</span></span> | <span data-ttu-id="591d8-121">Araç Çubuğu Görünümü</span><span class="sxs-lookup"><span data-stu-id="591d8-121">ToolBarAppearance</span></span> |
| <span data-ttu-id="591d8-122">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="591d8-122">ToolBarButton</span></span> | <span data-ttu-id="591d8-123">Toolstripbutton</span><span class="sxs-lookup"><span data-stu-id="591d8-123">ToolStripButton</span></span> | <span data-ttu-id="591d8-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="591d8-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|
| <span data-ttu-id="591d8-125">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="591d8-125">ContextMenu</span></span> | <span data-ttu-id="591d8-126">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="591d8-126">ContextMenuStrip</span></span> | |
| <span data-ttu-id="591d8-127">Menü</span><span class="sxs-lookup"><span data-stu-id="591d8-127">Menu</span></span> | <span data-ttu-id="591d8-128">ToolStripDropDown, ToolStripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="591d8-128">ToolStripDropDown, ToolStripDropDownMenu</span></span> | <span data-ttu-id="591d8-129">Menuıtemcollection</span><span class="sxs-lookup"><span data-stu-id="591d8-129">MenuItemCollection</span></span> |
| <span data-ttu-id="591d8-130">Mainmenu</span><span class="sxs-lookup"><span data-stu-id="591d8-130">MainMenu</span></span> | <span data-ttu-id="591d8-131">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="591d8-131">MenuStrip</span></span> | |
| <span data-ttu-id="591d8-132">MenuItem</span><span class="sxs-lookup"><span data-stu-id="591d8-132">MenuItem</span></span> | <span data-ttu-id="591d8-133">Toolstripmenuıtem</span><span class="sxs-lookup"><span data-stu-id="591d8-133">ToolStripMenuItem</span></span> | |

#### <a name="category"></a><span data-ttu-id="591d8-134">Kategori</span><span class="sxs-lookup"><span data-stu-id="591d8-134">Category</span></span>

<span data-ttu-id="591d8-135">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="591d8-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="591d8-136">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="591d8-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->

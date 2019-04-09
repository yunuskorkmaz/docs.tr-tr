---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: cd3e88b5b01b67f677fbe203a0db9c4de7fe67ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160556"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="becca-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma</span><span class="sxs-lookup"><span data-stu-id="becca-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="becca-103">Seçili hücre, satır veya sütun alabileceğiniz bir <xref:System.Windows.Forms.DataGridView> karşılık gelen özelliklerini kullanarak denetim: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="becca-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="becca-104">Aşağıdaki yordamlarda, seçili hücreleri alma ve satır ve sütun dizinlerini görüntüleme bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="becca-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="becca-105">DataGridView denetiminde seçili hücre almak için</span><span class="sxs-lookup"><span data-stu-id="becca-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="becca-106">Kullanım <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="becca-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="becca-107">Kullanım <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> potansiyel olarak büyük bir hücre sayısını gösteren önlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="becca-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="becca-108">DataGridView denetiminde seçili satır almak için</span><span class="sxs-lookup"><span data-stu-id="becca-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="becca-109">Kullanım <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="becca-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="becca-110">Satırları seçmek kullanıcıları etkinleştirmek için ayarlamalısınız <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="becca-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="becca-111">DataGridView denetiminde Seçili sütunları almak için</span><span class="sxs-lookup"><span data-stu-id="becca-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="becca-112">Kullanım <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="becca-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="becca-113">Sütunları seçmek kullanıcıları etkinleştirmek için ayarlamalısınız <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="becca-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="becca-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="becca-114">Compiling the Code</span></span>  
 <span data-ttu-id="becca-115">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="becca-115">This example requires:</span></span>  
  
-   <xref:System.Windows.Forms.Button> <span data-ttu-id="becca-116">adlarında `selectedCellsButton`, `selectedRowsButton`, ve `selectedColumnsButton`, her biri için işleyiciler <xref:System.Windows.Forms.Control.Click> ekli olay.</span><span class="sxs-lookup"><span data-stu-id="becca-116">controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="becca-117">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="becca-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="becca-118">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Text?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="becca-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="becca-119">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="becca-119">Robust Programming</span></span>  
 <span data-ttu-id="becca-120">Bu konuda açıklanan koleksiyonları, çok sayıda hücreler, satırlar veya sütunlar seçili olduğunda verimli bir şekilde gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="becca-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="becca-121">Büyük miktarlarda veri bu koleksiyonlara kullanma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="becca-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becca-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="becca-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="becca-123">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="becca-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)

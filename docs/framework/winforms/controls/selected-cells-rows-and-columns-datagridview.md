---
title: DataGridView denetiminde seçili hücreleri, satırları ve sütunları al
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 0079c590ee6e4732523fd50be157bd58ec1bfb1b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743075"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="816eb-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma</span><span class="sxs-lookup"><span data-stu-id="816eb-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="816eb-103"><xref:System.Windows.Forms.DataGridView> denetiminden seçili hücreleri, satırları veya sütunları, ilgili özellikleri kullanarak alabilirsiniz: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="816eb-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="816eb-104">Aşağıdaki yordamlarda, seçili hücreleri alacak ve satır ve sütun dizinlerini bir <xref:System.Windows.Forms.MessageBox>görüntüleyecek şekilde görüntüleyirsiniz.</span><span class="sxs-lookup"><span data-stu-id="816eb-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="816eb-105">Bir DataGridView denetiminde seçili hücreleri almak için</span><span class="sxs-lookup"><span data-stu-id="816eb-105">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="816eb-106"><xref:System.Windows.Forms.DataGridView.SelectedCells%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="816eb-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="816eb-107">Potansiyel olarak çok sayıda hücre gösterilmemek için <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="816eb-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="816eb-108">Bir DataGridView denetiminde seçili satırları almak için</span><span class="sxs-lookup"><span data-stu-id="816eb-108">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="816eb-109"><xref:System.Windows.Forms.DataGridView.SelectedRows%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="816eb-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="816eb-110">Kullanıcıların satır seçmesini sağlamak için <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="816eb-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="816eb-111">Bir DataGridView denetiminde seçili sütunları almak için</span><span class="sxs-lookup"><span data-stu-id="816eb-111">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="816eb-112"><xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="816eb-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="816eb-113">Kullanıcıların sütun seçmesini sağlamak için <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="816eb-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="816eb-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="816eb-114">Compiling the Code</span></span>  
 <span data-ttu-id="816eb-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="816eb-115">This example requires:</span></span>  
  
- <span data-ttu-id="816eb-116">`selectedCellsButton`, `selectedRowsButton`ve `selectedColumnsButton`adlı, her biri <xref:System.Windows.Forms.Control.Click> olayı için işleyiciler içeren <xref:System.Windows.Forms.Button> denetimleri.</span><span class="sxs-lookup"><span data-stu-id="816eb-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="816eb-117">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="816eb-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="816eb-118"><xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>ve <xref:System.Text?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="816eb-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="816eb-119">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="816eb-119">Robust Programming</span></span>  
 <span data-ttu-id="816eb-120">Bu konu başlığı altında açıklanan koleksiyonlar, çok sayıda hücre, satır veya sütun seçildiğinde verimli bir şekilde gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="816eb-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="816eb-121">Bu koleksiyonları büyük miktarda verilerle kullanma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirmek Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="816eb-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816eb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="816eb-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="816eb-123">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="816eb-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)

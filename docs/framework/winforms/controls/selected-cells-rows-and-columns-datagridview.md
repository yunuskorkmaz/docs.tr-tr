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
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960523"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2921a-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma</span><span class="sxs-lookup"><span data-stu-id="2921a-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2921a-103">Bir <xref:System.Windows.Forms.DataGridView> denetimden seçili hücreleri, satırları veya sütunları, ilgili özellikleri kullanarak alabilirsiniz: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="2921a-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="2921a-104">Aşağıdaki yordamlarda, seçili hücreleri alacak ve satır ve sütun dizinlerini bir <xref:System.Windows.Forms.MessageBox>içinde görüntüleyecek.</span><span class="sxs-lookup"><span data-stu-id="2921a-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="2921a-105">Bir DataGridView denetiminde seçili hücreleri almak için</span><span class="sxs-lookup"><span data-stu-id="2921a-105">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="2921a-106"><xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2921a-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2921a-107">Olası çok sayıda hücreyi göstermeyi önlemek için yönteminikullanın.<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A></span><span class="sxs-lookup"><span data-stu-id="2921a-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="2921a-108">Bir DataGridView denetiminde seçili satırları almak için</span><span class="sxs-lookup"><span data-stu-id="2921a-108">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="2921a-109"><xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2921a-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="2921a-110">Kullanıcıların satır seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>olarak <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2921a-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="2921a-111">Bir DataGridView denetiminde seçili sütunları almak için</span><span class="sxs-lookup"><span data-stu-id="2921a-111">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="2921a-112"><xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> Özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2921a-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="2921a-113">Kullanıcıların sütun seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2921a-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2921a-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2921a-114">Compiling the Code</span></span>  
 <span data-ttu-id="2921a-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2921a-115">This example requires:</span></span>  
  
- <span data-ttu-id="2921a-116"><xref:System.Windows.Forms.Button>her biri `selectedCellsButton`, `selectedRowsButton` `selectedColumnsButton`eklenen olaya<xref:System.Windows.Forms.Control.Click> yönelik işleyiciler içeren,, ve adlı denetimler.</span><span class="sxs-lookup"><span data-stu-id="2921a-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="2921a-117"><xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.</span><span class="sxs-lookup"><span data-stu-id="2921a-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="2921a-118"><xref:System?displayProperty=nameWithType> ,<xref:System.Windows.Forms?displayProperty=nameWithType>Ve derlemelerinin<xref:System.Text?displayProperty=nameWithType> başvuruları.</span><span class="sxs-lookup"><span data-stu-id="2921a-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2921a-119">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2921a-119">Robust Programming</span></span>  
 <span data-ttu-id="2921a-120">Bu konu başlığı altında açıklanan koleksiyonlar, çok sayıda hücre, satır veya sütun seçildiğinde verimli bir şekilde gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="2921a-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="2921a-121">Bu koleksiyonları büyük miktarda verilerle kullanma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirmek Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2921a-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2921a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2921a-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="2921a-123">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="2921a-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)

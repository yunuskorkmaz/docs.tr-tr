---
title: DataGridView denetiminde seçili hücreleri, satırları ve sütunları al
description: Seçilen hücreleri, satırları veya sütunları, ilgili özellikleri kullanarak bir DataGridView denetiminden almayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904175"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="835a5-103">Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma</span><span class="sxs-lookup"><span data-stu-id="835a5-103">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="835a5-104">Bir denetimden seçili hücreleri, satırları veya sütunları, <xref:System.Windows.Forms.DataGridView> ilgili özellikleri kullanarak alabilirsiniz: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> .</span><span class="sxs-lookup"><span data-stu-id="835a5-104">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="835a5-105">Aşağıdaki yordamlarda, seçili hücreleri alacak ve satır ve sütun dizinlerini bir içinde görüntüleyecek <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="835a5-105">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="835a5-106">Bir DataGridView denetiminde seçili hücreleri almak için</span><span class="sxs-lookup"><span data-stu-id="835a5-106">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="835a5-107">Özelliğini kullanın <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> .</span><span class="sxs-lookup"><span data-stu-id="835a5-107">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="835a5-108"><xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>Olası çok sayıda hücreyi göstermeyi önlemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="835a5-108">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="835a5-109">Bir DataGridView denetiminde seçili satırları almak için</span><span class="sxs-lookup"><span data-stu-id="835a5-109">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="835a5-110">Özelliğini kullanın <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="835a5-110">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="835a5-111">Kullanıcıların satır seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya olarak ayarlamanız gerekir <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> .</span><span class="sxs-lookup"><span data-stu-id="835a5-111">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="835a5-112">Bir DataGridView denetiminde seçili sütunları almak için</span><span class="sxs-lookup"><span data-stu-id="835a5-112">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="835a5-113">Özelliğini kullanın <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> .</span><span class="sxs-lookup"><span data-stu-id="835a5-113">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="835a5-114">Kullanıcıların sütun seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya olarak ayarlamanız gerekir <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> .</span><span class="sxs-lookup"><span data-stu-id="835a5-114">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="835a5-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="835a5-115">Compiling the Code</span></span>  
 <span data-ttu-id="835a5-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="835a5-116">This example requires:</span></span>  
  
- <span data-ttu-id="835a5-117"><xref:System.Windows.Forms.Button>`selectedCellsButton` `selectedRowsButton` `selectedColumnsButton` her biri, eklenen olaya yönelik işleyiciler içeren,, ve adlı denetimler <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="835a5-117"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="835a5-118"><xref:System.Windows.Forms.DataGridView>Adlı bir denetim `dataGridView1` .</span><span class="sxs-lookup"><span data-stu-id="835a5-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="835a5-119"><xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> Ve <xref:System.Text?displayProperty=nameWithType> derlemelerinin başvuruları.</span><span class="sxs-lookup"><span data-stu-id="835a5-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="835a5-120">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="835a5-120">Robust Programming</span></span>  
 <span data-ttu-id="835a5-121">Bu konu başlığı altında açıklanan koleksiyonlar, çok sayıda hücre, satır veya sütun seçildiğinde verimli bir şekilde gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="835a5-121">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="835a5-122">Bu koleksiyonları büyük miktarda verilerle kullanma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirmek Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="835a5-122">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835a5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="835a5-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="835a5-124">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="835a5-124">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)

---
title: DataGridView Denetimindeki hücrelerin görünümünü özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744045"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="56033-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="56033-102">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="56033-103"><xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CellPainting> olayını işleyerek herhangi bir hücrenin görünümünü özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56033-103">You can customize the appearance of any cell by handling the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellPainting> event.</span></span> <span data-ttu-id="56033-104"><xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> özelliğinden ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56033-104">You can extract the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Drawing.Graphics> from the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>.</span></span> <span data-ttu-id="56033-105">Bu <xref:System.Drawing.Graphics>, tüm <xref:System.Windows.Forms.DataGridView> denetiminin görünümünü etkileyebilirsiniz, ancak genellikle boyanmış olan hücrenin görünümünü etkilemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="56033-105">With this <xref:System.Drawing.Graphics>, you can affect the appearance of the entire <xref:System.Windows.Forms.DataGridView> control, but you will usually want to affect only the appearance of the cell that is currently being painted.</span></span> <span data-ttu-id="56033-106"><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> özelliği, boyama işlemlerinizi Şu anda boyanmış olan hücreyle kısıtlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="56033-106">The <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> property of the <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> enables you to restrict your painting operations to the cell that is currently being painted.</span></span>  
  
 <span data-ttu-id="56033-107">Aşağıdaki kod örneğinde, bir `ContactName` sütunundaki tüm hücreleri <xref:System.Windows.Forms.DataGridView> denetimin renk düzenini kullanarak boyayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56033-107">In the following code example, you will paint all the cells in a `ContactName` column using the <xref:System.Windows.Forms.DataGridView> control's color scheme.</span></span> <span data-ttu-id="56033-108">Her hücrenin metin içeriği <xref:System.Drawing.Color.Crimson%2A>boyanır ve bir iç içe dikdörtgen <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliği ile aynı renge çizilir.</span><span class="sxs-lookup"><span data-stu-id="56033-108">Each cell's text content is painted in <xref:System.Drawing.Color.Crimson%2A>, and an inset rectangle is drawn in the same color as the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56033-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="56033-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56033-110">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="56033-110">Compiling the Code</span></span>  
 <span data-ttu-id="56033-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="56033-111">This example requires:</span></span>  
  
- <span data-ttu-id="56033-112">Northwind örnek veritabanındaki Customers tablosunda bulunan gibi bir `ContactName` sütunuyla `dataGridView1` adlı bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="56033-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a `ContactName` column such as the one in the Customers table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="56033-113">Sisteme, System. Windows. Forms ve System. Drawing derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="56033-113">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56033-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56033-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [<span data-ttu-id="56033-115">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="56033-115">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)

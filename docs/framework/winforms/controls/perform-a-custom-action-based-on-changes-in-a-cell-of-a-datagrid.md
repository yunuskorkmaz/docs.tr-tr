---
title: 'Nasıl yapılır: Bir Windows Forms DataGridView denetiminin bir hücresindeki değişikliklere dayalı olarak özel eylem gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: 125da277c2db44f01e6cad8cea08fbd927234f09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686861"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="77588-102">Nasıl yapılır: Bir Windows Forms DataGridView denetiminin bir hücresindeki değişikliklere dayalı olarak özel eylem gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77588-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="77588-103"><xref:System.Windows.Forms.DataGridView> Denetim olayları durumunda değişikliklerini algılamak için kullanabileceğiniz bir dizi sahip <xref:System.Windows.Forms.DataGridView> hücreleri.</span><span class="sxs-lookup"><span data-stu-id="77588-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="77588-104">En sık kullanılan iki <xref:System.Windows.Forms.DataGridView.CellValueChanged> ve <xref:System.Windows.Forms.DataGridView.CellStateChanged> olayları.</span><span class="sxs-lookup"><span data-stu-id="77588-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="77588-105">DataGridView hücrelerinin değerleri değişikliklerini algılamak için</span><span class="sxs-lookup"><span data-stu-id="77588-105">To detect changes in the values of DataGridView cells</span></span>  
  
-   <span data-ttu-id="77588-106">Yazma için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValueChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="77588-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="77588-107">DataGridView hücrelerinin durumlarda değişikliklerini algılamak için</span><span class="sxs-lookup"><span data-stu-id="77588-107">To detect changes in the states of DataGridView cells</span></span>  
  
-   <span data-ttu-id="77588-108">Yazma için bir işleyici <xref:System.Windows.Forms.DataGridView.CellStateChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="77588-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77588-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="77588-109">Compiling the Code</span></span>  
 <span data-ttu-id="77588-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="77588-110">This example requires:</span></span>  
  
-   <span data-ttu-id="77588-111">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="77588-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="77588-112">İçin C#, olay işleyicilerini olaylara karşılık gelen'e bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77588-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
-   <span data-ttu-id="77588-113">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="77588-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77588-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77588-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [<span data-ttu-id="77588-115">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="77588-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [<span data-ttu-id="77588-116">İzlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="77588-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)

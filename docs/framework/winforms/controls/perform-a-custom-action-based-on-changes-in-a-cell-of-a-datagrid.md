---
title: DataGridView denetiminin hücresindeki değişikliklere dayalı olarak özel eylem gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: a809134b0a79bc9685c5b84acce58b4c61b5c526
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744288"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="26b1d-102">Nasıl yapılır: Bir Windows Forms DataGridView Denetiminin Bir Hücresindeki Değişikliklere Dayalı Olarak Özel Eylem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="26b1d-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="26b1d-103"><xref:System.Windows.Forms.DataGridView> denetiminde, <xref:System.Windows.Forms.DataGridView> hücrelerinin durumundaki değişiklikleri algılamak için kullanabileceğiniz bir dizi olay vardır.</span><span class="sxs-lookup"><span data-stu-id="26b1d-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="26b1d-104">En yaygın olarak kullanılan ikisi <xref:System.Windows.Forms.DataGridView.CellValueChanged> ve <xref:System.Windows.Forms.DataGridView.CellStateChanged> olaylardır.</span><span class="sxs-lookup"><span data-stu-id="26b1d-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="26b1d-105">DataGridView hücrelerinin değerlerinde değişiklik algılamak için</span><span class="sxs-lookup"><span data-stu-id="26b1d-105">To detect changes in the values of DataGridView cells</span></span>  
  
- <span data-ttu-id="26b1d-106"><xref:System.Windows.Forms.DataGridView.CellValueChanged> olayı için bir işleyici yazın.</span><span class="sxs-lookup"><span data-stu-id="26b1d-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="26b1d-107">DataGridView hücrelerinin durumlarındaki değişiklikleri algılamak için</span><span class="sxs-lookup"><span data-stu-id="26b1d-107">To detect changes in the states of DataGridView cells</span></span>  
  
- <span data-ttu-id="26b1d-108"><xref:System.Windows.Forms.DataGridView.CellStateChanged> olayı için bir işleyici yazın.</span><span class="sxs-lookup"><span data-stu-id="26b1d-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26b1d-109">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="26b1d-109">Compiling the Code</span></span>  
 <span data-ttu-id="26b1d-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="26b1d-110">This example requires:</span></span>  
  
- <span data-ttu-id="26b1d-111">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="26b1d-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="26b1d-112">İçin C#, olay işleyicilerinin ilgili olaylara bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="26b1d-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
- <span data-ttu-id="26b1d-113"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="26b1d-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b1d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26b1d-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [<span data-ttu-id="26b1d-115">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="26b1d-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [<span data-ttu-id="26b1d-116">İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="26b1d-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)

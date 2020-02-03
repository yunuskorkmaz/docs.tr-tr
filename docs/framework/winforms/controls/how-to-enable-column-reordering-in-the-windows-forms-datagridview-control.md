---
title: DataGridView denetiminde sütun yeniden sıralamayı etkinleştir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 681489cdb874677079e2577140040921e587d21e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745489"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="71173-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="71173-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="71173-103"><xref:System.Windows.Forms.DataGridView> denetiminde sütun yeniden sıralamayı etkinleştirdiğinizde, kullanıcılar sütun başlığını fareyle sürükleyerek bir sütunu yeni bir konuma taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="71173-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="71173-104"><xref:System.Windows.Forms.DataGridView> denetiminde, <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> Özellik değeri, kullanıcıların sütunları farklı konumlara taşıyıp taşıyamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="71173-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="71173-105">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="71173-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="71173-106">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütun yeniden sıralamayı etkinleştirme](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="71173-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="71173-107">Sütun yeniden sıralamayı programlı olarak etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="71173-107">To enable column reordering programmatically</span></span>  
  
- <span data-ttu-id="71173-108"><xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71173-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71173-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="71173-109">Compiling the Code</span></span>  
 <span data-ttu-id="71173-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="71173-110">This example requires:</span></span>  
  
- <span data-ttu-id="71173-111">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="71173-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="71173-112"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="71173-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71173-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71173-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="71173-114">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="71173-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="71173-115">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="71173-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)

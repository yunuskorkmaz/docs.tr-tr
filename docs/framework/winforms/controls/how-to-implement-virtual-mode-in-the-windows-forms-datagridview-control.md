---
title: DataGridView denetiminde sanal modu uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode
- DataGridView control [Windows Forms], large data sets
ms.assetid: 98236267-f08e-4918-bcf9-77acf050a3ca
ms.openlocfilehash: f8612a808ac5c9facee55d820529945f481a2cea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736515"
---
# <a name="how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9f35f-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9f35f-102">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9f35f-103">Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView> bir denetim kullanılarak <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`olarak ayarlanan büyük veri kümelerinin nasıl yönetileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f35f-103">The following code example demonstrates how to manage large sets of data using a <xref:System.Windows.Forms.DataGridView> control with its <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property set to `true`.</span></span>  
  
 <span data-ttu-id="9f35f-104">Bu kod örneği hakkında ayrıntılı bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9f35f-104">For a complete explanation of this code example, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f35f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f35f-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#000)]
 [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f35f-106">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="9f35f-106">Compiling the Code</span></span>  
 <span data-ttu-id="9f35f-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9f35f-107">This example requires:</span></span>  
  
- <span data-ttu-id="9f35f-108">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="9f35f-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f35f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f35f-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="9f35f-110">İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9f35f-110">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)
- [<span data-ttu-id="9f35f-111">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="9f35f-111">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f35f-112">Windows Forms DataGridView Denetiminde Sanal Mod</span><span class="sxs-lookup"><span data-stu-id="9f35f-112">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)

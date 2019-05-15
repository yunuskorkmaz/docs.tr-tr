---
title: 'Nasıl yapılır: ToolStripPanel Denetimleriyle MDI Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
ms.openlocfilehash: 4dae528d69c6c08c2005fd30d7d16fafa67afb53
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590551"
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="f5fdd-102">Nasıl yapılır: ToolStripPanel Denetimleriyle MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5fdd-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="f5fdd-103">Sahip birden çok belge arabirimi (MDI) formu oluşturabilirsiniz <xref:System.Windows.Forms.ToolStrip> dört dışlamada çerçeveleme denetimleri.</span><span class="sxs-lookup"><span data-stu-id="f5fdd-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5fdd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5fdd-104">Example</span></span>  
 <span data-ttu-id="f5fdd-105">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. yerleşik <xref:System.Windows.Forms.ToolStripPanel> dört ile bir MDI pencere çerçevesi için denetimleri <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f5fdd-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="f5fdd-106">Örnekte, <xref:System.Windows.Forms.ToolStripPanel.Join%2A> yöntemi ekler <xref:System.Windows.Forms.ToolStrip> denetimleri karşılık gelen <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f5fdd-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5fdd-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f5fdd-107">Compiling the Code</span></span>  
 <span data-ttu-id="f5fdd-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f5fdd-108">This example requires:</span></span>  
  
- <span data-ttu-id="f5fdd-109">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f5fdd-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5fdd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5fdd-110">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="f5fdd-111">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="f5fdd-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

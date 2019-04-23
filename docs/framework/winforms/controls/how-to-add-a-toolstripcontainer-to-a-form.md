---
title: 'Nasıl yapılır: Forma ToolStripContainer Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: d70c5b8f548cf325083782d6ea185c18fd2fa003
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216216"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="e747f-102">Nasıl yapılır: Forma ToolStripContainer Ekleme</span><span class="sxs-lookup"><span data-stu-id="e747f-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="e747f-103">Program aracılığıyla ekleyebilirsiniz bir <xref:System.Windows.Forms.ToolStripContainer> bir Windows forma ve denetimleri ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e747f-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e747f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e747f-104">Example</span></span>  
 <span data-ttu-id="e747f-105">Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir. bir <xref:System.Windows.Forms.ToolStripContainer> ve <xref:System.Windows.Forms.ToolStrip> için bir Windows Forms için öğelerin nasıl eklendiğini <xref:System.Windows.Forms.ToolStrip>ve ekleme <xref:System.Windows.Forms.ToolStrip> için <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> , <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="e747f-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e747f-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e747f-106">Compiling the Code</span></span>  
 <span data-ttu-id="e747f-107">Bu kod örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e747f-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="e747f-108">System.Drawing System.Text ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="e747f-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e747f-109">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e747f-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e747f-110">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e747f-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e747f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e747f-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="e747f-112">ToolStripContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="e747f-112">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="e747f-113">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="e747f-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

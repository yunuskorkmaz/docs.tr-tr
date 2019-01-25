---
title: 'Nasıl yapılır: Bir forma ToolStripContainer ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 9aace854a9583268ef7aac6ac1f57534cfdfe1e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515527"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="27d79-102">Nasıl yapılır: Bir forma ToolStripContainer ekleme</span><span class="sxs-lookup"><span data-stu-id="27d79-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="27d79-103">Program aracılığıyla ekleyebilirsiniz bir <xref:System.Windows.Forms.ToolStripContainer> bir Windows forma ve denetimleri ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27d79-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27d79-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="27d79-104">Example</span></span>  
 <span data-ttu-id="27d79-105">Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir. bir <xref:System.Windows.Forms.ToolStripContainer> ve <xref:System.Windows.Forms.ToolStrip> için bir Windows Forms için öğelerin nasıl eklendiğini <xref:System.Windows.Forms.ToolStrip>ve ekleme <xref:System.Windows.Forms.ToolStrip> için <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> , <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="27d79-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27d79-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="27d79-106">Compiling the Code</span></span>  
 <span data-ttu-id="27d79-107">Bu kod örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="27d79-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="27d79-108">System.Drawing System.Text ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="27d79-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="27d79-109">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="27d79-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="27d79-110">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27d79-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="27d79-111">Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) veya [ToolStripContainer görevleri iletişim kutusu](https://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="27d79-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](https://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d79-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27d79-112">See also</span></span>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="27d79-113">ToolStripContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="27d79-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)
- [<span data-ttu-id="27d79-114">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="27d79-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

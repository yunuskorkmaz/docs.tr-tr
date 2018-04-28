---
title: 'Nasıl yapılır: ToolStripPanel Denetimleriyle MDI Formu Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8c10c7a74e0562c59708b721f662ab95eadc23b4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="0a1a0-102">Nasıl yapılır: ToolStripPanel Denetimleriyle MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a1a0-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="0a1a0-103">Sahip birden çok belge arabirimi (MDI) form oluşturabilirsiniz <xref:System.Windows.Forms.ToolStrip> tüm dört tarafta çerçeveleme kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0a1a0-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a1a0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a1a0-104">Example</span></span>  
 <span data-ttu-id="0a1a0-105">Aşağıdaki kod örneğinde nasıl kullanılacağı gösterilmektedir yerleşik <xref:System.Windows.Forms.ToolStripPanel> dört ile MDI pencere çerçevesi için denetimleri <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0a1a0-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="0a1a0-106">Örnekte, <xref:System.Windows.Forms.ToolStripPanel.Join%2A> yöntemi ekler <xref:System.Windows.Forms.ToolStrip> denetimleri karşılık gelen <xref:System.Windows.Forms.ToolStripPanel> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0a1a0-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0a1a0-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0a1a0-107">Compiling the Code</span></span>  
 <span data-ttu-id="0a1a0-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0a1a0-108">This example requires:</span></span>  
  
-   <span data-ttu-id="0a1a0-109">System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="0a1a0-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0a1a0-110">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0a1a0-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0a1a0-111">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a1a0-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0a1a0-112">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0a1a0-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1a0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a1a0-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 <xref:System.Windows.Forms.ToolStripPanel.Join%2A>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="0a1a0-114">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="0a1a0-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

---
title: 'Nasıl yapılır: Bir StatusStrip içinde Spring özelliğini etkileşimli kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: cfce4e75d47bcaf67610312b95093282f9d1fa91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582296"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="f8c53-102">Nasıl yapılır: Bir StatusStrip içinde Spring özelliğini etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="f8c53-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="f8c53-103">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> konumlandırmak için özellik bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimine bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f8c53-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="f8c53-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Özelliği olup olmadığını <xref:System.Windows.Forms.ToolStripStatusLabel> denetimi otomatik olarak mevcut alan doldurulur üzerinde <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f8c53-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c53-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8c53-105">Example</span></span>  
 <span data-ttu-id="f8c53-106">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> konumlandırmak için özellik bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimine bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f8c53-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="f8c53-107"><xref:System.Windows.Forms.ToolStripItem.Click> Olay işleyicisi bir özel gerçekleştirir- ya da değerini değiştirmek için (XOR) işlemi <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8c53-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="f8c53-108">Bu kod örneği kullanmak için derlemek ve uygulamayı çalıştırın ve ardından **Orta (Spring)** üzerinde <xref:System.Windows.Forms.StatusStrip> değerini değiştirmek için Denetim <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8c53-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8c53-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f8c53-109">Compiling the Code</span></span>  
 <span data-ttu-id="f8c53-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8c53-110">This example requires:</span></span>  
  
-   <span data-ttu-id="f8c53-111">System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f8c53-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f8c53-112">Visual Basic veya Visual C# için komut satırından Bu örnek oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f8c53-112">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f8c53-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c53-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f8c53-114">Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f8c53-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c53-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c53-115">See also</span></span>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="f8c53-116">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="f8c53-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

---
title: 'Nasıl yapılır: Bir StatusStrip içinde Spring Özelliğini Etkileşimli Kullanma'
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
ms.openlocfilehash: e3818beb96a7c005ea02bc04e9ea740b28a54707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533802"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="44410-102">Nasıl yapılır: Bir StatusStrip içinde Spring Özelliğini Etkileşimli Kullanma</span><span class="sxs-lookup"><span data-stu-id="44410-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="44410-103">Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> konumlandırmak için özellik bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetim bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="44410-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="44410-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Özelliği belirler olup olmadığını <xref:System.Windows.Forms.ToolStripStatusLabel> denetimi otomatik olarak doldurur kullanılabilir alanı üzerinde <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="44410-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44410-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="44410-105">Example</span></span>  
 <span data-ttu-id="44410-106">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> konumlandırmak için özellik bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetim bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="44410-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="44410-107"><xref:System.Windows.Forms.ToolStripItem.Click> Olay işleyicisi gerçekleştiren bir özel- ya da değerini geçiş yapmak için (XOR) işlemi <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="44410-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="44410-108">Bu kod örneği kullanmak için derleme ve uygulamayı çalıştırın ve ardından **Orta (yay)** üzerinde <xref:System.Windows.Forms.StatusStrip> değerini geçiş yapmak için Denetim <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="44410-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44410-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="44410-109">Compiling the Code</span></span>  
 <span data-ttu-id="44410-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="44410-110">This example requires:</span></span>  
  
-   <span data-ttu-id="44410-111">System.Design, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="44410-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="44410-112">Bu örnek visual Basic veya Visual C# için komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="44410-112">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="44410-113">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44410-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="44410-114">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="44410-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44410-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44410-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="44410-116">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="44410-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

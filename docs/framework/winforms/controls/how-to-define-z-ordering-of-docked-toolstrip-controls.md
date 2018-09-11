---
title: 'Nasıl yapılır: Yerleştirilmiş ToolStrip Denetimlerinin Z Sıralamasını Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 34d600454a7fa63c7ba59bebded6365cd5401cb4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360907"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="5d87b-102">Nasıl yapılır: Yerleştirilmiş ToolStrip Denetimlerinin Z Sıralamasını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5d87b-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="5d87b-103">Konumuna bir <xref:System.Windows.Forms.ToolStrip> denetimi doğru şekilde yerleştirme ile denetim doğru formun z düzeninde hizalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d87b-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d87b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d87b-104">Example</span></span>  
 <span data-ttu-id="5d87b-105">Aşağıdaki kod örneğinde nasıl düzenleneceğini gösterir bir <xref:System.Windows.Forms.ToolStrip> denetimi ve bir yerleşik <xref:System.Windows.Forms.MenuStrip> z düzenini belirterek denetimi.</span><span class="sxs-lookup"><span data-stu-id="5d87b-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="5d87b-106">Z düzenini sıralarına göre belirlenir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="5d87b-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="5d87b-107">denetimler, formun eklenir <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5d87b-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="5d87b-108">Bu çağrılar için sırasını ters <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> yöntemi ve görünüm düzenini üzerindeki etkisi.</span><span class="sxs-lookup"><span data-stu-id="5d87b-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d87b-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5d87b-109">Compiling the Code</span></span>  
 <span data-ttu-id="5d87b-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5d87b-110">This example requires:</span></span>  
  
-   <span data-ttu-id="5d87b-111">System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="5d87b-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5d87b-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5d87b-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5d87b-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d87b-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="5d87b-114">Ayrıca se [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5d87b-114">Also se [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d87b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d87b-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>  
 <xref:System.Windows.Forms.Control.Controls%2A>  
 <xref:System.Windows.Forms.Control.Dock%2A>  
 [<span data-ttu-id="5d87b-116">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="5d87b-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

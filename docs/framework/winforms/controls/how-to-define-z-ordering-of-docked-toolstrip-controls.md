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
ms.openlocfilehash: 3347722383b7388c00335683537e00851e642bb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129174"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="3ce3a-102">Nasıl yapılır: Yerleştirilmiş ToolStrip Denetimlerinin Z Sıralamasını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="3ce3a-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="3ce3a-103">Konumuna bir <xref:System.Windows.Forms.ToolStrip> denetimi doğru şekilde yerleştirme ile denetim doğru formun z düzeninde hizalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ce3a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ce3a-104">Example</span></span>  
 <span data-ttu-id="3ce3a-105">Aşağıdaki kod örneğinde nasıl düzenleneceğini gösterir bir <xref:System.Windows.Forms.ToolStrip> denetimi ve bir yerleşik <xref:System.Windows.Forms.MenuStrip> z düzenini belirterek denetimi.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="3ce3a-106">Z düzenini sıralarına göre belirlenir <xref:System.Windows.Forms.ToolStrip> ve</span><span class="sxs-lookup"><span data-stu-id="3ce3a-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and</span></span> <xref:System.Windows.Forms.MenuStrip>  
  
 <span data-ttu-id="3ce3a-107">denetimler, formun eklenir <xref:System.Windows.Forms.Control.Controls%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="3ce3a-108">Bu çağrılar için sırasını ters <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> yöntemi ve görünüm düzenini üzerindeki etkisi.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ce3a-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3ce3a-109">Compiling the Code</span></span>  
 <span data-ttu-id="3ce3a-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3ce3a-110">This example requires:</span></span>  
  
-   <span data-ttu-id="3ce3a-111">System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3ce3a-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3ce3a-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3ce3a-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce3a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ce3a-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [<span data-ttu-id="3ce3a-115">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="3ce3a-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

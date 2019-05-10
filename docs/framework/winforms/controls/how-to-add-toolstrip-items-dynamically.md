---
title: 'Nasıl yapılır: Dinamik Olarak ToolStrip Öğeleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 9426c7cb3251dbbd95727b78c57be7a0b71556e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624022"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="4f182-102">Nasıl yapılır: Dinamik Olarak ToolStrip Öğeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="4f182-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="4f182-103">Dinamik olarak menü öğesi koleksiyonu doldurmak bir <xref:System.Windows.Forms.ToolStrip> menü ne zaman açıldığını kontrol.</span><span class="sxs-lookup"><span data-stu-id="4f182-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f182-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f182-104">Example</span></span>  
 <span data-ttu-id="4f182-105">Aşağıdaki kod örneği, dinamik olarak öğe ekleme yapmayı gösteren bir <xref:System.Windows.Forms.ContextMenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4f182-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="4f182-106">Örnek ayrıca nasıl aynı yeniden gösterir <xref:System.Windows.Forms.ContextMenuStrip> formda üç farklı denetimler için.</span><span class="sxs-lookup"><span data-stu-id="4f182-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="4f182-107">Örnekte, bir <xref:System.Windows.Forms.ToolStripDropDown.Opening> olay işleyicisi menü öğesi koleksiyonu doldurur.</span><span class="sxs-lookup"><span data-stu-id="4f182-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="4f182-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> Olay işleyicisi inceler <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> özellikleri ve ekler bir <xref:System.Windows.Forms.ToolStripItem> açıklayan kaynak denetimi.</span><span class="sxs-lookup"><span data-stu-id="4f182-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f182-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4f182-109">Compiling the Code</span></span>  
 <span data-ttu-id="4f182-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4f182-110">This example requires:</span></span>  
  
- <span data-ttu-id="4f182-111">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="4f182-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4f182-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4f182-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4f182-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f182-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f182-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f182-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="4f182-115">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="4f182-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

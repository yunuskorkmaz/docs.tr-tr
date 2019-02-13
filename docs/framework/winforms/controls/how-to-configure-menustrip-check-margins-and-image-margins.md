---
title: 'Nasıl yapılır: Yapılandırma MenuStrip denetim kenar boşluklarını ve görüntü kenar boşluklarını'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
ms.openlocfilehash: ab606e126d346332f3da1ca1281372f3cce8f7ab
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219068"
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="f0f5d-102">Nasıl yapılır: Yapılandırma MenuStrip denetim kenar boşluklarını ve görüntü kenar boşluklarını</span><span class="sxs-lookup"><span data-stu-id="f0f5d-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="f0f5d-103">Özelleştirebileceğiniz bir <xref:System.Windows.Forms.MenuStrip> ayarlayarak <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> ve <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> çeşitli birleşimlerini özellikleri.</span><span class="sxs-lookup"><span data-stu-id="f0f5d-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0f5d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0f5d-104">Example</span></span>  
 <span data-ttu-id="f0f5d-105">Aşağıdaki kod örneği, ayarlayın ve özelleştirmek gösterilmiştir <xref:System.Windows.Forms.ContextMenuStrip> kenar boşluklarını ve görüntü kenar boşluklarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f0f5d-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="f0f5d-106">Yordam için aynı olan bir <xref:System.Windows.Forms.ContextMenuStrip> veya <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f0f5d-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0f5d-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f0f5d-107">Compiling the Code</span></span>  
 <span data-ttu-id="f0f5d-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f0f5d-108">This example requires:</span></span>  
  
-   <span data-ttu-id="f0f5d-109">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f0f5d-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f0f5d-110">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f0f5d-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f0f5d-111">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0f5d-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f5d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0f5d-112">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="f0f5d-113">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="f0f5d-113">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
- [<span data-ttu-id="f0f5d-114">Nasıl yapılır: Kenar boşluklarını ve görüntü kenar boşluklarını ContextMenuStrip denetimlerinde denetim etkinleştir</span><span class="sxs-lookup"><span data-stu-id="f0f5d-114">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)

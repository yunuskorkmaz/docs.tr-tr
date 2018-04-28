---
title: 'Nasıl yapılır: ContextMenuStrip Denetim Kenar Boşluklarını ve Görüntü Kenar Boşluklarını Yapılandırma'
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
- context menus [Windows Forms], configuring check and image margins
- ContextMenuStrips [Windows Forms], configuring check and image margins
- margins [Windows Forms], setting check and image in Windows Forms ContextMenuStrips
ms.assetid: 3391c4c2-0c9e-4aa4-9492-13ff7644bdf2
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de047adfee28a6c92819695678201558959b1639
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-contextmenustrip-check-margins-and-image-margins"></a><span data-ttu-id="93f62-102">Nasıl yapılır: ContextMenuStrip Denetim Kenar Boşluklarını ve Görüntü Kenar Boşluklarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="93f62-102">How to: Configure ContextMenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="93f62-103">Özelleştirebileceğiniz bir <xref:System.Windows.Forms.ContextMenuStrip> ayarlayarak <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> ve <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> çeşitli bileşimlerini özellikleri.</span><span class="sxs-lookup"><span data-stu-id="93f62-103">You can customize a <xref:System.Windows.Forms.ContextMenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f62-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="93f62-104">Example</span></span>  
 <span data-ttu-id="93f62-105">Aşağıdaki kod örneğinde ayarlamak ve özelleştirmek gösterilmiştir <xref:System.Windows.Forms.ContextMenuStrip> denetleyin ve görüntü kenar boşluklarını.</span><span class="sxs-lookup"><span data-stu-id="93f62-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check and image margins.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93f62-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="93f62-106">Compiling the Code</span></span>  
 <span data-ttu-id="93f62-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="93f62-107">This example requires:</span></span>  
  
-   <span data-ttu-id="93f62-108">System.Design, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="93f62-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="93f62-109">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="93f62-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="93f62-110">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93f62-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="93f62-111">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="93f62-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f62-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93f62-112">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="93f62-113">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="93f62-113">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="93f62-114">Nasıl yapılır: ContextMenuStrip Denetimlerinde Denetim Kenar Boşluklarını ve Görüntü Kenar Boşluklarını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="93f62-114">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)

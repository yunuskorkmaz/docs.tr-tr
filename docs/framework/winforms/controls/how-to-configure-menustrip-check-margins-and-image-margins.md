---
title: 'Nasıl yapılır: MenuStrip Denetim Kenar Boşluklarını ve Görüntü Kenar Boşluklarını Yapılandırma'
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
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3ee49ec226c99a28322822983fa086954f0ef3e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="34aa8-102">Nasıl yapılır: MenuStrip Denetim Kenar Boşluklarını ve Görüntü Kenar Boşluklarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34aa8-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="34aa8-103">Özelleştirebileceğiniz bir <xref:System.Windows.Forms.MenuStrip> ayarlayarak <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> ve <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> çeşitli bileşimlerini özellikleri.</span><span class="sxs-lookup"><span data-stu-id="34aa8-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34aa8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="34aa8-104">Example</span></span>  
 <span data-ttu-id="34aa8-105">Aşağıdaki kod örneğinde ayarlamak ve özelleştirmek gösterilmiştir <xref:System.Windows.Forms.ContextMenuStrip> kenar boşluklarını ve görüntü kenar boşluklarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="34aa8-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="34aa8-106">Yordam aynıdır bir <xref:System.Windows.Forms.ContextMenuStrip> veya <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="34aa8-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34aa8-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="34aa8-107">Compiling the Code</span></span>  
 <span data-ttu-id="34aa8-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="34aa8-108">This example requires:</span></span>  
  
-   <span data-ttu-id="34aa8-109">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="34aa8-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="34aa8-110">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="34aa8-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="34aa8-111">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34aa8-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="34aa8-112">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="34aa8-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34aa8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34aa8-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="34aa8-114">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="34aa8-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="34aa8-115">Nasıl yapılır: ContextMenuStrip Denetimlerinde Denetim Kenar Boşluklarını ve Görüntü Kenar Boşluklarını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="34aa8-115">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)

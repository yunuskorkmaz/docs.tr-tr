---
title: "Nasıl yapılır: ToolStripContentPanel'ine Denetim Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e513505dbc25f2eebe8c3ba8353622b3c284297
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a><span data-ttu-id="58fa6-102">Nasıl yapılır: ToolStripContentPanel'ine Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="58fa6-102">How to: Add a Control to a ToolStripContentPanel</span></span>
<span data-ttu-id="58fa6-103">Bir veya daha fazla denetimlerine programlı olarak ekleyebileceğiniz bir <xref:System.Windows.Forms.ToolStripContentPanel>.</span><span class="sxs-lookup"><span data-stu-id="58fa6-103">You can programmatically add one or more controls to a <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58fa6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="58fa6-104">Example</span></span>  
 <span data-ttu-id="58fa6-105">Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir bir <xref:System.Windows.Forms.RichTextBox> için bir <xref:System.Windows.Forms.ToolStripContentPanel>.</span><span class="sxs-lookup"><span data-stu-id="58fa6-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.RichTextBox> to a <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58fa6-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="58fa6-106">Compiling the Code</span></span>  
 <span data-ttu-id="58fa6-107">Bu kod örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="58fa6-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="58fa6-108">Sistem, System.Data ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="58fa6-108">References to the System, System.Data and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="58fa6-109">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="58fa6-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="58fa6-110">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="58fa6-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="58fa6-111">Ayrıca bkz. [nasıl yapılır: derleme ve Visual Studio kullanarak tam Windows Forms kod örneği çalıştırma](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) veya [ToolStripContainer görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="58fa6-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fa6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58fa6-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="58fa6-113">ToolStripContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="58fa6-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="58fa6-114">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="58fa6-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

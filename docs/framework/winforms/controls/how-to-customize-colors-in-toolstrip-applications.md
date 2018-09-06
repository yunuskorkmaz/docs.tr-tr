---
title: 'Nasıl yapılır: ToolStrip Uygulamalarında Renkleri Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
ms.openlocfilehash: 9a3f712a4d729452ac0d2d4755a5fba59ca102ed
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732721"
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="7f6a9-102">Nasıl yapılır: ToolStrip Uygulamalarında Renkleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7f6a9-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="7f6a9-103">Görünümünü özelleştirebilirsiniz, <xref:System.Windows.Forms.ToolStrip> kullanarak <xref:System.Windows.Forms.ToolStripProfessionalRenderer> özelleştirilmiş renklerini kullanmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7f6a9-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f6a9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f6a9-104">Example</span></span>  
 <span data-ttu-id="7f6a9-105">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> çalışma zamanında özel renkler tanımlama.</span><span class="sxs-lookup"><span data-stu-id="7f6a9-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f6a9-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7f6a9-106">Compiling the Code</span></span>  
 <span data-ttu-id="7f6a9-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7f6a9-107">This example requires:</span></span>  
  
-   <span data-ttu-id="7f6a9-108">System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="7f6a9-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7f6a9-109">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7f6a9-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7f6a9-110">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f6a9-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="7f6a9-111">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7f6a9-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f6a9-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f6a9-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>

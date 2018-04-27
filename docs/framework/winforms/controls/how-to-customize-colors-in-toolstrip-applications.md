---
title: 'Nasıl yapılır: ToolStrip Uygulamalarında Renkleri Özelleştirme'
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
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b8806878c2bac338b4bce9cbee311edd7bf7978
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="5226d-102">Nasıl yapılır: ToolStrip Uygulamalarında Renkleri Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5226d-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="5226d-103">Görünümünü özelleştirebilirsiniz, <xref:System.Windows.Forms.ToolStrip> kullanarak <xref:System.Windows.Forms.ToolStripProfessionalRenderer> sınıfı özelleştirilmiş renkleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="5226d-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5226d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5226d-104">Example</span></span>  
 <span data-ttu-id="5226d-105">Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> çalışma zamanında özel renkler tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="5226d-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5226d-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5226d-106">Compiling the Code</span></span>  
 <span data-ttu-id="5226d-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5226d-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5226d-108">System.Design, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="5226d-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5226d-109">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5226d-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5226d-110">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="5226d-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5226d-111">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5226d-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5226d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5226d-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>

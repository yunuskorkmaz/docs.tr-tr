---
title: 'Nasıl yapılır: Çalışma Zamanında ToolStrip Oluşturucusunu Ayarlama'
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
- toolbars [Windows Forms]
- ToolStripManager class [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 525e2347-0804-49aa-b9a3-9b2cabbf1c35
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61bd3b85c46f6cc1cf0b4d898bfd89c509ce2b72
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a><span data-ttu-id="e90bc-102">Nasıl yapılır: Çalışma Zamanında ToolStrip Oluşturucusunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e90bc-102">How to: Set the ToolStrip Renderer at Run Time</span></span>
<span data-ttu-id="e90bc-103">Görünümünü özelleştirebilirsiniz, <xref:System.Windows.Forms.ToolStrip> özel oluşturarak denetim `ProfessionalColorTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e90bc-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> control by creating a custom `ProfessionalColorTable` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e90bc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e90bc-104">Example</span></span>  
 <span data-ttu-id="e90bc-105">Aşağıdaki kod örneğinde nasıl özel bir oluşturulduğunu gösteren `ProfessionalColorTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e90bc-105">The following code example demonstrates how to create a custom `ProfessionalColorTable` class.</span></span> <span data-ttu-id="e90bc-106">Bu sınıf için gradyan tanımlayan bir <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ToolStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="e90bc-106">This class defines gradients for a <xref:System.Windows.Forms.MenuStrip> and a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
 <span data-ttu-id="e90bc-107">Bu kod örneği kullanmak için derleme ve uygulamayı çalıştırın ve ardından **değişiklik renkleri** özel tanımlı gradyan uygulamak için `ProfessionalColorTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e90bc-107">To use this code example, compile and run the application, and then click **Change Colors** to apply the gradients defined in the custom `ProfessionalColorTable` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a><span data-ttu-id="e90bc-108">Özel ProfessionalColorTable sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="e90bc-108">Defining a Custom ProfessionalColorTable class</span></span>  
 <span data-ttu-id="e90bc-109">Özel gradyan tanımlanan `CustomProfessionalColors` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e90bc-109">The custom gradients are defined in the `CustomProfessionalColors` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a><span data-ttu-id="e90bc-110">Özel oluşturucu atama</span><span class="sxs-lookup"><span data-stu-id="e90bc-110">Assigning a Custom Renderer</span></span>  
 <span data-ttu-id="e90bc-111">Yeni bir `ToolStripProfessionalRenderer` ile bir `CustomProfessionalColors` sınıfı ve atayın <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e90bc-111">Create a new `ToolStripProfessionalRenderer` with a `CustomProfessionalColors` class, and assign it to the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e90bc-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e90bc-112">Compiling the Code</span></span>  
 <span data-ttu-id="e90bc-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e90bc-113">This example requires:</span></span>  
  
-   <span data-ttu-id="e90bc-114">System.Design, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e90bc-114">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e90bc-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e90bc-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e90bc-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e90bc-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e90bc-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e90bc-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90bc-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e90bc-118">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [<span data-ttu-id="e90bc-119">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="e90bc-119">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

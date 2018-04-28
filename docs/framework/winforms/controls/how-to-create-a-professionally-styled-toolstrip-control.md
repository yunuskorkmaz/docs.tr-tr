---
title: 'Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma'
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8b2d67f38f9533e60575b45df011f50e7ec091d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="f1350-102">Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1350-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="f1350-103">Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> türetilmiş kendi sınıfı yazarak profesyonel görünüm ve davranış (Görünüm) denetimleri <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.</span><span class="sxs-lookup"><span data-stu-id="f1350-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="f1350-104">Visual Studio'da bu özellik için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="f1350-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="f1350-105">Bkz: [izlenecek yol: profesyonel stilde ToolStrip denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="f1350-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1350-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1350-106">Example</span></span>  
 <span data-ttu-id="f1350-107">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStrip> taklit eden bir bileşik denetim oluşturmak için denetimleri **Gezinti Bölmesi** Microsoft Outlook® tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="f1350-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1350-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f1350-108">Compiling the Code</span></span>  
 <span data-ttu-id="f1350-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f1350-109">This example requires:</span></span>  
  
-   <span data-ttu-id="f1350-110">System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f1350-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f1350-111">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f1350-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f1350-112">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1350-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f1350-113">Ayrıca bkz. [izlenecek yol: bir profesyonel stilde ToolStrip denetimi oluşturma](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f1350-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1350-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1350-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="f1350-115">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="f1350-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="f1350-116">Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="f1350-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)

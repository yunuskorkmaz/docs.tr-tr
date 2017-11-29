---
title: "Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0199bad54d7b4ed4f1ed63b22914f8f99bbf6e85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="4c45d-102">Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c45d-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="4c45d-103">Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> türetilmiş kendi sınıfı yazarak profesyonel görünüm ve davranış (Görünüm) denetimleri <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.</span><span class="sxs-lookup"><span data-stu-id="4c45d-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="4c45d-104">Bu özellik için kapsamlı destek [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c45d-104">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="4c45d-105">Bkz: [izlenecek yol: profesyonel stilde ToolStrip denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="4c45d-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c45d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c45d-106">Example</span></span>  
 <span data-ttu-id="4c45d-107">Aşağıdaki kod örneğinde nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ToolStrip> taklit eden bir bileşik denetim oluşturmak için denetimleri **Gezinti Bölmesi** Microsoft Outlook® tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="4c45d-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c45d-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4c45d-108">Compiling the Code</span></span>  
 <span data-ttu-id="4c45d-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4c45d-109">This example requires:</span></span>  
  
-   <span data-ttu-id="4c45d-110">System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="4c45d-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4c45d-111">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4c45d-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4c45d-112">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="4c45d-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="4c45d-113">Ayrıca bkz. [izlenecek yol: bir profesyonel stilde ToolStrip denetimi oluşturma](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="4c45d-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c45d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c45d-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="4c45d-115">ToolStrip denetimi</span><span class="sxs-lookup"><span data-stu-id="4c45d-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="4c45d-116">Nasıl yapılır: bir forma standart menü öğeleri sağlayın</span><span class="sxs-lookup"><span data-stu-id="4c45d-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)

---
title: 'Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6da6e113867efed79dfcd02f3b89ee1f9ae13c4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746673"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="73a3e-102">Nasıl yapılır: Profesyonel Stilde ToolStrip Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73a3e-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="73a3e-103">Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> kendi sınıfından türetilen yazarak bir profesyonel görünümünü ve davranışını (Görünüm) denetimleri <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.</span><span class="sxs-lookup"><span data-stu-id="73a3e-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="73a3e-104">Visual Studio'da bu özellik için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="73a3e-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="73a3e-105">Bkz: [izlenecek yol: Profesyonel stilde ToolStrip denetimi oluşturma](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="73a3e-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73a3e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="73a3e-106">Example</span></span>  
 <span data-ttu-id="73a3e-107">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStrip> taklit eden bir bileşik denetim oluşturmak için denetimleri **Gezinti bölmesinde** Microsoft Outlook® tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="73a3e-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73a3e-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="73a3e-108">Compiling the Code</span></span>  
 <span data-ttu-id="73a3e-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="73a3e-109">This example requires:</span></span>  
  
- <span data-ttu-id="73a3e-110">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="73a3e-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="73a3e-111">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="73a3e-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="73a3e-112">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73a3e-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="73a3e-113">Ayrıca bkz: [izlenecek yol: Profesyonel stilde ToolStrip denetimi oluşturma](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="73a3e-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a3e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73a3e-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="73a3e-115">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="73a3e-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="73a3e-116">Nasıl yapılır: Bir forma standart menü öğeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="73a3e-116">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)

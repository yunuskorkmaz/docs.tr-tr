---
title: 'Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: b118392d089bf28edee1496e0e11ed24d263202a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533338"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="07ba0-102">Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="07ba0-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="07ba0-103">Formlarınızı ile için standart menü sağlayabilirsiniz <xref:System.Windows.Forms.MenuStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="07ba0-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="07ba0-104">Visual Studio'da bu özellik için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="07ba0-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="07ba0-105">Ayrıca bkz. [izlenecek yol: bir forma standart menü öğeleri sağlama](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="07ba0-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07ba0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="07ba0-106">Example</span></span>  
 <span data-ttu-id="07ba0-107">Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.MenuStrip> bir forma standart menü ile oluşturmak için denetim.</span><span class="sxs-lookup"><span data-stu-id="07ba0-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="07ba0-108">Menü öğesi seçimlerini görüntülenir bir <xref:System.Windows.Forms.StatusStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="07ba0-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07ba0-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="07ba0-109">Compiling the Code</span></span>  
 <span data-ttu-id="07ba0-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="07ba0-110">This example requires:</span></span>  
  
-   <span data-ttu-id="07ba0-111">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="07ba0-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="07ba0-112">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="07ba0-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="07ba0-113">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07ba0-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="07ba0-114">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="07ba0-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ba0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07ba0-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="07ba0-116">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="07ba0-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)

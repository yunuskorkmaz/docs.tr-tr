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
ms.openlocfilehash: bf43d27ed728d11b5cde5b9250cfc4614077ed94
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395715"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="e4836-102">Nasıl yapılır: Bir Forma Standart Menü Öğeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="e4836-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="e4836-103">Formlarınızla için standart bir menü sağlayabilir <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4836-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="e4836-104">Visual Studio'da bu özellik için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4836-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="e4836-105">Ayrıca bkz: [izlenecek yol: bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="e4836-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4836-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4836-106">Example</span></span>  
 <span data-ttu-id="e4836-107">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.MenuStrip> denetimi ile standart bir menü bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e4836-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="e4836-108">Menü öğesi seçimlerini görüntülenir bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4836-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4836-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e4836-109">Compiling the Code</span></span>  
 <span data-ttu-id="e4836-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e4836-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e4836-111">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e4836-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e4836-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e4836-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e4836-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4836-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e4836-114">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e4836-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4836-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4836-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="e4836-116">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="e4836-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)

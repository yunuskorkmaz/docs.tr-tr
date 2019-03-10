---
title: 'Nasıl yapılır: Bir forma standart menü öğeleri sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: 3cf53a6934190cd0e7cd7e18bc57fb5fbfb57a86
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713871"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="076a0-102">Nasıl yapılır: Bir forma standart menü öğeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="076a0-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="076a0-103">Formlarınızla için standart bir menü sağlayabilir <xref:System.Windows.Forms.MenuStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="076a0-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="076a0-104">Visual Studio'da bu özellik için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="076a0-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="076a0-105">Ayrıca bkz: [izlenecek yol: Bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="076a0-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="076a0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="076a0-106">Example</span></span>  
 <span data-ttu-id="076a0-107">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.MenuStrip> denetimi ile standart bir menü bir form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="076a0-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="076a0-108">Menü öğesi seçimlerini görüntülenir bir <xref:System.Windows.Forms.StatusStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="076a0-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="076a0-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="076a0-109">Compiling the Code</span></span>  
 <span data-ttu-id="076a0-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="076a0-110">This example requires:</span></span>  
  
-   <span data-ttu-id="076a0-111">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="076a0-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="076a0-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="076a0-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="076a0-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="076a0-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="076a0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="076a0-114">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="076a0-115">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="076a0-115">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)

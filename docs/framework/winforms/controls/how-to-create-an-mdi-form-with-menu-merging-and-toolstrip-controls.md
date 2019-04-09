---
title: 'Nasıl yapılır: Menü Birleştirme ve ToolStrip Denetimleri içeren MDI Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: a67298614b1985152c42577de14d2c5d295f672f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157537"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="2f774-102">Nasıl yapılır: Menü Birleştirme ve ToolStrip Denetimleri içeren MDI Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f774-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="2f774-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı birden çok belge arabirimi (MDI) uygulamaları destekler ve <xref:System.Windows.Forms.MenuStrip> denetimi, menü birleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="2f774-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="2f774-104">MDI formları aynı zamanda <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="2f774-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="2f774-105">Visual Studio'da bu özellik için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="2f774-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="2f774-106">Ayrıca bkz: [izlenecek yol: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2f774-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f774-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f774-107">Example</span></span>  
 <span data-ttu-id="2f774-108">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStripPanel> denetimleriyle MDI formu.</span><span class="sxs-lookup"><span data-stu-id="2f774-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="2f774-109">Formu ile alt menülerini birleştirme menüsünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="2f774-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f774-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2f774-110">Compiling the Code</span></span>  
 <span data-ttu-id="2f774-111">Bu kod örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2f774-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="2f774-112">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="2f774-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2f774-113">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2f774-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2f774-114">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f774-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f774-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f774-115">See also</span></span>

- [<span data-ttu-id="2f774-116">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="2f774-116">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

---
title: 'Nasıl yapılır: Çalışma Zamanında ToolStrip Oluşturucusunu Ayarlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: f0e8668ef46de8cc073663786bcd43b740a1b2f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138592"
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a><span data-ttu-id="73db0-102">Nasıl yapılır: Çalışma Zamanında ToolStrip Oluşturucusunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="73db0-102">How to: Set the ToolStrip Renderer at Run Time</span></span>
<span data-ttu-id="73db0-103">Görünümünü özelleştirebilirsiniz, <xref:System.Windows.Forms.ToolStrip> oluşturarak bir özel denetim `ProfessionalColorTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73db0-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> control by creating a custom `ProfessionalColorTable` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73db0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="73db0-104">Example</span></span>  
 <span data-ttu-id="73db0-105">Aşağıdaki kod örneği bir özel oluşturma işlemini gösterir `ProfessionalColorTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73db0-105">The following code example demonstrates how to create a custom `ProfessionalColorTable` class.</span></span> <span data-ttu-id="73db0-106">Bu sınıf için gradyan tanımlayan bir <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="73db0-106">This class defines gradients for a <xref:System.Windows.Forms.MenuStrip> and a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
 <span data-ttu-id="73db0-107">Bu kod örneği kullanmak için derlemek ve uygulamayı çalıştırın ve ardından **değişiklik renkleri** özel tanımlı gradyanlar uygulanacak `ProfessionalColorTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73db0-107">To use this code example, compile and run the application, and then click **Change Colors** to apply the gradients defined in the custom `ProfessionalColorTable` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a><span data-ttu-id="73db0-108">Özel ProfessionalColorTable sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="73db0-108">Defining a Custom ProfessionalColorTable class</span></span>  
 <span data-ttu-id="73db0-109">Özel gradyanlar içinde tanımlanan `CustomProfessionalColors` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73db0-109">The custom gradients are defined in the `CustomProfessionalColors` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a><span data-ttu-id="73db0-110">Özel oluşturucu atama</span><span class="sxs-lookup"><span data-stu-id="73db0-110">Assigning a Custom Renderer</span></span>  
 <span data-ttu-id="73db0-111">Yeni bir `ToolStripProfessionalRenderer` ile bir `CustomProfessionalColors` sınıfı ve atamanıza <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="73db0-111">Create a new `ToolStripProfessionalRenderer` with a `CustomProfessionalColors` class, and assign it to the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73db0-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="73db0-112">Compiling the Code</span></span>  
 <span data-ttu-id="73db0-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="73db0-113">This example requires:</span></span>  
  
-   <span data-ttu-id="73db0-114">System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="73db0-114">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="73db0-115">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="73db0-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="73db0-116">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73db0-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73db0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73db0-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="73db0-118">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="73db0-118">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

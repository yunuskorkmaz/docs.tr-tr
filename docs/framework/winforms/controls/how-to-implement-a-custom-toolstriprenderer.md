---
title: 'Nasıl yapılır: Özel ToolStripRenderer Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: 91c04ba41a02c7c620c2f6c621505a19e0302c19
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398121"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="864dd-102">Nasıl yapılır: Özel ToolStripRenderer Uygulama</span><span class="sxs-lookup"><span data-stu-id="864dd-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="864dd-103">Görünümünü özelleştirebileceğiniz bir <xref:System.Windows.Forms.ToolStrip> türetildiği bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="864dd-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="864dd-104">Bu size sağlanan görünümü farklı bir görünüm oluşturmak için esneklik <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve <xref:System.Windows.Forms.ToolStripSystemRenderer> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="864dd-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="864dd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="864dd-105">Example</span></span>  
 <span data-ttu-id="864dd-106">Aşağıdaki kod örneği, özel bir uygulama gösterilmektedir <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="864dd-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="864dd-107">Bu örnekte, `GridStrip` kutucukları bir görüntü oluşturmak için bir tablo düzeni taşımak kullanıcı izin veren bir kayan kutucuk Bulmacanın denetimi uygular.</span><span class="sxs-lookup"><span data-stu-id="864dd-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="864dd-108">Özel bir <xref:System.Windows.Forms.ToolStrip> denetim düzenler, <xref:System.Windows.Forms.ToolStripButton> bir kılavuz düzeni denetimleri.</span><span class="sxs-lookup"><span data-stu-id="864dd-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="864dd-109">Düzen, bir Sürükle ve bırak işlemi kullanarak bitişik bir kutucuk kullanıcı kaydırabilirsiniz boş bir hücreye içerir.</span><span class="sxs-lookup"><span data-stu-id="864dd-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="864dd-110">Kullanıcı taşıyabilirsiniz kutucukları vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="864dd-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="864dd-111">`GridStripRenderer` Sınıfı özelleştirir üç yönlerini `GridStrip` denetimin görünümü:</span><span class="sxs-lookup"><span data-stu-id="864dd-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="864dd-112">`GridStrip` Kenarlık</span><span class="sxs-lookup"><span data-stu-id="864dd-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="864dd-113"><xref:System.Windows.Forms.ToolStripButton> Kenarlık</span><span class="sxs-lookup"><span data-stu-id="864dd-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="864dd-114"><xref:System.Windows.Forms.ToolStripButton> Görüntü</span><span class="sxs-lookup"><span data-stu-id="864dd-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="864dd-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="864dd-115">Compiling the Code</span></span>  
 <span data-ttu-id="864dd-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="864dd-116">This example requires:</span></span>  
  
-   <span data-ttu-id="864dd-117">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="864dd-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="864dd-118">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="864dd-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="864dd-119">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="864dd-119">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="864dd-120">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="864dd-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864dd-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="864dd-121">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="864dd-122">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="864dd-122">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

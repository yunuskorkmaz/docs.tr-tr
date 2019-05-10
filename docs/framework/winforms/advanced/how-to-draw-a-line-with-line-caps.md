---
title: 'Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: 682474120cbeeeb4cb83b69188a5a125228279d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631642"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="a4ec6-102">Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="a4ec6-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="a4ec6-103">Satır caps adlı birkaç şekil birini başlangıç veya satırın çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="a4ec6-104">hepsini, kare, elmas ve ok ucu gibi birkaç satır caps destekler.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-104">supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4ec6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4ec6-105">Example</span></span>  
 <span data-ttu-id="a4ec6-106">İçin bir satır (Başlangıç cap), bir satır (bitiş ucu) veya tireler (dash cap) kesikli satır başı satır caps belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="a4ec6-107">Aşağıdaki örnek, bir ucunda bir ok ucu ve diğer uçtaki yuvarlak bir uç bir çizgi çizer.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="a4ec6-108">Çizim, sonuçta elde edilen satırı gösterir:</span><span class="sxs-lookup"><span data-stu-id="a4ec6-108">The illustration shows the resulting line:</span></span>  
  
 ![Yuvarlak bir uç bir çizgiyle gösterildiği çizim.](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4ec6-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a4ec6-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="a4ec6-111">Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="a4ec6-112">Örnek kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> geçirme olay işleyicisi `e` olarak <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ec6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4ec6-113">See also</span></span>

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [<span data-ttu-id="a4ec6-114">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="a4ec6-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="a4ec6-115">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="a4ec6-115">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)

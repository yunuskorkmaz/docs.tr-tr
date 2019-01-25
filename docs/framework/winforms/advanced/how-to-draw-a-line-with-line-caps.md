---
title: 'Nasıl yapılır: Çizgi uçlarıyla çizgi çizme'
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
ms.openlocfilehash: a0d4d92d7201c4ac09eadd11d8f2e38a3c80c287
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713148"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="66c63-102">Nasıl yapılır: Çizgi uçlarıyla çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="66c63-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="66c63-103">Satır caps adlı birkaç şekil birini başlangıç veya satırın çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66c63-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="66c63-104">hepsini, kare, elmas ve ok ucu gibi birkaç satır caps destekler.</span><span class="sxs-lookup"><span data-stu-id="66c63-104">supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66c63-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="66c63-105">Example</span></span>  
 <span data-ttu-id="66c63-106">İçin bir satır (Başlangıç cap), bir satır (bitiş ucu) veya tireler (dash cap) kesikli satır başı satır caps belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66c63-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="66c63-107">Aşağıdaki örnek, bir ucunda bir ok ucu ve diğer uçtaki yuvarlak bir uç bir çizgi çizer.</span><span class="sxs-lookup"><span data-stu-id="66c63-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="66c63-108">Çizim, sonuçta elde edilen satırı gösterir:</span><span class="sxs-lookup"><span data-stu-id="66c63-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="66c63-109">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="66c63-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66c63-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="66c63-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="66c63-111">Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="66c63-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="66c63-112">Örnek kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> geçirme olay işleyicisi `e` olarak <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="66c63-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c63-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66c63-113">See also</span></span>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [<span data-ttu-id="66c63-114">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="66c63-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="66c63-115">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="66c63-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)

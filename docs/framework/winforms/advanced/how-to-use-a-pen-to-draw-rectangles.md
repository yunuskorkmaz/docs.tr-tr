---
title: "Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="98b1f-102">Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="98b1f-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="98b1f-103">Dikdörtgen çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="98b1f-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="98b1f-104"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi satırının renk ve genişlik gibi özellikleri saklar.</span><span class="sxs-lookup"><span data-stu-id="98b1f-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98b1f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="98b1f-105">Example</span></span>  
 <span data-ttu-id="98b1f-106">Aşağıdaki örnek, sol üst köşede bir dikdörtgen çizer (10, 10).</span><span class="sxs-lookup"><span data-stu-id="98b1f-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="98b1f-107">Dikdörtgen 100 genişliği ve yüksekliği 50 sahiptir.</span><span class="sxs-lookup"><span data-stu-id="98b1f-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="98b1f-108">İkinci bağımsız değişkeni geçirilen <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu kalem genişliği 5 pikselden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="98b1f-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="98b1f-109">Dikdörtgen çizildiğinde kalem dikdörtgenin sınırında ortalanır.</span><span class="sxs-lookup"><span data-stu-id="98b1f-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="98b1f-110">Kalem genişliği 5'tir dikdörtgen yanlarından çizilmiş 5 piksel olduklarından, o 1 piksel genişliğinde, bu tür çizilir sınırın üzerinde kendi iç 2 piksel çizilir ve 2 piksel dışarıda çizilir.</span><span class="sxs-lookup"><span data-stu-id="98b1f-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="98b1f-111">Kalem hizalama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kalem genişliği ve hizalamasını](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="98b1f-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="98b1f-112">Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="98b1f-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="98b1f-113">Kalem genişliği bir piksel olsaydı burada dikdörtgen Çekildi noktalı çizgiler gösterir.</span><span class="sxs-lookup"><span data-stu-id="98b1f-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="98b1f-114">Kalın siyah çizgiler bu noktalı satırlarında ortalanır dikdörtgenin sol üst köşesindeki genişletilmiş görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="98b1f-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="98b1f-115">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="98b1f-115">![Pens](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98b1f-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="98b1f-116">Compiling the Code</span></span>  
 <span data-ttu-id="98b1f-117">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="98b1f-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b1f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98b1f-118">See Also</span></span>  
 [<span data-ttu-id="98b1f-119">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="98b1f-119">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)

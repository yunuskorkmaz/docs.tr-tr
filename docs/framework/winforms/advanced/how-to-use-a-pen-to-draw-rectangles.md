---
title: 'Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 0e51a1e3a2d14754147dbd36f170127a7e978acd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074618"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="1860f-102">Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="1860f-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="1860f-103">Dikdörtgen çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="1860f-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="1860f-104"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesne satır, renk ve genişlik gibi özellikleri depolar.</span><span class="sxs-lookup"><span data-stu-id="1860f-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1860f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1860f-105">Example</span></span>  
 <span data-ttu-id="1860f-106">Aşağıdaki örnek, sol üst köşesinde bir dikdörtgen çizer (10, 10).</span><span class="sxs-lookup"><span data-stu-id="1860f-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="1860f-107">Dikdörtgenin genişliği 100 ve 50 yüksekliğini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1860f-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="1860f-108">Geçirilen ikinci bağımsız değişken <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu kalem genişliği 5 pikselden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1860f-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="1860f-109">Dikdörtgen çizildiğinde kalem dikdörtgenin sınırında ortalanır.</span><span class="sxs-lookup"><span data-stu-id="1860f-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="1860f-110">Kalem genişliği 5 olduğundan, dikdörtgen tarafının çizilen 5 piksel olan geniş, bu tür, 1 piksel artımlı çizilir sınırında kendisi, 2 piksel iç çizilir. ve 2 piksel dışarıda çizilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1860f-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="1860f-111">Kalem hizalamayı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kalem genişliği ve hizalamasını ayarlama](how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="1860f-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="1860f-112">Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="1860f-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="1860f-113">Kalem genişliği bir piksel olsaydı burada dikdörtgen Çekildi noktalı satırları gösterir.</span><span class="sxs-lookup"><span data-stu-id="1860f-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="1860f-114">Kalın siyah satırları bu noktalı satırlarda ortalanır dikdörtgenin sol üst köşesinin genişletilmiş görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1860f-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 ![Siyah ve noktalı çizgiler ile çizilen dikdörtgen gösteren ekran görüntüsü.](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1860f-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1860f-116">Compiling the Code</span></span>  
 <span data-ttu-id="1860f-117">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1860f-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1860f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1860f-118">See also</span></span>

- [<span data-ttu-id="1860f-119">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="1860f-119">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)

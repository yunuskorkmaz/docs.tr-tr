---
title: 'Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 2441687cb36d0780b7fbc935c5cb0edc74bc6ba0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712181"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="82812-102">Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="82812-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="82812-103">Dikdörtgen çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="82812-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="82812-104"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesne satır, renk ve genişlik gibi özellikleri depolar.</span><span class="sxs-lookup"><span data-stu-id="82812-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82812-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="82812-105">Example</span></span>  
 <span data-ttu-id="82812-106">Aşağıdaki örnek, sol üst köşesinde bir dikdörtgen çizer (10, 10).</span><span class="sxs-lookup"><span data-stu-id="82812-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="82812-107">Dikdörtgenin genişliği 100 ve 50 yüksekliğini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82812-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="82812-108">Geçirilen ikinci bağımsız değişken <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu kalem genişliği 5 pikselden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="82812-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="82812-109">Dikdörtgen çizildiğinde kalem dikdörtgenin sınırında ortalanır.</span><span class="sxs-lookup"><span data-stu-id="82812-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="82812-110">Kalem genişliği 5 olduğundan, dikdörtgen tarafının çizilen 5 piksel olan geniş, bu tür, 1 piksel artımlı çizilir sınırında kendisi, 2 piksel iç çizilir. ve 2 piksel dışarıda çizilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82812-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="82812-111">Kalem hizalamayı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kalem genişliği ve hizalamasını ayarlama](how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="82812-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="82812-112">Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="82812-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="82812-113">Kalem genişliği bir piksel olsaydı burada dikdörtgen Çekildi noktalı satırları gösterir.</span><span class="sxs-lookup"><span data-stu-id="82812-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="82812-114">Kalın siyah satırları bu noktalı satırlarda ortalanır dikdörtgenin sol üst köşesinin genişletilmiş görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="82812-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="82812-115">![Kalemler](./media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="82812-115">![Pens](./media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82812-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="82812-116">Compiling the Code</span></span>  
 <span data-ttu-id="82812-117">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="82812-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82812-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82812-118">See also</span></span>
- [<span data-ttu-id="82812-119">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="82812-119">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)

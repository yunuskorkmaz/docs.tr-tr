---
title: 'Nasıl yapılır: Çizim, bir sıra B&#233;zier eğrileri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711808"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="a0332-102">Nasıl yapılır: Çizim, bir sıra B&#233;zier eğrileri</span><span class="sxs-lookup"><span data-stu-id="a0332-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="a0332-103">Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawBeziers%2A> yöntemi <xref:System.Drawing.Graphics> dizisini çizmek için sınıf Bézier eğrileri bağlı.</span><span class="sxs-lookup"><span data-stu-id="a0332-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0332-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0332-104">Example</span></span>  
 <span data-ttu-id="a0332-105">Aşağıdaki örnek iki bağlı Bézier eğrileri oluşan bir eğrisi çizer.</span><span class="sxs-lookup"><span data-stu-id="a0332-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="a0332-106">Uç nokta ilk Bézier eğri ikinci Bézier eğri başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="a0332-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="a0332-107">Bağlı eğrileri yedi noktaları ile birlikte aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0332-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="a0332-108">![Bezier Spline](./media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="a0332-108">![Bezier Spline](./media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0332-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a0332-109">Compiling the Code</span></span>  
 <span data-ttu-id="a0332-110">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a0332-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0332-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0332-111">See also</span></span>
- [<span data-ttu-id="a0332-112">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="a0332-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="a0332-113">GDI+'daki Bézier Eğrileri</span><span class="sxs-lookup"><span data-stu-id="a0332-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="a0332-114">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="a0332-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)

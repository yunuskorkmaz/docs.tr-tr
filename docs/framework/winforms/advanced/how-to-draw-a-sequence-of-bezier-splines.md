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
ms.openlocfilehash: 2b74b03137d5a450fb1e436a514877d1a17229ad
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654256"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="a2261-102">Nasıl yapılır: Çizim, bir sıra B&#233;zier eğrileri</span><span class="sxs-lookup"><span data-stu-id="a2261-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="a2261-103">Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawBeziers%2A> yöntemi <xref:System.Drawing.Graphics> dizisini çizmek için sınıf Bézier eğrileri bağlı.</span><span class="sxs-lookup"><span data-stu-id="a2261-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2261-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2261-104">Example</span></span>  
 <span data-ttu-id="a2261-105">Aşağıdaki örnek iki bağlı Bézier eğrileri oluşan bir eğrisi çizer.</span><span class="sxs-lookup"><span data-stu-id="a2261-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="a2261-106">Uç nokta ilk Bézier eğri ikinci Bézier eğri başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="a2261-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="a2261-107">Bağlı eğrileri yedi noktaları ile birlikte aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a2261-107">The following illustration shows the connected splines along with the seven points:</span></span>  
  
 ![Yedi noktalarının yanı sıra bağlı eğrileri gösteren grafik.](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2261-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a2261-109">Compiling the Code</span></span>  
 <span data-ttu-id="a2261-110">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a2261-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2261-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2261-111">See also</span></span>
- [<span data-ttu-id="a2261-112">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="a2261-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="a2261-113">GDI+'daki Bézier Eğrileri</span><span class="sxs-lookup"><span data-stu-id="a2261-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="a2261-114">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="a2261-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)

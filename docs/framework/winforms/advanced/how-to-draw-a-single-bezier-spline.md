---
title: 'Nasıl yapılır: Tek bir B çizmek&#233;zier eğri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 32fc09c7525b40daea8c8705c43100cea0c052bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676464"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="5efa6-102">Nasıl yapılır: Tek bir B çizmek&#233;zier eğri</span><span class="sxs-lookup"><span data-stu-id="5efa6-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="5efa6-103">Bézier eğri dört noktaları tarafından tanımlanır: bir başlangıç noktası, iki denetim noktalarını ve uç nokta.</span><span class="sxs-lookup"><span data-stu-id="5efa6-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5efa6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5efa6-104">Example</span></span>  
 <span data-ttu-id="5efa6-105">Aşağıdaki örnek, başlangıç noktası (10, 100) ve (200, 100) uç noktası olan bir Bézier eğrisi çizer.</span><span class="sxs-lookup"><span data-stu-id="5efa6-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="5efa6-106">Denetim olan (100, 10) ve (150, 150) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5efa6-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="5efa6-107">Sonuçta elde edilen Bézier eğri, başlangıç noktası, denetim noktalarını ve uç nokta ile birlikte aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5efa6-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="5efa6-108">Çizimde, dört noktası düz çizgiler ile bağlanarak oluşturulmuş bir Çokgen eğri'nın dışbükey Kabuk da gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5efa6-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="5efa6-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="5efa6-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5efa6-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5efa6-110">Compiling the Code</span></span>  
 <span data-ttu-id="5efa6-111">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5efa6-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5efa6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5efa6-112">See also</span></span>
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [<span data-ttu-id="5efa6-113">GDI+'daki Bézier Eğrileri</span><span class="sxs-lookup"><span data-stu-id="5efa6-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)
- [<span data-ttu-id="5efa6-114">Nasıl yapılır: Bir dizi Bézier eğrileri çizme</span><span class="sxs-lookup"><span data-stu-id="5efa6-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)

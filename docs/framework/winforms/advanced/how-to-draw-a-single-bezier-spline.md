---
title: 'Nasıl yapılır: tek bir B çizin&#233;zier eğri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 9e91b63275c37fc0cdde5721fddd114e1bf2264e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521342"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="5723b-102">Nasıl yapılır: tek bir B çizin&#233;zier eğri</span><span class="sxs-lookup"><span data-stu-id="5723b-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="5723b-103">Bir Bézier eğrisi dört noktaları tarafından tanımlanır: bir başlangıç noktası, iki denetim noktası ve bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="5723b-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5723b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5723b-104">Example</span></span>  
 <span data-ttu-id="5723b-105">Aşağıdaki örnek, başlangıç noktası (10, 100) ve (200, 100) uç noktası olan bir Bézier eğrisi çizer.</span><span class="sxs-lookup"><span data-stu-id="5723b-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="5723b-106">Denetim noktalarını olan (100, 10) ve (150 150).</span><span class="sxs-lookup"><span data-stu-id="5723b-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="5723b-107">Sonuçta elde edilen bir Bézier eğrisi başlangıç noktasını, denetim noktaları ve uç nokta ile birlikte aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5723b-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="5723b-108">Çizimde de düz satırıyla dört noktası bağlanarak biçimlendirilmiş bir Çokgen eğri 's dışbükey hull gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5723b-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="5723b-109">![Bezier eğrisi](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="5723b-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5723b-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5723b-110">Compiling the Code</span></span>  
 <span data-ttu-id="5723b-111">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5723b-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5723b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5723b-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [<span data-ttu-id="5723b-113">GDI+'daki Bézier Eğrileri</span><span class="sxs-lookup"><span data-stu-id="5723b-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="5723b-114">Nasıl yapılır: Bir Sıra Bézier Eğrisi Çizme</span><span class="sxs-lookup"><span data-stu-id="5723b-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)

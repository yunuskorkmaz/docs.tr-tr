---
title: 'Nasıl yapılır: Eğriler çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 0f5c7a8555130e884b641648d1ffc9865f44dc1e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464703"
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="77d46-102">Nasıl yapılır: Eğriler çizme</span><span class="sxs-lookup"><span data-stu-id="77d46-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="77d46-103">Kardinal eğri sorunsuz bir şekilde belirli bir nokta kümesi geçen bir eğri ' dir.</span><span class="sxs-lookup"><span data-stu-id="77d46-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="77d46-104">Kardinal eğri çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesnesi ve bir dizi noktası adresini geçirmek <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77d46-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="77d46-105">Zil şeklinde bir Kardinal eğri çizme</span><span class="sxs-lookup"><span data-stu-id="77d46-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="77d46-106">Aşağıdaki örnek zil şeklinde ve beş belirlenen noktalara geçirmeden bir Kardinal eğrisi çizer.</span><span class="sxs-lookup"><span data-stu-id="77d46-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="77d46-107">Eğriyi ve beş noktaları aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77d46-107">The following illustration shows the curve and five points.</span></span>  
  
     ![Zil şeklinde bir Kardinal eğri gösteren diyagram.](./media/how-to-draw-cardinal-splines/bell-shaped-cardinal-spline.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="77d46-109">Bir kapalı Kardinal eğri çizme</span><span class="sxs-lookup"><span data-stu-id="77d46-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="77d46-110">Kullanım <xref:System.Drawing.Graphics.DrawClosedCurve%2A> yöntemi <xref:System.Drawing.Graphics> bir kapalı Kardinal eğri çizmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="77d46-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="77d46-111">Kapalı Kardinal eğri, eğrinin dizideki son noktası ile devam eder ve dizideki ilk noktasıyla bağlanır.</span><span class="sxs-lookup"><span data-stu-id="77d46-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="77d46-112">Aşağıdaki örnek, altı belirlenen noktalara geçen bir kapalı Kardinal eğri çizer.</span><span class="sxs-lookup"><span data-stu-id="77d46-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="77d46-113">Kapalı eğri altı noktaları ile birlikte aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="77d46-113">The following illustration shows the closed spline along with the six points:</span></span>  
  
 ![Bir kapalı Kardinal eğri gösteren diyagram.](./media/how-to-draw-cardinal-splines/closed-cardinal-spine.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="77d46-115">Kardinal eğri bSon değiştirme</span><span class="sxs-lookup"><span data-stu-id="77d46-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="77d46-116">Kardinal eğri bends gerilimi değişkenine geçirerek değiştirecek <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77d46-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="77d46-117">Aşağıdaki örnek, aynı dizi noktaları aracılığıyla geçen üç ana Eğriler çizer.</span><span class="sxs-lookup"><span data-stu-id="77d46-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="77d46-118">Aşağıdaki çizim üç eğrileri gerilimi değerleriyle birlikte gösterir.</span><span class="sxs-lookup"><span data-stu-id="77d46-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="77d46-119">Gerilimi 0 olduğunda noktaları düz satırlarla bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="77d46-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 ![Üç ana Eğriler gösteren diyagram.](./media/how-to-draw-cardinal-splines/three-cardinal-splines.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77d46-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="77d46-121">Compiling the Code</span></span>  
 <span data-ttu-id="77d46-122">Önceki örneklerde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirdikleri <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="77d46-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d46-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77d46-123">See also</span></span>
- [<span data-ttu-id="77d46-124">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="77d46-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="77d46-125">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="77d46-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)

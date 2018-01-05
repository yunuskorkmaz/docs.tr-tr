---
title: "Nasıl yapılır: Ana Eğriler Çizme"
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
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64661bbdcb267e2f2ce33b8a8db2ab2aac9a86f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="99b0f-102">Nasıl yapılır: Ana Eğriler Çizme</span><span class="sxs-lookup"><span data-stu-id="99b0f-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="99b0f-103">Kardinal eğri sorunsuz verilen kümesini noktaları geçirir bir eğri ' dir.</span><span class="sxs-lookup"><span data-stu-id="99b0f-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="99b0f-104">Kardinal eğri çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne ve bir dizi noktalarına adresini geçirin <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99b0f-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="99b0f-105">Zil şeklinde Kardinal eğrisi çizme</span><span class="sxs-lookup"><span data-stu-id="99b0f-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="99b0f-106">Aşağıdaki örnek zil şeklinde ve beş belirlenen noktalara geçirmeden bir Kardinal eğri çizer.</span><span class="sxs-lookup"><span data-stu-id="99b0f-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="99b0f-107">Aşağıdaki çizimde eğri ve beş noktalarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99b0f-107">The following illustration shows the curve and five points.</span></span>  
  
     <span data-ttu-id="99b0f-108">![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span><span class="sxs-lookup"><span data-stu-id="99b0f-108">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="99b0f-109">Kapalı Kardinal eğri çizme</span><span class="sxs-lookup"><span data-stu-id="99b0f-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="99b0f-110">Kullanım <xref:System.Drawing.Graphics.DrawClosedCurve%2A> yöntemi <xref:System.Drawing.Graphics> kapalı Kardinal eğri çizmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="99b0f-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="99b0f-111">Kapalı Kardinal eğri eğri dizideki son noktası ile devam eder ve dizinin ilk noktasıyla bağlanır.</span><span class="sxs-lookup"><span data-stu-id="99b0f-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="99b0f-112">Aşağıdaki örnekte, altı belirlenen noktalara geçirir kapalı bir Kardinal eğri çizilmiştir.</span><span class="sxs-lookup"><span data-stu-id="99b0f-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="99b0f-113">Kapalı eğri altı noktaları ile birlikte aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="99b0f-113">The following illustration shows the closed spline along with the six points.</span></span>  
  
 <span data-ttu-id="99b0f-114">![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span><span class="sxs-lookup"><span data-stu-id="99b0f-114">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="99b0f-115">Kardinal eğri bSon değiştirme</span><span class="sxs-lookup"><span data-stu-id="99b0f-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="99b0f-116">Kardinal eğri bends gerilim bağımsız değişkeni geçirerek şeklini değiştirmenize <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99b0f-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="99b0f-117">Aşağıdaki örnekte noktaları aynı dizi ile geçmesi üç ana Eğriler çizilmiştir.</span><span class="sxs-lookup"><span data-stu-id="99b0f-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="99b0f-118">Aşağıdaki çizim üç eğrileri gerilim değerleriyle birlikte göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="99b0f-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="99b0f-119">Gerilim 0 olduğunda noktaları düz çizgilerle bağlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="99b0f-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 <span data-ttu-id="99b0f-120">![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span><span class="sxs-lookup"><span data-stu-id="99b0f-120">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99b0f-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="99b0f-121">Compiling the Code</span></span>  
 <span data-ttu-id="99b0f-122">Önceki örneklerde Windows Forms ile kullanılmak üzere tasarlanmıştır ve ihtiyaç <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="99b0f-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b0f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99b0f-123">See Also</span></span>  
 [<span data-ttu-id="99b0f-124">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="99b0f-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="99b0f-125">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="99b0f-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)

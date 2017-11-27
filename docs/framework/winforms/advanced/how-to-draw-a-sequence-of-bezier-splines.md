---
title: "Nasıl yapılır: çizim sırası B &#233; zier eğrileri"
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
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76a0ab96f40c1b8d9db6f61d19ece82066b63eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="fff54-102">Nasıl yapılır: çizim sırası B &#233; zier eğrileri</span><span class="sxs-lookup"><span data-stu-id="fff54-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="fff54-103">Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawBeziers%2A> yöntemi <xref:System.Drawing.Graphics> dizisini çizmek için sınıf Bézier eğrileri bağlı.</span><span class="sxs-lookup"><span data-stu-id="fff54-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fff54-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fff54-104">Example</span></span>  
 <span data-ttu-id="fff54-105">Aşağıdaki örnekte iki bağlı Bézier eğrileri oluşan bir eğri çizer.</span><span class="sxs-lookup"><span data-stu-id="fff54-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="fff54-106">İlk Bézier eğrisi uç noktası ikinci bir Bézier eğrisi başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="fff54-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="fff54-107">Aşağıdaki çizimde bağlı eğrileri yedi noktaları ile birlikte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="fff54-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="fff54-108">![Bezier eğrisi](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="fff54-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fff54-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fff54-109">Compiling the Code</span></span>  
 <span data-ttu-id="fff54-110">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="fff54-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff54-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fff54-111">See Also</span></span>  
 [<span data-ttu-id="fff54-112">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="fff54-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="fff54-113">GDI +'daki Bézier eğrileri</span><span class="sxs-lookup"><span data-stu-id="fff54-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="fff54-114">Eğriler oluşturma ve çizme</span><span class="sxs-lookup"><span data-stu-id="fff54-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)

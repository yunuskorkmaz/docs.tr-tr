---
title: 'Nasıl yapılır: Çizgi Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452954"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="ec54b-102">Nasıl yapılır: Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="ec54b-102">How to: Draw a Line</span></span>
<span data-ttu-id="ec54b-103">Bu örnek, <xref:System.Windows.Shapes.Line> öğesini kullanarak nasıl çizgi çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec54b-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="ec54b-104">Çizgi çizmek için bir <xref:System.Windows.Shapes.Line> öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec54b-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="ec54b-105">Başlangıç noktasını ayarlamak için <xref:System.Windows.Shapes.Line.X1%2A> ve <xref:System.Windows.Shapes.Line.Y1%2A> özelliklerini kullanın; ve <xref:System.Windows.Shapes.Line.X2%2A> ve <xref:System.Windows.Shapes.Line.Y2%2A> özelliklerini kullanarak bitiş noktasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec54b-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="ec54b-106">Son olarak, konturu olmayan bir çizgi görünmez olduğundan <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec54b-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="ec54b-107">Bir çizginin iç kısmı olmadığından, bir satır için <xref:System.Windows.Shapes.Shape.Fill%2A> öğesinin ayarlanması etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="ec54b-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="ec54b-108">Aşağıdaki örnek, <xref:System.Windows.Controls.Canvas> öğesinin içinde üç satır çizer.</span><span class="sxs-lookup"><span data-stu-id="ec54b-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec54b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec54b-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="ec54b-110">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="ec54b-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec54b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec54b-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="ec54b-112">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="ec54b-112">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

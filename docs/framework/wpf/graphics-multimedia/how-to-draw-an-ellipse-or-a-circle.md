---
title: 'Nasıl yapılır: Elips veya Daire Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452928"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="b15f2-102">Nasıl yapılır: Elips veya Daire Çizme</span><span class="sxs-lookup"><span data-stu-id="b15f2-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="b15f2-103">Bu örnek, <xref:System.Windows.Shapes.Ellipse> öğesi kullanılarak üç nokta ve dairelerin nasıl çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b15f2-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="b15f2-104">Elips çizmek için bir <xref:System.Windows.Shapes.Ellipse> öğesi oluşturun ve <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>belirtin.</span><span class="sxs-lookup"><span data-stu-id="b15f2-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="b15f2-105">Elipsin iç kısmını boyamak için kullanılan <xref:System.Windows.Media.Brush> belirtmek için <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b15f2-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="b15f2-106">Elipsin ana hattını boyamak için kullanılan <xref:System.Windows.Media.Brush> belirtmek için <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b15f2-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="b15f2-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliği, elips anahattının kalınlığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b15f2-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="b15f2-108">Bir daire çizmek için <xref:System.Windows.Shapes.Ellipse> öğenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> birbirlerine eşit hale getirin.</span><span class="sxs-lookup"><span data-stu-id="b15f2-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="b15f2-109">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>içinde dört <xref:System.Windows.Shapes.Ellipse> öğesi çizer.</span><span class="sxs-lookup"><span data-stu-id="b15f2-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b15f2-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b15f2-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="b15f2-111">Bu örnek, üç noktayı içermek için bir <xref:System.Windows.Controls.Canvas> kullansa da metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte elips öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b15f2-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="b15f2-112">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="b15f2-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15f2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b15f2-113">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="b15f2-114">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="b15f2-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

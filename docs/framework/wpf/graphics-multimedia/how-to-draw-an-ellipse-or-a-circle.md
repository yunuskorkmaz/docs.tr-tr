---
title: 'Nasıl yapılır: Elips veya Daire Çizme'
description: Windows Presentation Foundation (WPF) içinde, ana hat kalınlığı ve iç renk seçenekleriyle bir elips veya daire çizmeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853565"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="7393d-103">Nasıl yapılır: Elips veya Daire Çizme</span><span class="sxs-lookup"><span data-stu-id="7393d-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="7393d-104">Bu örnek, öğesini kullanarak elips ve dairelerin nasıl çizileceğini gösterir <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="7393d-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="7393d-105">Elips çizmek için bir <xref:System.Windows.Shapes.Ellipse> öğe oluşturun ve ve ' ı belirtin <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="7393d-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="7393d-106"><xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Media.Brush> Elipsin iç kısmını boyamak için kullanılan öğesini belirtmek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7393d-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="7393d-107"><xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Media.Brush> Elipsin anahattını boyamak için kullanılan öğesini belirtmek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7393d-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="7393d-108"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>Özelliği, elips anahattının kalınlığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7393d-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="7393d-109">Bir daire çizmek için <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> öğesi ve öğelerini birbirlerine eşit yapın.</span><span class="sxs-lookup"><span data-stu-id="7393d-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="7393d-110">Aşağıdaki örnek, içinde dört <xref:System.Windows.Shapes.Ellipse> öğe çizer <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="7393d-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7393d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7393d-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="7393d-112">Bu örnek, üç noktayı içermek için bir kullanıyor olsa da <xref:System.Windows.Controls.Canvas> , elips öğelerini (ve diğer tüm şekil öğelerini) <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> metin olmayan içeriği destekleyen herhangi bir ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7393d-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="7393d-113">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="7393d-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7393d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7393d-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="7393d-115">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="7393d-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

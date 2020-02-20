---
title: 'Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452967"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="850e8-102">Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="850e8-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="850e8-103">Bu örnek, <xref:System.Windows.Shapes.Polyline> öğesi kullanılarak bir dizi bağlantılı çizgi olan bir çoklu çizginin nasıl çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="850e8-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="850e8-104">Bir çoklu çizgi çizmek için bir <xref:System.Windows.Shapes.Polyline> öğesi oluşturun ve <xref:System.Windows.Shapes.Polyline.Points%2A> özelliğini kullanarak şekil köşelerine belirleyin.</span><span class="sxs-lookup"><span data-stu-id="850e8-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="850e8-105">Son olarak, çizgi ana hattını anlatmak için <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="850e8-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="850e8-106"><xref:System.Windows.Shapes.Polyline> öğesi kapalı bir şekil olmadığından, şekil ana hattını kasıtlı olarak kapatsanız bile <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="850e8-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="850e8-107"><xref:System.Windows.Shapes.Shape.Fill%2A>ile kapalı bir şekil oluşturmak için <xref:System.Windows.Shapes.Polygon> bir öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="850e8-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="850e8-108">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>içinde iki <xref:System.Windows.Shapes.Polyline> öğesi çizer.</span><span class="sxs-lookup"><span data-stu-id="850e8-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="850e8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="850e8-109">Example</span></span>  
 <span data-ttu-id="850e8-110">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktalara yönelik geçerli sözdizimi, virgülle ayrılmış x ve y koordinatı çiftleri için boşlukla ayrılmış bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="850e8-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="850e8-111">Bu örnek polylines 'ı içermek için bir <xref:System.Windows.Controls.Canvas> kullansa da, metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte çoklu çizgi öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="850e8-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="850e8-112">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="850e8-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850e8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="850e8-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="850e8-114">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="850e8-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="850e8-115">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="850e8-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)

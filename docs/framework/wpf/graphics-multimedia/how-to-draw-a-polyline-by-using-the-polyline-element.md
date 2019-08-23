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
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934956"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="c6dd4-102">Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="c6dd4-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="c6dd4-103">Bu örnek, <xref:System.Windows.Shapes.Polyline> öğesini kullanarak bir dizi bağlantılı çizgi olan bir çoklu çizginin nasıl çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="c6dd4-104">Bir çoklu çizgi çizmek için bir <xref:System.Windows.Shapes.Polyline> öğe oluşturun ve kendi <xref:System.Windows.Shapes.Polyline.Points%2A> özelliğini kullanarak şekil köşelerine belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="c6dd4-105">Son olarak, kontur <xref:System.Windows.Shapes.Shape.Stroke%2A> içermeyen <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> bir çizgi görünmez olduğundan, çoklu çizgi anahattını anlatmak için ve özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6dd4-106">Öğe kapalı bir şekil olmadığından <xref:System.Windows.Shapes.Shape.Fill%2A> , şekil ana hattını kasıtlı olarak kapatsanız bile özelliğin etkisi yoktur. <xref:System.Windows.Shapes.Polyline></span><span class="sxs-lookup"><span data-stu-id="c6dd4-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="c6dd4-107">İle <xref:System.Windows.Shapes.Shape.Fill%2A>kapalı bir şekil oluşturmak için, bir <xref:System.Windows.Shapes.Polygon> öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="c6dd4-108">Aşağıdaki örnek bir <xref:System.Windows.Controls.Canvas>içinde iki <xref:System.Windows.Shapes.Polyline> öğe çizer.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6dd4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6dd4-109">Example</span></span>  
 <span data-ttu-id="c6dd4-110">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], nokta için geçerli sözdizimi, virgülle ayrılmış x ve y koordinatı çiftleri için boşlukla ayrılmış bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="c6dd4-111">Bu örnek, polylines <xref:System.Windows.Controls.Canvas> 'ı içermek için bir kullanıyor olsa da, metin olmayan içeriği destekleyen herhangi bir veya herhangi <xref:System.Windows.Controls.Panel> bir veya <xref:System.Windows.Controls.Control> daha fazla öğe içeren çoklu çizgi öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="c6dd4-112">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="c6dd4-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6dd4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6dd4-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="c6dd4-114">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="c6dd4-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="c6dd4-115">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6dd4-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)

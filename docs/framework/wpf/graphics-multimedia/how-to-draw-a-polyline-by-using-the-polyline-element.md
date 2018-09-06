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
ms.openlocfilehash: d065d3cead1ed9746a9615ce2bb6d3ec4cbd614d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855436"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="b76fc-102">Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="b76fc-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="b76fc-103">Bu örnekte bir dizi bağlantılı çizgiler kullanmaktır çoklu çizgi çizme gösterilmektedir <xref:System.Windows.Shapes.Polyline> öğesi.</span><span class="sxs-lookup"><span data-stu-id="b76fc-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="b76fc-104">Çoklu çizgi çizme için oluşturma bir <xref:System.Windows.Shapes.Polyline> öğesi ve kullanımı, <xref:System.Windows.Shapes.Polyline.Points%2A> şeklin köşe belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="b76fc-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="b76fc-105">Son olarak, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliklerini çoklu çizgi açıklamak için bir çizgi görünmez olduğundan genel çizgileriyle belirtin.</span><span class="sxs-lookup"><span data-stu-id="b76fc-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b76fc-106">Çünkü <xref:System.Windows.Shapes.Polyline> öğesi kapalı bir şekil değil <xref:System.Windows.Shapes.Shape.Fill%2A> özelliği, şeklin dış hattının kapatsanız bile hiçbir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b76fc-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="b76fc-107">Kapalı bir şekil ile oluşturmak için bir <xref:System.Windows.Shapes.Shape.Fill%2A>, kullanan bir <xref:System.Windows.Shapes.Polygon> öğesi.</span><span class="sxs-lookup"><span data-stu-id="b76fc-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="b76fc-108">Aşağıdaki örnek iki çizer <xref:System.Windows.Shapes.Polyline> içinde öğeleri bir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="b76fc-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b76fc-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b76fc-109">Example</span></span>  
 <span data-ttu-id="b76fc-110">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktaları için geçerli sözdizimi virgülle ayrılmış x ve y-koordinatını çiftlerinin boşlukla ayrılmış bir listesini aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="b76fc-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="b76fc-111">Bu örnek kullansa da bir <xref:System.Windows.Controls.Canvas> kullansa içerecek şekilde çoklu çizgi öğelerini (ve diğer tüm şekil öğelerine) ile kullanabilirsiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> , metin olmayan içerikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b76fc-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="b76fc-112">Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="b76fc-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76fc-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b76fc-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="b76fc-114">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="b76fc-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="b76fc-115">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b76fc-115">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)

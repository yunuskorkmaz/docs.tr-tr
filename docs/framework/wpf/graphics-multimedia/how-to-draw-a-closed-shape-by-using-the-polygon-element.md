---
title: 'Nasıl yapılır: Çokgen Öğe Kullanarak Kapalı Şekil Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452980"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="1141b-102">Nasıl yapılır: Çokgen Öğe Kullanarak Kapalı Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="1141b-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="1141b-103">Bu örnek, <xref:System.Windows.Shapes.Polygon> öğesi kullanılarak nasıl kapalı bir şekil çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1141b-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="1141b-104">Kapalı bir şekil çizmek için bir <xref:System.Windows.Shapes.Polygon> öğesi oluşturun ve bir şeklin köşelerini belirtmek için <xref:System.Windows.Shapes.Polygon.Points%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1141b-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="1141b-105">İlk ve son noktaları bağlayan bir çizgi otomatik olarak çizilir.</span><span class="sxs-lookup"><span data-stu-id="1141b-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="1141b-106">Son olarak, bir <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>veya her ikisini de belirtin.</span><span class="sxs-lookup"><span data-stu-id="1141b-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1141b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1141b-107">Example</span></span>  
 <span data-ttu-id="1141b-108">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktalara yönelik geçerli sözdizimi, virgülle ayrılmış x ve y koordinatı çiftleri için boşlukla ayrılmış bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="1141b-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="1141b-109">Örnek, çokgenler içeren bir <xref:System.Windows.Controls.Canvas> kullansa da, metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte çokgen öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1141b-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="1141b-110">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="1141b-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

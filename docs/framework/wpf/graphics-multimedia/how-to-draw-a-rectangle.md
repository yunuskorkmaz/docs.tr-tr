---
title: 'Nasıl yapılır: Dikdörtgen Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452941"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="c5c3b-102">Nasıl yapılır: Dikdörtgen Çizme</span><span class="sxs-lookup"><span data-stu-id="c5c3b-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="c5c3b-103">Bu örnek, <xref:System.Windows.Shapes.Rectangle> öğesi kullanılarak nasıl dikdörtgen çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="c5c3b-104">Bir dikdörtgen çizmek için bir <xref:System.Windows.Shapes.Rectangle> öğesi oluşturun ve <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>belirtin.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="c5c3b-105">Dikdörtgenin içini boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="c5c3b-106">Dikdörtgene bir ana hat vermek için, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="c5c3b-107">Dikdörtgene yuvarlatılmış köşeler vermek için isteğe bağlı <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özelliklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="c5c3b-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri, dikdörtgenin köşelerini yuvarlamak için kullanılan elipsin x ekseni ve y ekseni yarıçapı türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="c5c3b-109">Aşağıdaki örnekte, iki <xref:System.Windows.Shapes.Rectangle> öğesi bir <xref:System.Windows.Controls.Canvas>çizilir.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="c5c3b-110">İlk dikdörtgenin iç <xref:System.Windows.Media.Brushes.Blue%2A> vardır.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="c5c3b-111">İkinci dikdörtgen <xref:System.Windows.Media.Brushes.Blue%2A> iç, <xref:System.Windows.Media.Brushes.Black%2A> ana hat ve yuvarlatılmış köşeler vardır.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c3b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5c3b-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="c5c3b-113">Bu örnek, dikdörtgenleri içermesi için bir <xref:System.Windows.Controls.Canvas> kullansa da metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte dikdörtgen öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="c5c3b-114">Aslında, dikdörtgenler <xref:System.Windows.Controls.Grid> panellerin bölümleri için arka plan sağlamak üzere özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="c5c3b-115">Bir örnek için bkz. [tabloya genel bakış](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c5c3b-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="c5c3b-116">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="c5c3b-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c3b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c3b-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="c5c3b-118">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="c5c3b-118">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="c5c3b-119">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5c3b-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="c5c3b-120">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5c3b-120">Table Overview</span></span>](../advanced/table-overview.md)

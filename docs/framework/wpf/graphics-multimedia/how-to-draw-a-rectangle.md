---
title: 'Nasıl yapılır: Dikdörtgen Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 261026b994b432565928b38ff1657115ff7cbe4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217360"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="ce1f0-102">Nasıl yapılır: Dikdörtgen Çizme</span><span class="sxs-lookup"><span data-stu-id="ce1f0-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="ce1f0-103">Bu örnek gösterir kullanarak bir dikdörtgen çizmek nasıl <xref:System.Windows.Shapes.Rectangle> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="ce1f0-104">Bir dikdörtgen çizmek için oluşturma bir <xref:System.Windows.Shapes.Rectangle> öğesi ve kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="ce1f0-105">Dikdörtgenin iç boyamak için ayarlanmış kendi <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="ce1f0-106">Anahat dikdörtgen vermek için kullanın, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="ce1f0-107">Yuvarlak köşeler dikdörtgene vermek için isteğe bağlı belirtin <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="ce1f0-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> Ve <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> dikdörtgenin köşelerini yuvarlatmak için kullanılacak olan elipsin yarıçaplarını x ve y ekseni özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="ce1f0-109">Aşağıdaki örnekte, iki <xref:System.Windows.Shapes.Rectangle> öğeleri çizilmiştir bir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ce1f0-110">İlk dikdörtgen sahip bir <xref:System.Windows.Media.Brushes.Blue%2A> iç.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="ce1f0-111">İkinci dikdörtgeni sahip bir <xref:System.Windows.Media.Brushes.Blue%2A> iç, bir <xref:System.Windows.Media.Brushes.Black%2A> yuvarlatılmış köşeler ve ana hat.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce1f0-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce1f0-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="ce1f0-113">Bu örnek kullansa da bir <xref:System.Windows.Controls.Canvas> dikdörtgenler içermek için dikdörtgen öğelerini (ve diğer tüm şekil öğelerine) ile kullanabilirsiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> , metin olmayan içerikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="ce1f0-114">Aslında, dikdörtgenler kısımları için arka plan sağlamak için özellikle yararlıdır <xref:System.Windows.Controls.Grid> panelleri.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="ce1f0-115">Bir örnek için bkz. [tabloya genel bakış](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce1f0-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="ce1f0-116">Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="ce1f0-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1f0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce1f0-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="ce1f0-118">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="ce1f0-118">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="ce1f0-119">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="ce1f0-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="ce1f0-120">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce1f0-120">Table Overview</span></span>](../advanced/table-overview.md)

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
ms.openlocfilehash: ddeada8619d1b6c8970f1efb7cca1bc98773d0c5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079119"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="5bf74-102">Nasıl yapılır: Elips veya Daire Çizme</span><span class="sxs-lookup"><span data-stu-id="5bf74-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="5bf74-103">Bu örnekte kullanarak elips ve daireler çizin gösterilmektedir <xref:System.Windows.Shapes.Ellipse> öğesi.</span><span class="sxs-lookup"><span data-stu-id="5bf74-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="5bf74-104">Elips çizin için oluşturma bir <xref:System.Windows.Shapes.Ellipse> öğesi ve kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="5bf74-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="5bf74-105">Kullanım, <xref:System.Windows.Shapes.Shape.Fill%2A> belirtmek için özellik <xref:System.Windows.Media.Brush> elipsin iç kısmını boyamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="5bf74-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="5bf74-106">Kullanım, <xref:System.Windows.Shapes.Shape.Stroke%2A> belirtmek için özellik <xref:System.Windows.Media.Brush> elipsin anahat boyamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="5bf74-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="5bf74-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Elipsin Anahat kalınlığı özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bf74-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="5bf74-108">Bir daire çizmek için olun <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> , <xref:System.Windows.Shapes.Ellipse> öğesi birbirine eşittir.</span><span class="sxs-lookup"><span data-stu-id="5bf74-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="5bf74-109">Aşağıdaki örnekte, dört çizer <xref:System.Windows.Shapes.Ellipse> öğeleri içinde bir <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="5bf74-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bf74-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bf74-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="5bf74-111">Bu örnek kullansa da bir <xref:System.Windows.Controls.Canvas> elipsler içermek için elips öğelerini (ve diğer tüm şekil öğelerine) ile kullanabilirsiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> , metin olmayan içerikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="5bf74-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="5bf74-112">Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="5bf74-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf74-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5bf74-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="5bf74-114">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="5bf74-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)

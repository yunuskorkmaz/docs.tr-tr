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
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Nasıl yapılır: Elips veya Daire Çizme
Bu örnek, <xref:System.Windows.Shapes.Ellipse> öğesi kullanılarak üç nokta ve dairelerin nasıl çizileceğini gösterir. Elips çizmek için bir <xref:System.Windows.Shapes.Ellipse> öğesi oluşturun ve <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>belirtin. Elipsin iç kısmını boyamak için kullanılan <xref:System.Windows.Media.Brush> belirtmek için <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğini kullanın. Elipsin ana hattını boyamak için kullanılan <xref:System.Windows.Media.Brush> belirtmek için <xref:System.Windows.Shapes.Shape.Stroke%2A> özelliğini kullanın. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliği, elips anahattının kalınlığını belirtir.  
  
 Bir daire çizmek için <xref:System.Windows.Shapes.Ellipse> öğenin <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> birbirlerine eşit hale getirin.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>içinde dört <xref:System.Windows.Shapes.Ellipse> öğesi çizer.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Bu örnek, üç noktayı içermek için bir <xref:System.Windows.Controls.Canvas> kullansa da metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte elips öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

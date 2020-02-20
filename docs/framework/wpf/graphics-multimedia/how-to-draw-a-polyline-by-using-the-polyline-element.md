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
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme
Bu örnek, <xref:System.Windows.Shapes.Polyline> öğesi kullanılarak bir dizi bağlantılı çizgi olan bir çoklu çizginin nasıl çizileceğini gösterir.  
  
 Bir çoklu çizgi çizmek için bir <xref:System.Windows.Shapes.Polyline> öğesi oluşturun ve <xref:System.Windows.Shapes.Polyline.Points%2A> özelliğini kullanarak şekil köşelerine belirleyin. Son olarak, çizgi ana hattını anlatmak için <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliklerini kullanın.  
  
> [!NOTE]
> <xref:System.Windows.Shapes.Polyline> öğesi kapalı bir şekil olmadığından, şekil ana hattını kasıtlı olarak kapatsanız bile <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğin hiçbir etkisi yoktur. <xref:System.Windows.Shapes.Shape.Fill%2A>ile kapalı bir şekil oluşturmak için <xref:System.Windows.Shapes.Polygon> bir öğesi kullanın.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas>içinde iki <xref:System.Windows.Shapes.Polyline> öğesi çizer.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktalara yönelik geçerli sözdizimi, virgülle ayrılmış x ve y koordinatı çiftleri için boşlukla ayrılmış bir listesidir.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Bu örnek polylines 'ı içermek için bir <xref:System.Windows.Controls.Canvas> kullansa da, metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte çoklu çizgi öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)

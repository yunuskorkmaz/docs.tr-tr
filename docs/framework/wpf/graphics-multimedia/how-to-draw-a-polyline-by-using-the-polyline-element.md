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
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme
Bu örnek, <xref:System.Windows.Shapes.Polyline> öğesini kullanarak bir dizi bağlantılı çizgi olan bir çoklu çizginin nasıl çizileceğini gösterir.  
  
 Bir çoklu çizgi çizmek için bir <xref:System.Windows.Shapes.Polyline> öğe oluşturun ve kendi <xref:System.Windows.Shapes.Polyline.Points%2A> özelliğini kullanarak şekil köşelerine belirleyin. Son olarak, kontur <xref:System.Windows.Shapes.Shape.Stroke%2A> içermeyen <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> bir çizgi görünmez olduğundan, çoklu çizgi anahattını anlatmak için ve özelliklerini kullanın.  
  
> [!NOTE]
> Öğe kapalı bir şekil olmadığından <xref:System.Windows.Shapes.Shape.Fill%2A> , şekil ana hattını kasıtlı olarak kapatsanız bile özelliğin etkisi yoktur. <xref:System.Windows.Shapes.Polyline> İle <xref:System.Windows.Shapes.Shape.Fill%2A>kapalı bir şekil oluşturmak için, bir <xref:System.Windows.Shapes.Polygon> öğesi kullanın.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Controls.Canvas>içinde iki <xref:System.Windows.Shapes.Polyline> öğe çizer.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], nokta için geçerli sözdizimi, virgülle ayrılmış x ve y koordinatı çiftleri için boşlukla ayrılmış bir listesidir.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Bu örnek, polylines <xref:System.Windows.Controls.Canvas> 'ı içermek için bir kullanıyor olsa da, metin olmayan içeriği destekleyen herhangi bir veya herhangi <xref:System.Windows.Controls.Panel> bir veya <xref:System.Windows.Controls.Control> daha fazla öğe içeren çoklu çizgi öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)

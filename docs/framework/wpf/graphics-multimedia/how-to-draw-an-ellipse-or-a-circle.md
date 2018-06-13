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
ms.openlocfilehash: 69620d81eb77eb76f21f099b30017b142d818457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559372"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Nasıl yapılır: Elips veya Daire Çizme
Bu örnek kullanarak elipsler ve daireler çizin gösterilmektedir <xref:System.Windows.Shapes.Ellipse> öğesi. Elips çizmek için oluşturma bir <xref:System.Windows.Shapes.Ellipse> öğesi ve kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A>. Kullanım kendi <xref:System.Windows.Shapes.Shape.Fill%2A> belirtmek için özellik <xref:System.Windows.Media.Brush> elipsin iç kısmını boyamak için kullanılan. Kullanım kendi <xref:System.Windows.Shapes.Shape.Stroke%2A> belirtmek için özellik <xref:System.Windows.Media.Brush> elipsin anahat boyamak için kullanılan. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Özelliği elips anahat kalınlığını belirtir.  
  
 Bir daire çizmek için olun <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> , <xref:System.Windows.Shapes.Ellipse> öğesi birbirine eşit.  
  
 Aşağıdaki örnek dört çizer <xref:System.Windows.Shapes.Ellipse> içinde öğelerin bir <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Bu örnek kullanıyor olsa da bir <xref:System.Windows.Controls.Canvas> üç nokta içerecek şekilde elips öğelerini (ve diğer tüm şekil öğelerini) ile kullanabilirsiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> metin dışı içeriği destekler.  
  
 Bu örnek daha büyük bir örneğin parçasıdır; tam bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [Şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037)

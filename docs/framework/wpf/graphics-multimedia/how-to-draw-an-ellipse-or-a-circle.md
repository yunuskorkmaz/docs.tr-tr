---
title: 'Nasıl yapılır: Elips veya Daire Çizme'
description: Windows Presentation Foundation (WPF) içinde, ana hat kalınlığı ve iç renk seçenekleriyle bir elips veya daire çizmeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853565"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>Nasıl yapılır: Elips veya Daire Çizme
Bu örnek, öğesini kullanarak elips ve dairelerin nasıl çizileceğini gösterir <xref:System.Windows.Shapes.Ellipse> . Elips çizmek için bir <xref:System.Windows.Shapes.Ellipse> öğe oluşturun ve ve ' ı belirtin <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> . <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Media.Brush> Elipsin iç kısmını boyamak için kullanılan öğesini belirtmek için özelliğini kullanın. <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Media.Brush> Elipsin anahattını boyamak için kullanılan öğesini belirtmek için özelliğini kullanın. <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>Özelliği, elips anahattının kalınlığını belirtir.  
  
 Bir daire çizmek için <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> öğesi ve öğelerini birbirlerine eşit yapın.  
  
 Aşağıdaki örnek, içinde dört <xref:System.Windows.Shapes.Ellipse> öğe çizer <xref:System.Windows.Controls.Canvas> .  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 Bu örnek, üç noktayı içermek için bir kullanıyor olsa da <xref:System.Windows.Controls.Canvas> , elips öğelerini (ve diğer tüm şekil öğelerini) <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> metin olmayan içeriği destekleyen herhangi bir ile birlikte kullanabilirsiniz.  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

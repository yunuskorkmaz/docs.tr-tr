---
title: 'Nasıl yapılır: Çizgi Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452954"
---
# <a name="how-to-draw-a-line"></a>Nasıl yapılır: Çizgi Çizme
Bu örnek, <xref:System.Windows.Shapes.Line> öğesini kullanarak nasıl çizgi çizileceğini gösterir.  
  
 Çizgi çizmek için bir <xref:System.Windows.Shapes.Line> öğesi oluşturun. Başlangıç noktasını ayarlamak için <xref:System.Windows.Shapes.Line.X1%2A> ve <xref:System.Windows.Shapes.Line.Y1%2A> özelliklerini kullanın; ve <xref:System.Windows.Shapes.Line.X2%2A> ve <xref:System.Windows.Shapes.Line.Y2%2A> özelliklerini kullanarak bitiş noktasını ayarlayın. Son olarak, konturu olmayan bir çizgi görünmez olduğundan <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> ayarlayın.  
  
 Bir çizginin iç kısmı olmadığından, bir satır için <xref:System.Windows.Shapes.Shape.Fill%2A> öğesinin ayarlanması etkisizdir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Canvas> öğesinin içinde üç satır çizer.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Line>
- [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)

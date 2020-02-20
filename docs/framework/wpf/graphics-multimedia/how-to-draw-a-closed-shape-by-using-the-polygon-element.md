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
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Nasıl yapılır: Çokgen Öğe Kullanarak Kapalı Şekil Çizme
Bu örnek, <xref:System.Windows.Shapes.Polygon> öğesi kullanılarak nasıl kapalı bir şekil çizileceğini gösterir. Kapalı bir şekil çizmek için bir <xref:System.Windows.Shapes.Polygon> öğesi oluşturun ve bir şeklin köşelerini belirtmek için <xref:System.Windows.Shapes.Polygon.Points%2A> özelliğini kullanın. İlk ve son noktaları bağlayan bir çizgi otomatik olarak çizilir. Son olarak, bir <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>veya her ikisini de belirtin.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktalara yönelik geçerli sözdizimi, virgülle ayrılmış x ve y koordinatı çiftleri için boşlukla ayrılmış bir listesidir.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Örnek, çokgenler içeren bir <xref:System.Windows.Controls.Canvas> kullansa da, metin olmayan içeriği destekleyen herhangi bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> birlikte çokgen öğelerini (ve diğer tüm şekil öğelerini) kullanabilirsiniz.  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

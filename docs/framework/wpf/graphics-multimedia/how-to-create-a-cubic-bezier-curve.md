---
title: 'Nasıl yapılır: Üçüncü Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452116"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>Nasıl yapılır: Üçüncü Dereceden Bezier Eğrisi Oluşturma
Bu örnek, üçüncü dereceden Bezier eğrisinin nasıl oluşturulacağını gösterir. Üçüncü dereceden Bezier eğrisi oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.BezierSegment> sınıflarını kullanın.  Elde edilen geometriyi göstermek için bir <xref:System.Windows.Shapes.Path> öğesi kullanın veya bir <xref:System.Windows.Media.GeometryDrawing> ya da <xref:System.Windows.Media.DrawingContext>ile kullanın. Aşağıdaki örneklerde, (10, 100) (300, 100) arasında bir üçüncü dereceden Bezier eğrisi çizilir. Eğrinin (100, 0) ve (200, 200) denetim noktaları vardır.  
  
## <a name="example"></a>Örnek  
 xaml  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için kısaltılmış biçimlendirme sözdizimini kullanabilirsiniz.  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 xaml  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne etiketlerini kullanarak üçüncü dereceden Bezier eğrisi da çizebilirsiniz. Aşağıdaki, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğine eşdeğerdir.  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Elips Yay Oluşturma](how-to-create-an-elliptical-arc.md)
- [PathGeometry İçinde LineSegment Oluşturma](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [Üçüncü Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-cubic-bezier-curve.md)
- [İkinci Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-quadratic-bezier-curve.md)

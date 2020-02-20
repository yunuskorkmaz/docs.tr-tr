---
title: 'Nasıl yapılır: Elips Yay Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453071"
---
# <a name="how-to-create-an-elliptical-arc"></a>Nasıl yapılır: Elips Yay Oluşturma
Bu örnek, elips bir yayı nasıl çizileceğini gösterir. Elips bir yay oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.ArcSegment> sınıflarını kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, (10.100) öğesinden (200.100) bir elips yay çizilir. Arc, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> cihazdan bağımsız piksel, 45 <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> bir `true`ve <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>bir 50 100 <xref:System.Windows.Media.ArcSegment.Size%2A> sahiptir.  
  
 xaml  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için öznitelik sözdizimini kullanabilirsiniz.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 xaml  
  
 (Bu öznitelik sözdiziminin aslında bir <xref:System.Windows.Media.PathGeometry>daha hafif bir sürümünü <xref:System.Windows.Media.StreamGeometry>oluşturduğunu unutmayın. Daha fazla bilgi için [yol biçimlendirme sözdizimi](path-markup-syntax.md) sayfasına bakın.)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]' de, açıkça nesne etiketleri kullanarak elips bir yay çizebilirsiniz. Aşağıda, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmesine eşdeğerdir.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır. Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkinci Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-quadratic-bezier-curve.md)
- [Üçüncü Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-cubic-bezier-curve.md)

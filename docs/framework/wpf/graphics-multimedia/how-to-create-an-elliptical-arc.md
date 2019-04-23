---
title: 'Nasıl yapılır: Elips Yay Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: aae304b9963f3a8e5833b4d8ba0a54777a750225
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183657"
---
# <a name="how-to-create-an-elliptical-arc"></a>Nasıl yapılır: Elips Yay Oluşturma
Bu örnek, bir elips yay çizmenin gösterilmektedir. Elips yay oluşturma için kullanın <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.ArcSegment> sınıfları.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, elips yay dan (200,100) (10,100) çizilir. Yayı sahip bir <xref:System.Windows.Media.ArcSegment.Size%2A> 100 tarafından 50 CİHAZDAN bağımsız piksel bir <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> açısını 45 derecenin bir <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ayarıyla `true`ve <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> , <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 [xaml]  
  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], öznitelik sözdizimi bir yolunu tanımlamak için kullanabilirsiniz.  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (Aslında bu öznitelik sözdizimi oluşturan Not bir <xref:System.Windows.Media.StreamGeometry>, daha basit sürümü bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için [yol işaretleme söz dizimi](path-markup-syntax.md) sayfası.)  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne etiketleri kullanarak açıkça elips yay çizebilirsiniz. Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Bu örnek, daha büyük bir örnek bir parçasıdır. Tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkinci Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-quadratic-bezier-curve.md)
- [Üçüncü Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-cubic-bezier-curve.md)

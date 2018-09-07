---
title: 'Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 8481a7e0e6d682a335b22ea6cdf73a23a9f155af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085838"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma
Bu örnekte, ikinci dereceden Bezier eğrisi oluşturma işlemi gösterilmektedir.  İkinci dereceden Bezier eğrisi oluşturmak için kullanın <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.QuadraticBezierSegment> sınıfları.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, ikinci dereceden Bezier eğrisi (300,100) için (10,100) çizilir. Eğriyi (200,200) bir denetim noktası var.  
  
 [xaml]  
  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], öznitelik sözdizimi bir yolunu tanımlamak için kullanabilirsiniz.  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 [xaml]  
  
 (Aslında bu öznitelik sözdizimi oluşturan Not bir <xref:System.Windows.Media.StreamGeometry>, daha basit sürümü bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için [yol işaretleme söz dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne öğesi sözdizimi kullanarak ikinci dereceden Bezier eğrisi da çizebilirsiniz. Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek.  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Bu örnek, daha büyük örnek bir parçasıdır; tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Elips Yay Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [Üçüncü Dereceden Bezier Eğrisi Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)

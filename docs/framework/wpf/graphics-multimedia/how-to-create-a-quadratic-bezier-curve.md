---
title: 'Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452077"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma
Bu örnek, ikinci dereceden Bezier eğrisinin nasıl oluşturulacağını gösterir.  İkinci dereceden Bezier eğrisi oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.QuadraticBezierSegment> sınıflarını kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, (10.100) ile (300.100) arasında bir ikinci dereceden Bezier eğrisi çizilir. Eğrinin bir denetim noktası (200.200) vardır.  
  
 xaml  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için öznitelik sözdizimini kullanabilirsiniz.  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 xaml  
  
 (Bu öznitelik sözdiziminin aslında bir <xref:System.Windows.Media.PathGeometry>daha hafif bir sürümünü <xref:System.Windows.Media.StreamGeometry>oluşturduğunu unutmayın. Daha fazla bilgi için [yol biçimlendirme sözdizimi](path-markup-syntax.md) sayfasına bakın.)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne öğesi söz dizimini kullanarak ikinci dereceden Bezier eğrisi da çizebilirsiniz. Aşağıdaki, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğine eşdeğerdir.  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Elips Yay Oluşturma](how-to-create-an-elliptical-arc.md)
- [Üçüncü Dereceden Bezier Eğrisi Oluşturma](how-to-create-a-cubic-bezier-curve.md)

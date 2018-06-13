---
title: 'Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559338"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma
Bu örnek, birden çok alt oluşturulacağını gösterir bir <xref:System.Windows.Media.PathGeometry>. Birden çok alt yolların oluşturmak için oluşturduğunuz bir <xref:System.Windows.Media.PathFigure> her alt yolu için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki alt, her biri bir üçgen oluşturur.  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 Aşağıdaki örnek kullanarak birden çok alt yolların oluşturulacağını gösterir bir <xref:System.Windows.Shapes.Path> ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik sözdizimi. Her `M` her bir üçgen çizmek iki alt örneği oluşturur, böylece yeni bir alt yolu oluşturur.  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Bu öznitelik sözdizimi gerçekte oluşturur Not bir <xref:System.Windows.Media.StreamGeometry>, hafifletilmiş sürümü bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)

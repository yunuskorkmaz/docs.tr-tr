---
title: 'Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904728"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma
Bu örnek, birden çok alt yol oluşturma işlemini gösterir bir <xref:System.Windows.Media.PathGeometry>. Birden çok alt yol oluşturma için oluşturduğunuz bir <xref:System.Windows.Media.PathFigure> için her alt yol.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki alt, her biri bir üçgen oluşturur.  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 Aşağıdaki örnek, kullanarak birden çok alt yol oluşturma işlemi gösterilmektedir bir <xref:System.Windows.Shapes.Path> ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik sözdizimi. Her `M` çizen bir üçgen her iki alt örneği oluşturur, böylece yeni bir alt oluşturur.  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Aslında bu öznitelik sözdizimi oluşturan Not bir <xref:System.Windows.Media.StreamGeometry>, daha basit sürümü bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için [yol işaretleme söz dizimi](path-markup-syntax.md) sayfası.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geometriye Genel Bakış](geometry-overview.md)

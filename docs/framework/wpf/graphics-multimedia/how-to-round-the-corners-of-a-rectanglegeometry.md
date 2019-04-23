---
title: "Nasıl yapılır: RectangleGeometry'nin Köşelerini Yuvarlama"
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089139"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Nasıl yapılır: RectangleGeometry'nin Köşelerini Yuvarlama
Köşelerini yuvarlatmak için bir <xref:System.Windows.Media.RectangleGeometry>ayarlayın, <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> sıfırdan büyük bir değere özellikleri. Daha büyük değerler, yuvarlaklaşır dikdörtgenin köşelerini.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli gösterir <xref:System.Windows.Media.RectangleGeometry> farklı nesneleriyle <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ayarları. <xref:System.Windows.Media.RectangleGeometry> Nesneler kullanarak görüntülenir <xref:System.Windows.Shapes.Path> öğeleri.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Farklı RadiusX dikdörtgenin&#47;RadiusY ayarları](./media/graphicsmm-rounded.png "graphicsmm_rounded")  
Yuvarlak köşeli dikdörtgen  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geometriye Genel Bakış](geometry-overview.md)
- [Bileşik Şekil Oluşturma](how-to-create-a-composite-shape.md)
- [PathGeometry Kullanarak Şekil Oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md)

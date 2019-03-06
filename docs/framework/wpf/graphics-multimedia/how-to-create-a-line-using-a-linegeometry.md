---
title: 'Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: 6d5d0b413f940a2c7f70e05135ff070c1fe5ba21
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374667"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LineGeometry> bir satırı tanımlamak için sınıf. A <xref:System.Windows.Media.LineGeometry> kendi başlangıç ve bitiş noktası tarafından tanımlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.LineGeometry>.  A <xref:System.Windows.Shapes.Path> öğesi satırı işlemek için kullanılır.  Bir satır, alanı olmadığından <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> belirtilmedi; bunun yerine <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri kullanılır.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry (10,20)'den alınan (100,130)  
  
 Diğer basit geometri sınıfları <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.EllipseGeometry>. Daha karmaşık olanları yanı sıra bu geometriler ayrıca kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya <xref:System.Windows.Media.StreamGeometry>. Daha fazla bilgi için [geometrisi](geometry-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Geometriye Genel Bakış](geometry-overview.md)
- [Bileşik Şekil Oluşturma](how-to-create-a-composite-shape.md)
- [PathGeometry Kullanarak Şekil Oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md)

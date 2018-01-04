---
title: "Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 487a5ffaf952450c6196f5fe0d00fd249177b054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LineGeometry> bir satır açıklamak için sınıf. A <xref:System.Windows.Media.LineGeometry> kendi başlangıç ve bitiş noktaları tarafından tanımlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturma ve işleme gösterir bir <xref:System.Windows.Media.LineGeometry>.  A <xref:System.Windows.Shapes.Path> öğesi çizgiyi işlemek için kullanılır.  Bir çizginin hiçbir alan olmadığından <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> belirtilmedi; bunun yerine <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri kullanılır.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
(10,20)'den (100,130) çizilen bir LineGeometry  
  
 Diğer basit geometri sınıfları dahil <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.EllipseGeometry>. Daha karmaşık olanları yanı sıra bu geometri ayrıca kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya <xref:System.Windows.Media.StreamGeometry>. Daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Bileşik Şekil Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [PathGeometry Kullanarak Şekil Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)

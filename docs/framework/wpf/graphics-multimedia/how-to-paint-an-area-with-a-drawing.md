---
title: 'Nasıl yapılır: Çizim ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010091"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>Nasıl yapılır: Çizim ile bir Alanı Boyama
Bu örnek, bir çizim ile bir alanı boyama gösterilmektedir. Çizim ile bir alanı boyama için kullandığınız bir <xref:System.Windows.Media.DrawingBrush> ve bir veya daha fazla <xref:System.Windows.Media.Drawing> nesneleri.   Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingBrush> iki elips çizim ile bir nesneyi boyamak için.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 Örnekteki çıktı aşağıda gösterilmiştir.  
  
 ![DrawingBrush ' çıkış](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (Açıklanan sebeplerden dolayı şeklin Orta beyaz [bileşik şeklin dolgusunu denetleme](how-to-control-the-fill-of-a-composite-shape.md).)  
  
 Ayarlayarak bir <xref:System.Windows.Media.DrawingBrush> nesnenin <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> özellikleri, yinelenen bir desen oluşturabilirsiniz. Aşağıdaki örnek, bir nesne iki elips Çizimden oluşturulan bir desen ile boyar.  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 Aşağıdaki çizim döşenmiş gösterir <xref:System.Windows.Media.DrawingBrush> çıktı.  
  
 ![Döşeli DrawingBrush çıkışı](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 Çizim fırçaları hakkında daha fazla bilgi için bkz. [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md). Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelerine genel bakış](drawing-objects-overview.md).

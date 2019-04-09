---
title: 'Nasıl yapılır: Bileşik Çizim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132476"
---
# <a name="how-to-create-a-composite-drawing"></a>Nasıl yapılır: Bileşik Çizim Oluşturma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.DrawingGroup> birden çok birleştirerek karmaşık çizimleri oluşturmak için <xref:System.Windows.Media.Drawing> tek bir bileşik çizim nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingGroup> bileşik çizim oluşturma <xref:System.Windows.Media.GeometryDrawing> ve <xref:System.Windows.Media.ImageDrawing> nesneleri. Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.  
  
 ![Birden çok çizimler DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
DrawingGroup kullanılarak oluşturulan bir bileşik çizim  
  
 Çizim sınırları gösteren gri kenarlık unutmayın.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Kullanabileceğiniz bir <xref:System.Windows.Media.DrawingGroup> uygulamak için bir <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ayarını <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, veya <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> içerdiği çizimler için. Çünkü bir <xref:System.Windows.Media.DrawingGroup> aynı zamanda bir <xref:System.Windows.Media.Drawing>, diğer içerebilir <xref:System.Windows.Media.DrawingGroup> nesneleri.  
  
 Ek kullanması hariç, aşağıdaki örnek önceki örneğe benzer <xref:System.Windows.Media.DrawingGroup> bit eşlem efektleri ve geçirgenlik maskesi bazı çizimlerde uygulamak için nesne. Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.  
  
 ![Birden çok çizimler DrawingGroup](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
Bileşik çizim sahip birden fazla DrawingGroup nesneleri  
  
 Çizim sınırları gösteren gri kenarlık unutmayın.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)

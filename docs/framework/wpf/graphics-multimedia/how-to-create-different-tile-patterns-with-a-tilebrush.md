---
title: 'Nasıl yapılır: TileBrush ile Farklı Döşeme Desenleri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: c1051b234961eee9ae740af2abac3d64c523656c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227411"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Nasıl yapılır: TileBrush ile Farklı Döşeme Desenleri Oluşturma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği bir <xref:System.Windows.Media.TileBrush> desen oluşturmak için.  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> Özelliği belirtmenize imkan tanır nasıl içeriğini bir <xref:System.Windows.Media.TileBrush> yinelenen, diğer bir deyişle, bir çıkış alanı dolduracak şekilde döşenir. Desen oluşturmak için ayarladığınız <xref:System.Windows.Media.TileBrush.TileMode%2A> için <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, veya <xref:System.Windows.Media.TileMode.FlipXY>. Ayrıca ayarlamanız gerekir <xref:System.Windows.Media.TileBrush.Viewport%2A> , <xref:System.Windows.Media.TileBrush> boyama; alanından daha küçükse, aksi takdirde, yalnızca tek bir kutucuk bakılmaksızın olduğu <xref:System.Windows.Media.TileBrush.TileMode%2A> kullanmanız ayarı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, beş oluşturur <xref:System.Windows.Media.DrawingBrush> nesneleri, bunları her farklı bir veren <xref:System.Windows.Media.TileBrush.TileMode%2A> ayarlama ve bunları beş dikdörtgenler boyamak için kullanır. Bu örnek kullansa <xref:System.Windows.Media.DrawingBrush> göstermek için sınıf <xref:System.Windows.Media.TileBrush.TileMode%2A> davranışı <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği çalıştığı aynı şekilde tüm <xref:System.Windows.Media.TileBrush> nesnelerini, diğer bir deyişle, için <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, ve <xref:System.Windows.Media.DrawingBrush>.  
  
 Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.  
  
 ![Örnek çıktı döşeme TileBrush](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Döşeme desenleri TileMode özelliği ile oluşturulmuş  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TileBrush için Döşeme Boyutunu Ayarlama](how-to-set-the-tile-size-for-a-tilebrush.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)

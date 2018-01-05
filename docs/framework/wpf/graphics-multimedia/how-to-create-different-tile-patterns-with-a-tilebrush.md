---
title: "Nasıl yapılır: TileBrush ile Farklı Döşeme Desenleri Oluşturma"
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
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646ce5142875c95c0b1ca19643790f73f7eb83e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Nasıl yapılır: TileBrush ile Farklı Döşeme Desenleri Oluşturma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği bir <xref:System.Windows.Media.TileBrush> bir desen oluşturmak için.  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> Özelliği belirtmenize olanak sağlar nasıl içeriğini bir <xref:System.Windows.Media.TileBrush> yinelenen, diğer bir deyişle, bir çıkış alanı dolduracak şekilde döşenir. Bir desen oluşturmak için ayarladığınız <xref:System.Windows.Media.TileBrush.TileMode%2A> için <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, veya <xref:System.Windows.Media.TileMode.FlipXY>. De ayarlamalısınız <xref:System.Windows.Media.TileBrush.Viewport%2A> , <xref:System.Windows.Media.TileBrush> böylece boyama; alandan daha küçük Aksi halde, yalnızca tek bir döşeme bakılmaksızın olduğu <xref:System.Windows.Media.TileBrush.TileMode%2A> ayarını kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, beş oluşturur <xref:System.Windows.Media.DrawingBrush> nesneleri, bunların her farklı bir verir <xref:System.Windows.Media.TileBrush.TileMode%2A> ayarlama ve onları beş dikdörtgeni boyamak için kullanır. Bu örnek kullansa <xref:System.Windows.Media.DrawingBrush> göstermek için sınıf <xref:System.Windows.Media.TileBrush.TileMode%2A> davranışı <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği aynı çalışır tüm <xref:System.Windows.Media.TileBrush> nesneleri, diğer bir deyişle, için <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, ve <xref:System.Windows.Media.DrawingBrush>.  
  
 Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.  
  
 ![Örnek çıktı döşeme TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
TileMode özelliği ile oluşturulan döşeme desenleri  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TileBrush için Döşeme Boyutunu Ayarlama](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)

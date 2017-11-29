---
title: "Nasıl yapılır: Bileşik Çizim Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7789f9aa94db32d3dc61ccf01ef9ddfe1e777a37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-composite-drawing"></a>Nasıl yapılır: Bileşik Çizim Oluşturma
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.DrawingGroup> birden çok birleştirerek karmaşık çizimler oluşturmak için <xref:System.Windows.Media.Drawing> tek bileşik çizim nesnelerine.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingGroup> çizim bileşik oluşturmak için <xref:System.Windows.Media.GeometryDrawing> ve <xref:System.Windows.Media.ImageDrawing> nesneleri. Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.  
  
 ![Birden çok çizimler DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
DrawingGroup kullanılarak oluşturulan bir bileşik çizim  
  
 Çizim sınırlarına gösterir gri kenarlık unutmayın.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Kullanabileceğiniz bir <xref:System.Windows.Media.DrawingGroup> uygulamak için bir <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ayarı <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, veya <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> içerdiği çizimler için. Çünkü bir <xref:System.Windows.Media.DrawingGroup> aynı zamanda bir <xref:System.Windows.Media.Drawing>, diğer içerebilir <xref:System.Windows.Media.DrawingGroup> nesneleri.  
  
 Ek kullanan aşağıdaki örnek önceki örneğe benzerdir <xref:System.Windows.Media.DrawingGroup> bazı çizimlerde bit eşlem efektleri ve geçirgenlik maskesi uygulamak için nesneleri. Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.  
  
 ![Birden çok çizimler DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
Birden çok DrawingGroup nesneleri bileşik çizim sahip  
  
 Çizim sınırlarına gösterir gri kenarlık unutmayın.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [Çizim nesnelerine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)

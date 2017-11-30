---
title: "Nasıl yapılır: TileBrush Yatay ve Dikey Hizalamasını Ayarlama"
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
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c581bb167c020e9e4f0de26b0e17e7a1d70704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Nasıl yapılır: TileBrush Yatay ve Dikey Hizalamasını Ayarlama
Bu örnek, döşeme içinde içeriğin yatay ve dikey hizalamasını denetlemek gösterilmiştir. Yatay ve dikey hizalamasını denetlemek için bir <xref:System.Windows.Media.TileBrush>, kullanma, <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özellikleri.  
  
 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> Ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliklerini bir <xref:System.Windows.Media.TileBrush> kullanılan olduğunda aşağıdaki koşullardan herhangi biri doğruysa:  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill> ve <xref:System.Windows.Media.TileBrush.Viewbox%2A> ve <xref:System.Windows.Media.TileBrush.Viewport%2A> farklı en boy oranlarına sahiptir.  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği <xref:System.Windows.Media.Stretch.None> ve <xref:System.Windows.Media.TileBrush.Viewbox%2A> ve <xref:System.Windows.Media.TileBrush.Viewport%2A> farklı boyutlarda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içeriği hizalanır bir <xref:System.Windows.Media.DrawingBrush>, bir tür olduğu <xref:System.Windows.Media.TileBrush>, döşemesinin sol üst köşesindeki için. Örnek içeriği hizalamak için <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliği <xref:System.Windows.Media.DrawingBrush> için <xref:System.Windows.Media.AlignmentX.Left> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğine <xref:System.Windows.Media.AlignmentY.Top>. Bu örnek şu çıkışı üretir.  
  
 ![Üst &#45;TileBrush; sol hizalama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
Sol üst köşesindeki hizalanan TileBrush içeriği  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte içeriğini hizalanır bir <xref:System.Windows.Media.DrawingBrush> ayarlayarak döşemesinin sağ alt köşesine <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliğine <xref:System.Windows.Media.AlignmentX.Right> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğine <xref:System.Windows.Media.AlignmentY.Bottom>. Örneğin şu çıkışı üretir.  
  
 ![Alt &#45;TileBrush; sağa hizalama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
Sağ alt köşedeki hizalanan TileBrush içeriği  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte içeriğini hizalanır bir <xref:System.Windows.Media.DrawingBrush> ayarlayarak döşemesinin sol üst köşesine <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliğine <xref:System.Windows.Media.AlignmentX.Left> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğine <xref:System.Windows.Media.AlignmentY.Top>. Ayrıca ayarlar <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> , <xref:System.Windows.Media.DrawingBrush> döşeme deseni oluşturmak için. Örneğin şu çıkışı üretir.  
  
 ![Üst &#45;döşeli bir TileBrush; sol hizalama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Döşeme deseni içeriği hizalanan sol üst köşede temel döşeme  
  
 İçeriğinin nasıl hizalandığını görebilmeniz için çizim vurgular döşeme abase. Dikkat <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ayarı etkisi yoktur çünkü içeriğini <xref:System.Windows.Media.DrawingBrush> tamamen temel döşeme yatay olarak doldurur.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Örnek  
 Son örnek bir döşeli içeriğini hizalar <xref:System.Windows.Media.DrawingBrush> ayarlayarak temel döşemesinin sağ alt köşesindeki için <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliğine <xref:System.Windows.Media.AlignmentX.Right> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğine <xref:System.Windows.Media.AlignmentY.Bottom>. Örneğin şu çıkışı üretir.  
  
 ![Bir alt &#45;TileBrush döşenir; sağa hizalama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Döşeme deseni içeriği hizalanan taban döşemesinin sağ alt  
  
 Yeniden <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ayarı etkisi yoktur çünkü içeriğini <xref:System.Windows.Media.DrawingBrush> tamamen temel döşeme yatay olarak doldurur.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 Örneklerde <xref:System.Windows.Media.DrawingBrush> göstermek için nesneler nasıl <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özellikleri kullanılır. Bu özellikleri tüm Döşeme fırçaları için aynı şekilde davranır: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, ve <xref:System.Windows.Media.VisualBrush>. Döşeme fırçaları hakkında daha fazla bilgi için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 [Görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)

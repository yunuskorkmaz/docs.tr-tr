---
title: 'Nasıl yapılır: TileBrush Yatay ve Dikey Hizalamasını Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
ms.openlocfilehash: ddef63bba7fce1bfb8d50b4f2dbaaddfa76709ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149194"
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Nasıl yapılır: TileBrush Yatay ve Dikey Hizalamasını Ayarlama
Bu örnek, bir döşeme içindeki içeriği yatay ve dikey hizalamasını denetlemek nasıl gösterir. Yatay ve dikey hizalamasını denetlemek için bir <xref:System.Windows.Media.TileBrush>, kullanma, <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özellikleri.  
  
 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> Ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliklerini bir <xref:System.Windows.Media.TileBrush> kullanılan olduğunda aşağıdaki koşullardan biri doğruysa:  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill> ve <xref:System.Windows.Media.TileBrush.Viewbox%2A> ve <xref:System.Windows.Media.TileBrush.Viewport%2A> farklı en boy oranlarına sahip.  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Özelliği <xref:System.Windows.Media.Stretch.None> ve <xref:System.Windows.Media.TileBrush.Viewbox%2A> ve <xref:System.Windows.Media.TileBrush.Viewport%2A> farklı boyutlarda.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içeriği hizalanır bir <xref:System.Windows.Media.DrawingBrush>, bir tür olduğu <xref:System.Windows.Media.TileBrush>, sol üst köşesine için. Örnek içerik hizalama için <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliği <xref:System.Windows.Media.DrawingBrush> için <xref:System.Windows.Media.AlignmentX.Left> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğini <xref:System.Windows.Media.AlignmentY.Top>. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![TileBrush ile üst&#45;sola hizalıdır](./media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
TileBrush için sol üst köşesine hizalanır içeriği  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte içeriğini hizalanır bir <xref:System.Windows.Media.DrawingBrush> ayarlayarak, kutucuğa sağ alt köşesine <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliğini <xref:System.Windows.Media.AlignmentX.Right> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğini <xref:System.Windows.Media.AlignmentY.Bottom>. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![TileBrush ile alt&#45;sağa hizalama](./media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
TileBrush için sağ alt köşedeki hizalı içeriği  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte içeriğini hizalanır bir <xref:System.Windows.Media.DrawingBrush> ayarlayarak döşemesinin sol üst köşesine <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliğini <xref:System.Windows.Media.AlignmentX.Left> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğini <xref:System.Windows.Media.AlignmentY.Top>. Ayrıca ayarlar <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> , <xref:System.Windows.Media.DrawingBrush> bir döşeme düzen oluşturmak için. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Bir döşemeli TileBrush ile üst&#45;sola hizalıdır](./media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Hizalanan içeriği kutucuk deseni taban döşemesi üst sol  
  
 Çizim vurgular kutucuk abase, içeriğinin nasıl hizalandığını görebilirsiniz. Dikkat <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ayarı etkisi yoktur çünkü içeriğini <xref:System.Windows.Media.DrawingBrush> taban döşemesi yatay olarak tamamen doldurur.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Örnek  
 Son örnek döşenmiş içeriğini hizalar <xref:System.Windows.Media.DrawingBrush> sağ alt köşesindeki ayarlayarak, temel bir kutucuk için <xref:System.Windows.Media.TileBrush.AlignmentX%2A> özelliğini <xref:System.Windows.Media.AlignmentX.Right> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özelliğini <xref:System.Windows.Media.AlignmentY.Bottom>. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Bir döşemeli TileBrush ile alt&#45;sağa hizalama](./media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Hizalanan kutucuk deseni içeriği temel kutucuğunda sağ alt  
  
 Yeniden <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ayarı etkisi yoktur çünkü içeriğini <xref:System.Windows.Media.DrawingBrush> taban döşemesi yatay olarak tamamen doldurur.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 Örneklerde <xref:System.Windows.Media.DrawingBrush> göstermek için nesneleri nasıl <xref:System.Windows.Media.TileBrush.AlignmentX%2A> ve <xref:System.Windows.Media.TileBrush.AlignmentY%2A> özellikleri kullanılır. Bu özellikler için tüm Döşeme fırçaları aynı şekilde davranır: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, ve <xref:System.Windows.Media.VisualBrush>. Kutucuk Fırçalar hakkında daha fazla bilgi için bkz. [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.VisualBrush>
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)

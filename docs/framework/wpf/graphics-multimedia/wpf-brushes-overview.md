---
title: Fırçalar genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 7a9474b392052900952f5b677ad94b16025de8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186571"
---
# <a name="wpf-brushes-overview"></a>WPF Fırçalarına Genel Bakış
Ekranınızda görünen her şey bir fırçayla boyandığı için görünür. Örneğin, bir düğmenin arka planını, metnin ön planını ve şeklin dolgusu için bir fırça kullanılır. Bu konu fırçalarla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] boyama kavramlarını tanıtır ve örnekler sunar. Fırçalar, nesneleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] basit, düz renklerden karmaşık desen ve görüntü kümelerine kadar her şeyle boyamanızı sağlar.  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a>Fırçayla Boyama  
 Bir <xref:System.Windows.Media.Brush> "boyalar" onun çıkışı ile bir alan. Farklı fırçaların farklı çıktı türleri vardır. Bazı fırçalar bir alanı düz renkle, diğerleri degrade, desen, görüntü veya çizimle boyar. Aşağıdaki resimde, her biri farklı <xref:System.Windows.Media.Brush> türdeki örnekler gösterilmektedir.  
  
 ![Fırça türleri](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Fırça örnekleri  
  
 Çoğu görsel nesne nasıl boyandıklarını belirtmenize olanak tanır. Aşağıdaki tabloda, bir <xref:System.Windows.Media.Brush>.  
  
|Sınıf|Fırça özellikleri|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Aşağıdaki bölümlerde farklı <xref:System.Windows.Media.Brush> türleri açıklar ve her biri bir örnek sağlar.  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a>Katı Renkle Boya  
 Bir <xref:System.Windows.Media.SolidColorBrush> katı <xref:System.Windows.Media.Color>ile bir alan boyar. Bir tanesini <xref:System.Windows.Media.SolidColorBrush.Color%2A> belirtmenin çeşitli yolları <xref:System.Windows.Media.SolidColorBrush>vardır: örneğin, alfa, kırmızı, mavi ve yeşil kanallarını belirtebilir veya <xref:System.Windows.Media.Colors> sınıf tarafından sağlanan önceden tanımlanmış renkten birini kullanabilirsiniz.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.SolidColorBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki resimde boyalı dikdörtgen gösterilmektedir.  
  
 ![SolidColorBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
SolidColorBrush kullanılarak boyanmış bir Dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Sınıf hakkında daha fazla bilgi için, [Düz Renkler ve Degradeler Genel Bakış ile Boyama](painting-with-solid-colors-and-gradients-overview.md)bölümüne bakın. <xref:System.Windows.Media.SolidColorBrush>  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a>Doğrusal Degradeli Boya  
 Bir <xref:System.Windows.Media.LinearGradientBrush> doğrusal degrade ile bir alan boyar. Doğrusal degrade, iki veya daha fazla rengi bir çizgi, degrade ekseni boyunca karıştırır. Degradedeki renkleri ve konumlarını belirtmek için nesneleri kullanırsınız. <xref:System.Windows.Media.GradientStop>  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.LinearGradientBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki resimde boyalı dikdörtgen gösterilmektedir.  
  
 ![LinearGradientBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
LinearGradientBrush kullanılarak boyanmış bir Dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Sınıf hakkında daha fazla bilgi için, [Düz Renkler ve Degradeler Genel Bakış ile Boyama](painting-with-solid-colors-and-gradients-overview.md)bölümüne bakın. <xref:System.Windows.Media.LinearGradientBrush>  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a>Radyal Degrade ile Boya  
 Bir <xref:System.Windows.Media.RadialGradientBrush> radyal degrade ile bir alan boyar. Radyal degrade, iki veya daha fazla rengi bir daire boyunca karıştırır. <xref:System.Windows.Media.LinearGradientBrush> Sınıfta olduğu gibi, <xref:System.Windows.Media.GradientStop> degradedeki renkleri ve konumlarını belirtmek için nesneleri kullanırsınız.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.RadialGradientBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki resimde boyalı dikdörtgen gösterilmektedir.  
  
 ![RadialGradientBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
RadialGradientBrush kullanılarak boyanmış bir Dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Sınıf hakkında daha fazla bilgi için, [Düz Renkler ve Degradeler Genel Bakış ile Boyama](painting-with-solid-colors-and-gradients-overview.md)bölümüne bakın. <xref:System.Windows.Media.RadialGradientBrush>  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a>Resimle Boyama  
 Bir <xref:System.Windows.Media.ImageBrush> alan boyar <xref:System.Windows.Media.ImageSource>bir .  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.ImageBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki resimde boyalı dikdörtgen gösterilmektedir.  
  
 ![ImageBrush ile boyanmış bir Dikdörtgen](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Görüntü kullanılarak boyanmış bir Dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <xref:System.Windows.Media.ImageBrush> Sınıf hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama'ya](painting-with-images-drawings-and-visuals.md)bakın.  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a>Çizimle Boyama  
 Bir <xref:System.Windows.Media.DrawingBrush> alan boyar <xref:System.Windows.Media.Drawing>bir . A <xref:System.Windows.Media.Drawing> şekiller, görüntüler, metin ve ortam içerebilir.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.DrawingBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki resimde boyalı dikdörtgen gösterilmektedir.  
  
 ![DrawingBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
DrawingBrush kullanılarak boyanmış bir Dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <xref:System.Windows.Media.DrawingBrush> Sınıf hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama'ya](painting-with-images-drawings-and-visuals.md)bakın.  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a>Görsel boya  
 Bir <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Media.Visual> nesne ile bir alan boyar. Görsel nesnelere örnek <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Page>olarak <xref:System.Windows.Controls.MediaElement>, ve . A <xref:System.Windows.Media.VisualBrush> ayrıca, uygulamanızın bir bölümünden içeriği başka bir alana yansıtmanızı sağlar; yansıma efektleri oluşturmak ve ekranın büyüteç bölümlerini oluşturmak için çok yararlıdır.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.VisualBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki resimde boyalı dikdörtgen gösterilmektedir.  
  
 ![VisualBrush kullanılarak boyanmış bir dikdörtgen](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
VisualBrush kullanılarak boyanmış bir Dikdörtgen  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <xref:System.Windows.Media.VisualBrush> Sınıf hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama'ya](painting-with-images-drawings-and-visuals.md)bakın.  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a>Önceden Tanımlanmış ve Sistem Fırçaları Kullanarak Boya  
 Kolaylık sağlamak için, Windows Presentation Foundation (WPF) nesneleri boyamak için kullanabileceğiniz önceden tanımlanmış ve sistem fırçaları kümesi sağlar.  
  
- Kullanılabilir önceden tanımlanmış fırçaların listesi için <xref:System.Windows.Media.Brushes> sınıfa bakın. Önceden tanımlanmış bir fırçanın nasıl kullanılacağını gösteren [bir](how-to-paint-an-area-with-a-solid-color.md)örnek için bkz.  
  
- Kullanılabilir sistem fırçalarının listesi için <xref:System.Windows.SystemColors> sınıfa bakın. Örneğin, [bkz.](how-to-paint-an-area-with-a-system-brush.md)  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a>Ortak Fırça Özellikleri  
 <xref:System.Windows.Media.Brush>nesneler, fırçayı saydam veya kısmen saydam yapmak için kullanılabilecek bir <xref:System.Windows.Media.Brush.Opacity%2A> özellik sağlar. 0 <xref:System.Windows.Media.Brush.Opacity%2A> değeri fırçayı tamamen saydam hale <xref:System.Windows.Media.Brush.Opacity%2A> getirirken, 1 değeri fırçayı tamamen opak yapar. Aşağıdaki örnekte, <xref:System.Windows.Media.Brush.Opacity%2A> yüzde <xref:System.Windows.Media.SolidColorBrush> 25 opak hale getirmek için özellik kullanır.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Fırça kısmen saydam renkler içeriyorsa, rengin opaklık değeri fırçanın opaklık değeriyle çarpımı yla birleştirilir. Örneğin, bir fırçanın opaklık değeri 0,5 ve kullanılan bir rengin de opaklık değeri 0,5 ise, çıkış renginin opaklık değeri 0,25'dir.  
  
> [!NOTE]
> Bir fırçanın opaklık değerini değiştirmek, tüm öğenin opaklığını özelliğini <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> kullanmaktan daha etkilidir.  
  
 Bir fırçanın içeriğini veya <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliklerini kullanarak döndürebilir, ölçeklendirebilir, eğriltebilir ve çevirebilirsiniz. Daha fazla bilgi için [Bkz. Fırça Dönüşümü Genel Bakış.](brush-transformation-overview.md)  
  
 Nesneler oldukları <xref:System.Windows.Media.Animation.Animatable> ndan, <xref:System.Windows.Media.Brush> nesneler animasyonlu olabilir. Daha fazla bilgi için [Animasyona Genel Bakış'a](animation-overview.md)bakın.  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a>Freezable Özellikler  
 <xref:System.Windows.Freezable> Sınıftan devraldığı için, <xref:System.Windows.Media.Brush> sınıf çeşitli özel <xref:System.Windows.Media.Brush> özellikler sağlar: nesneler [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak bildirilebilir, birden çok nesne arasında paylaşılabilir ve klonlanabilir. Buna ek olarak, <xref:System.Windows.Media.VisualBrush> performansı artırmak ve iş parçacığı güvenli hale getirmek için salt okunur yapılabilir dışında tüm <xref:System.Windows.Media.Brush> türleri.  
  
 Nesneler tarafından <xref:System.Windows.Freezable> sağlanan farklı özellikler hakkında daha fazla bilgi için [Freezable Objects Overview](../advanced/freezable-objects-overview.md)'a bakın.  
  
 Nesnelerin neden <xref:System.Windows.Media.VisualBrush> dondurulamayacağı hakkında daha fazla <xref:System.Windows.Media.VisualBrush> bilgi için tür sayfasına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Fırçalar Örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [ImageBrush Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [VisualBrush Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [Nasıl Dır Konular](brushes-how-to-topics.md)
- [Diğer Performans Önerileri](../advanced/optimizing-performance-other-recommendations.md)

---
title: WPF Fırçalarına Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ef53da1febd6a49af8404e5889a728a1b7c649b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-brushes-overview"></a>WPF Fırçalarına Genel Bakış
Fırça tarafından boyandığında çünkü ekranda görünen her şeyi görünür olur. Örneğin, bir fırça bir düğme, metin ön ve şeklin dolgu arka plan açıklamak için kullanılır. Bu konu ile Boyama kavramlarını tanıtır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fırçaları ve örnekler sağlar. Fırçalar boyamak etkinleştirme [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] nesneler herhangi bir şeyin desenleri ve görüntüleri karmaşık kümesi için basit, düz renk ile.  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>Fırça ile Boyama  
 A <xref:System.Windows.Media.Brush> "çıktısını sahip bir alan boyar". Farklı fırçalar çıkış farklı tür vardır. Bazı fırçaları düz renk, gradyan, desen, görüntü veya çizim başkalarıyla sahip bir alan boyar. Her biri farklı örnekleri aşağıda gösterilmiştir <xref:System.Windows.Media.Brush> türleri.  
  
 ![Fırça türleri](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
Fırça örnekleri  
  
 Çoğu visual nesneleri nasıl boyanır belirtmenize olanak sağlar. Aşağıdaki tabloda bazı ortak nesneleri ve özellikleri ile kullanabileceğiniz listeler bir <xref:System.Windows.Media.Brush>.  
  
|örneği|Fırça özellikleri|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 Aşağıdaki bölümlerde farklı açıklanmaktadır <xref:System.Windows.Media.Brush> türleri ve her biri bir örnek sağlar.  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>Düz renk ile Boyama  
 A <xref:System.Windows.Media.SolidColorBrush> düz bir sahip bir alan boyar <xref:System.Windows.Media.Color>. Çeşitli belirtmek için çeşitli yollar vardır <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush>: Örneğin, kendi alfa, kırmızı, mavi ve yeşil kanallarını belirtebilir veya tarafından sağlanan önceden tanımlanmış renk birini kullanın <xref:System.Windows.Media.Colors> sınıfı.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.SolidColorBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizimde boyanmış dikdörtgeni gösterir.  
  
 ![Dikdörtgene boyandığında SolidColorBrush kullanılarak](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
Dikdörtgene SolidColorBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.SolidColorBrush> sınıfı için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>Doğrusal gradyan ile Boyama  
 A <xref:System.Windows.Media.LinearGradientBrush> doğrusal gradyan ile alanı boyar. Doğrusal gradyan satır, gradyan ekseni boyunca iki veya daha fazla rengi karıştırır. Kullandığınız <xref:System.Windows.Media.GradientStop> nesneleri renkleri gradyan ve onların konumlarını belirtin.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.LinearGradientBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizimde boyanmış dikdörtgeni gösterir.  
  
 ![Dikdörtgene boyandığında LinearGradientBrush kullanılarak](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
Dikdörtgene LinearGradientBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.LinearGradientBrush> sınıfı için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>Radyal gradyan ile Boyama  
 A <xref:System.Windows.Media.RadialGradientBrush> Radyal gradyan ile alanı boyar. Radyal gradyan daire boyunca iki veya daha fazla rengi karıştırır. İle <xref:System.Windows.Media.LinearGradientBrush> sınıfı, kullandığınız <xref:System.Windows.Media.GradientStop> nesneleri renkleri gradyan ve onların konumlarını belirtin.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.RadialGradientBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizimde boyanmış dikdörtgeni gösterir.  
  
 ![Dikdörtgene boyandığında RadialGradientBrush kullanılarak](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
Dikdörtgene RadialGradientBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.RadialGradientBrush> sınıfı için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>Bir görüntü ile Boyama  
 Bir <xref:System.Windows.Media.ImageBrush> sahip bir alan boyar bir <xref:System.Windows.Media.ImageSource>.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.ImageBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizimde boyanmış dikdörtgeni gösterir.  
  
 ![Dikdörtgene boyandığında ImageBrush tarafından](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
Bir görüntü kullanarak bir dikdörtgen boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> sınıfı için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>Çizim ile Boyama  
 A <xref:System.Windows.Media.DrawingBrush> sahip bir alan boyar bir <xref:System.Windows.Media.Drawing>. A <xref:System.Windows.Media.Drawing> şekiller, görüntüler, metin ve ortam içerebilir.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizimde boyanmış dikdörtgeni gösterir.  
  
 ![Dikdörtgene boyandığında DrawingBrush kullanılarak](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
Dikdörtgene DrawingBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.DrawingBrush> sınıfı için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>Görsel ile Boyama  
 A <xref:System.Windows.Media.VisualBrush> sahip bir alan boyar bir <xref:System.Windows.Media.Visual> nesnesi. Görsel nesneler örneklerindendir <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, ve <xref:System.Windows.Controls.MediaElement>. A <xref:System.Windows.Media.VisualBrush> bir bölümünü başka bir alan; uygulamanıza proje içerik sağlar yansıma efektleri oluşturmak ve ekranın bölümlerini büyütme için faydalıdır.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.VisualBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle>. Aşağıdaki çizimde boyanmış dikdörtgeni gösterir.  
  
 ![Dikdörtgene boyandığında VisualBrush kullanılarak](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
Dikdörtgene VisualBrush kullanılarak boyanır  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.VisualBrush> sınıfı için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>Önceden tanımlanmış ve sistem fırçaları ile Boyama  
 Kolaylık olması için bir dizi önceden tanımlanmış ve sistem nesneleri boyamak için kullanabileceğiniz fırçaları Windows Presentation Foundation (WPF) sağlar.  
  
-   Kullanılabilen önceden tanımlanmış Fırçalar listesi için bkz: <xref:System.Windows.Media.Brushes> sınıfı. Önceden tanımlanmış fırça kullanma gösteren bir örnek için bkz: [düz renk ile alanı boyamak](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-solid-color.md).  
  
-   Kullanılabilir sistem Fırçalar listesi için bkz: <xref:System.Windows.SystemColors> sınıfı. Bir örnek için bkz: [sistem fırçası sahip bir alan boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md).  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>Ortak Fırça özellikleri  
 <xref:System.Windows.Media.Brush> nesneleri sağlayan bir <xref:System.Windows.Media.Brush.Opacity%2A> fırça saydam veya kısmen saydam yapmak için kullanılan özellik. Bir <xref:System.Windows.Media.Brush.Opacity%2A> 0 değeri fırça sırasında tamamen saydam yapar bir <xref:System.Windows.Media.Brush.Opacity%2A> 1 değerini fırça tamamen opak yapar. Aşağıdaki örnek kullanır <xref:System.Windows.Media.Brush.Opacity%2A> özelliğini bir <xref:System.Windows.Media.SolidColorBrush> yüzde 25 donuk.  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 Fırça kısmen saydam renkleri içeriyorsa, renk geçirgenlik değeri fırça geçirgenlik değeri ile çarpma ile birleştirilir. Örneğin, fırça 0,5 geçirgenlik değeri varsa ve fırça içinde kullanılan renk 0,5 geçirgenlik değeri, çıkış rengi geçirgenlik değeri 0,25 sahiptir.  
  
> [!NOTE]
>  Kullanarak tüm öğenin saydamlığını değiştirmek yerine Fırça geçirgenlik değeri değiştirmek için daha verimlidir kendi <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> özelliği.  
  
 Döndürme, ölçeklendirme, eğme ve fırça içeriği kullanarak çevir kendi <xref:System.Windows.Media.Brush.Transform%2A> veya <xref:System.Windows.Media.Brush.RelativeTransform%2A> özellikleri. Daha fazla bilgi için bkz: [fırça dönüşümüne genel bakış](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Çünkü bunlar <xref:System.Windows.Media.Animation.Animatable> nesneleri <xref:System.Windows.Media.Brush> nesneleri ettirilebilir. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable Özellikleri  
 Sınıfından devraldığı için <xref:System.Windows.Freezable> sınıfı, <xref:System.Windows.Media.Brush> sınıfı, birkaç özel özellik sağlar: <xref:System.Windows.Media.Brush> nesneleri olarak bildirilebilir [kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md), birden fazla nesne arasında paylaşılan ve kopyalanamıyor. Ayrıca, tüm <xref:System.Windows.Media.Brush> dışında türleri <xref:System.Windows.Media.VisualBrush> performansını artırmak için salt okunur yapılan ve iş parçacığı yapılan.  
  
 Tarafından sağlanan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Neden hakkında daha fazla bilgi için <xref:System.Windows.Media.VisualBrush> nesneleri olamaz dondurulmuş, bkz: <xref:System.Windows.Media.VisualBrush> türü sayfası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Brush>  
 <xref:System.Windows.Media.Brushes>  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973)  
 [ImageBrush Örneği](http://go.microsoft.com/fwlink/?LinkID=160005)  
 [VisualBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160049)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/brushes-how-to-topics.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)

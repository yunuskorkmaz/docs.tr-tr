---
title: Çizim Nesnelerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: edbb5521069caaa83dc24ca03af510d8e12f1b11
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836532"
---
# <a name="drawing-objects-overview"></a>Çizim Nesnelerine Genel Bakış
Bu konu tanıtır <xref:System.Windows.Media.Drawing> nesneleri ve bunları şekiller, bit eşlemler, metin ve medya verimli bir şekilde çizmek için kullanmayı açıklar. Kullanma <xref:System.Windows.Media.Drawing> küçük resim, oluşturduğunuz nesneleri boyama ile bir <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.Visual> nesneleri.  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Çizim nesnesi nedir?  
 A <xref:System.Windows.Media.Drawing> nesne gibi bir şekil, bit eşlem, görüntü veya metin satırı görünür içeriği açıklar. Farklı türde çizimler içeriği farklı türleri açıklanmaktadır. Çizim nesneleri farklı türlerinin bir listesi verilmiştir.  
  
-   <xref:System.Windows.Media.GeometryDrawing> Bir şekil çizer.  
  
-   <xref:System.Windows.Media.ImageDrawing> Resim çizer.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> Metin çizer.  
  
-   <xref:System.Windows.Media.VideoDrawing> – Bir ses veya video dosyası çalar.  
  
-   <xref:System.Windows.Media.DrawingGroup> Diğer çizimler çizer. Çizim grubu, tek bir bileşik çizim diğer çizimlerini birleştirmek için kullanın.  
  
 <xref:System.Windows.Media.Drawing> nesneleri yönlüdür; kullanabileceğiniz birçok yöntemle bir <xref:System.Windows.Media.Drawing> nesne.  
  
-   Kullanarak, bir görüntü olarak görüntüleyebilirsiniz bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> denetimi.  
  
-   İle kullanabileceğiniz bir <xref:System.Windows.Media.DrawingBrush> gibi bir nesne boyanacak <xref:System.Windows.Controls.Page.Background%2A> , bir <xref:System.Windows.Controls.Page>.  
  
-   Görünümünü tanımlamak için kullanabileceğiniz bir <xref:System.Windows.Media.DrawingVisual>.  
  
-   İçeriğini listeleme için kullanabileceğiniz bir <xref:System.Windows.Media.Visual>.  
  
 WPF çizim şekiller, bit eşlemler, metin ve medya özellikli olan nesnelerin diğer türleri sağlar. Örneğin, ayrıca kullanabileceğiniz <xref:System.Windows.Shapes.Shape> şekiller çizmek için nesneleri ve <xref:System.Windows.Controls.MediaElement> denetimi video uygulamanıza eklemek için başka bir yol sağlar. Bu nedenle ne zaman kullanmalısınız <xref:System.Windows.Media.Drawing> nesneleri? Performans avantajı kazanmak için framework düzeyi özellikleri özelliğinden faydalanmasına veya, ihtiyacınız olduğunda <xref:System.Windows.Freezable> özellikleri. Çünkü <xref:System.Windows.Media.Drawing> nesneler için destek yetersizliği [Düzen](../../../../docs/framework/wpf/advanced/layout.md), giriş ve odak ile alt düzey çizim ve arka plan, küçük resim, açıklama için ideal hale performans avantajlarının sağladıkları <xref:System.Windows.Media.Visual> nesneleri.  
  
 Bir türü olduklarından <xref:System.Windows.Freezable> nesnesi <xref:System.Windows.Media.Drawing> nesneleri elde etmek, aşağıdakileri içeren birkaç özel özellik: olarak bildirilebilir [kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)geliştirmek için salt okunur yapılan birden fazla nesne arasında paylaşılan performans, kopyalanan ve iş parçacığı açısından güvenli hale. Tarafından sağlanan farklı özellikleri hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Bir şekil çizme  
 Bir şekil çizmek için kullandığınız bir <xref:System.Windows.Media.GeometryDrawing>. Geometri çiziminin <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> özelliği çizmek için şekli tanımlar, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> özelliği tanımlar şeklin içinin nasıl boyanacağını ve onun <xref:System.Windows.Media.GeometryDrawing.Pen%2A> özelliği anahattı nasıl çizileceğini açıklar.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.GeometryDrawing> bir şekil çizmek için. Şekil tarafından açıklanan bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesneleri. Şeklin içinin ile boyanır bir <xref:System.Windows.Media.LinearGradientBrush> ve anahattı ile çizilen bir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Bu örnek aşağıdaki oluşturur <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing iki elips](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Tam bir örnek için bkz. [GeometryDrawing Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 Diğer <xref:System.Windows.Media.Geometry> gibi sınıfları <xref:System.Windows.Media.PathGeometry> , eğriler ve yaylar oluşturarak daha karmaşık şekiller oluşturmanıza olanak sağlar. Hakkında daha fazla bilgi için <xref:System.Windows.Media.Geometry> nesneleri bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Kullanmayan şekiller çizmek için diğer yollar hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [şekiller ve temel çizimlere WPF genel bakışında](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Görüntü çizme  
 Bir görüntü çizin için kullandığınız bir <xref:System.Windows.Media.ImageDrawing>. Bir <xref:System.Windows.Media.ImageDrawing> nesnenin <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> özelliği çizmek için görüntüyü açıklar ve kendi <xref:System.Windows.Media.ImageDrawing.Rect%2A> görüntünün nerede çizilmez bölge özelliği tanımlar.  
  
 Aşağıdaki örnek, bir dikdörtgen (75,75) bulunan içine bir resim çizer. yani 100 x 100 piksel. Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.ImageDrawing> örnek tarafından oluşturuldu. Bir gri kenarlık sınırları göstermek için eklenmiştir <xref:System.Windows.Media.ImageDrawing>.  
  
 ![X 100 100 adresindeki çizilmiş ImageDrawing &#40;75,75&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 x 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Görüntüleri hakkında daha fazla bilgi için bkz. [Imaging genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>(Yalnızca kod) medya yürütme  
  
> [!NOTE]
>  Bildirebilirsiniz rağmen bir <xref:System.Windows.Media.VideoDrawing> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], yalnızca yükleyin ve kendi medya kod kullanarak yürütme. Video yürütülecek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullanan bir <xref:System.Windows.Controls.MediaElement> yerine.  
  
 Bir ses veya video dosyası yürütmek için kullandığınız bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer>. Yükleme ve ortam yürütmek için iki yolu vardır. İlk kullanmaktır bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> kendilerini ve ikinci tarafından kendi yoludur <xref:System.Windows.Media.MediaTimeline> ile kullanılacak <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Görüntü gibi uygulamanız ile medya dağıtırken, bir medya dosyası bir proje kaynak olarak kullanamazsınız. Proje dosyanızda, bunun yerine ortam türünü ayarlamalısınız `Content` ayarlayıp `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.  
  
 Kendi oluşturmadan medya yürütme için <xref:System.Windows.Media.MediaTimeline>, aşağıdaki adımları gerçekleştirin.  
  
1.  Oluşturma bir <xref:System.Windows.Media.MediaPlayer> nesne.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Kullanım <xref:System.Windows.Media.MediaPlayer.Open%2A> medya dosyasını yüklemek için yöntemi.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Oluşturma bir <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Medyayı ayarlayarak çizmek için konum ve boyut belirtin <xref:System.Windows.Media.VideoDrawing.Rect%2A> özelliği <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Ayarlama <xref:System.Windows.Media.VideoDrawing.Player%2A> özelliği <xref:System.Windows.Media.VideoDrawing> ile <xref:System.Windows.Media.MediaPlayer> oluşturduğunuz.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Kullanım <xref:System.Windows.Media.MediaPlayer.Play%2A> yöntemi <xref:System.Windows.Media.MediaPlayer> medya oynatmayı başlatmak için.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> video dosyası bir kez oynatmak için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetim kazanmak için kullanmak bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleri. <xref:System.Windows.Media.MediaTimeline> Video yinelenmesi gerektiğini belirtmenize olanak sağlar. Kullanılacak bir <xref:System.Windows.Media.MediaTimeline> ile bir <xref:System.Windows.Media.VideoDrawing>, aşağıdaki adımları gerçekleştirin:  
  
1.  Bildirme <xref:System.Windows.Media.MediaTimeline> ve zamanlama davranışlarını ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Oluşturma bir <xref:System.Windows.Media.MediaClock> gelen <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Oluşturma bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.MediaClock> ayarlamak için kendi <xref:System.Windows.Media.MediaPlayer.Clock%2A> özelliği.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Oluşturma bir <xref:System.Windows.Media.VideoDrawing> ve atama <xref:System.Windows.Media.MediaPlayer> için <xref:System.Windows.Media.VideoDrawing.Player%2A> özelliği <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.MediaTimeline> ile bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> video tekrar tekrar oynatmak için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Kullandığınızda, Not bir <xref:System.Windows.Media.MediaTimeline>, etkileşimli kullandığınız <xref:System.Windows.Media.Animation.ClockController> döndürüldüğü <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.MediaClock> etkileşimli yöntemlerinin yerine medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Metin çizme  
 Metin çizmek için kullandığınız bir <xref:System.Windows.Media.GlyphRunDrawing> ve <xref:System.Windows.Media.GlyphRun>. Aşağıdaki örnekte bir <xref:System.Windows.Media.GlyphRunDrawing> "Hello World" metninin çizmek için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları ile kullanılmak için alt düzey bir nesne. Ekrana metnin çizmek için basit bir yolu bir <xref:System.Windows.Controls.Label> veya <xref:System.Windows.Controls.TextBlock>. Hakkında daha fazla bilgi için <xref:System.Windows.Media.GlyphRun>, bkz: [GlyphRun Nesnesi ve karakter öğesine giriş](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) genel bakış.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Bileşik çizimler  
 A <xref:System.Windows.Media.DrawingGroup> birden çok tek bir bileşik çizim çizimi birleştirmenizi sağlar. Kullanarak bir <xref:System.Windows.Media.DrawingGroup>, tek bir şekil, görüntü ve metin birleştirebilirsiniz <xref:System.Windows.Media.Drawing> nesne.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingGroup> iki birleştirilecek <xref:System.Windows.Media.GeometryDrawing> nesneleri ve bir <xref:System.Windows.Media.ImageDrawing> nesne. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Birden çok çizimler DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Bileşik çizim  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> opaklık maskeleri, dönüşüm, bit eşlem efektleri ve diğer işlemleri içeriğine uygulanmasını sağlar. <xref:System.Windows.Media.DrawingGroup> işlem, şu sırayla uygulanır: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, ardından <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Aşağıdaki çizim sırayı gösterir <xref:System.Windows.Media.DrawingGroup> işlemler uygulanır.  
  
 ![DrawingGroup işlem sırası](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemlerin sırası  
  
 Aşağıdaki tabloda yönetmek için kullanabileceğiniz özellikleri açıklar bir <xref:System.Windows.Media.DrawingGroup> nesnenin içeriğini.  
  
|Özellik|Açıklama|Çizim|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Seçili bölümlerini opaklığını değiştirir <xref:System.Windows.Media.DrawingGroup> içeriği. Bir örnek için bkz [nasıl yapılır: Çizim opaklığını kontrol](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Bir opaklık maskesine sahip bir DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Birörnek opaklığını değiştiğini <xref:System.Windows.Media.DrawingGroup> içeriği. Yapmak için bu özelliği kullanmak bir <xref:System.Windows.Media.Drawing> saydam veya saydam kısmen. Bir örnek için bkz [nasıl yapılır: Bir opaklık maskesi çizime uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Farklı bir opaklık ayarları DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Geçerli bir <xref:System.Windows.Media.Effects.BitmapEffect> için <xref:System.Windows.Media.DrawingGroup> içeriği. Bir örnek için bkz [nasıl yapılır: BitmapEffect çizime uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![DrawingGroup BlurBitmapEffect](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Küçük resimleri <xref:System.Windows.Media.DrawingGroup> bir bölgeye içeriğini açıklayan kullanarak bir <xref:System.Windows.Media.Geometry>. Bir örnek için bkz [nasıl yapılır: Çizim küçük](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Tanımlanan kırpma bölgesini DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Cihaz piksel Belirtilen yönergeleriyle birlikte cihaz bağımsız piksel kılavuzuna tutturur. Bu özellik, ayrıntılı grafik keskin düşük DPI ekranlarda işlemeyi sağlamak için kullanışlıdır. Bir örnek için bkz. [çizime GuidelineSet uygulama](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).|![DrawingGroup GuidelineSet olmadan ve](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Dönüşümler <xref:System.Windows.Media.DrawingGroup> içeriği. Bir örnek için bkz [nasıl yapılır: Dönüşüm çizime uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![A Döndürülmüş DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Çizimi görüntü olarak görüntüleyin  
 Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanmak bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizim özelliğini.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> görüntülemek üzere bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![GeometryDrawing iki elips](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Çizim ile bir nesne boyama  
 A <xref:System.Windows.Media.DrawingBrush> çizim nesnesi ile bir alanı boyar fırça türü. Çizim ile neredeyse tüm grafik nesnesini boyamak için kullanabilirsiniz. <xref:System.Windows.Media.Drawing> Özelliği bir <xref:System.Windows.Media.DrawingBrush> açıklar, <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. İşlenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Media.DrawingBrush>, fırça kullanarak fırçaya ekleme <xref:System.Windows.Media.Drawing> özelliği ve, nesne gibi bir denetim veya panel kullanımı bir grafik boyanacak fırça.  
  
 Aşağıdaki örnekler kullanan bir <xref:System.Windows.Media.DrawingBrush> boyanacak <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> oluşturulan bir desen ile bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Bir DrawingBrush döşenmiş](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
GeometryDrawing DrawingBrush ile kullanılan  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Sınıf çeşitli uzatma ve içeriği döşeme için seçenekler sağlar. Hakkında daha fazla bilgi için <xref:System.Windows.Media.DrawingBrush>, bkz: [görüntüler, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md) genel bakış.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Görsel ile bir çizim oluşturma  
 A <xref:System.Windows.Media.DrawingVisual> çizimi işlemek için tasarlanmış görsel nesne türüdür. Görsel katmanda doğrudan çalışma, üst düzeyde özelleştirilmiş bir grafik ortamı oluşturmak istiyorsanız ve bu genel bakışta açıklanmayan geliştiriciler için kullanılan bir seçenektir. Daha fazla bilgi için [DrawingVisual nesnelerini kullanma](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md) genel bakış.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext nesneleri  
 <xref:System.Windows.Media.DrawingContext> Sınıfı sağlar, doldurmak bir <xref:System.Windows.Media.Visual> veya <xref:System.Windows.Media.Drawing> görsel içeriğe sahip. Çok düşük düzeyli grafik nesneleri kullanan bir <xref:System.Windows.Media.DrawingContext> çünkü çok verimli bir şekilde grafik içeriğini açıklar.  
  
 Ancak <xref:System.Windows.Media.DrawingContext> çizim yöntemleri çizim yöntemlere benzer görünür <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü, bunlar gerçekten çok farklı. <xref:System.Windows.Media.DrawingContext> olan bir saklama modu grafik sistemi ile kullanıldığında, while <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü, bir anlık mod grafik sistemiyle kullanılır. Kullandığınızda, bir <xref:System.Windows.Media.DrawingContext> nesnesinin çizme komutları, aslında bir dizi işleme yönergeleri depoladığını (tam depolama mekanizması sağlayan nesne türüne bağlı olsa da <xref:System.Windows.Media.DrawingContext>) daha sonra kullanılacak olan grafik tarafından sistem; gerçek zamanlı ekranda çizim değil. Windows Presentation Foundation (WPF) grafik sisteminin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [WPF Grafik işlemeye genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Hiçbir zaman doğrudan örneği bir <xref:System.Windows.Media.DrawingContext>; belirli yöntemlerini çizim bağlamı gibi ancak elde edebilir <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Görselin içeriklerini numaralandırma  
 Diğer kullanımları, ek olarak <xref:System.Windows.Media.Drawing> nesneleri ayrıca içeriğini numaralandırma için nesne modeli sağlar bir <xref:System.Windows.Media.Visual>.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> alınacak yöntemi <xref:System.Windows.Media.DrawingGroup> değerini bir <xref:System.Windows.Media.Visual> ve onu numaralandırır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)

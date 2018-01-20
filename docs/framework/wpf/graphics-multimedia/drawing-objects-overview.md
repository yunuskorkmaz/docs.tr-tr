---
title: "Çizim Nesnelerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9b77b47a3f3ade27f2ba86304b1868a8d388482
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="drawing-objects-overview"></a>Çizim Nesnelerine Genel Bakış
Bu konu tanıtır <xref:System.Windows.Media.Drawing> nesnelerini ve bunların şekiller, bit eşlemler, metin ve medya verimli bir şekilde çizmek için nasıl kullanılacağını açıklar. Kullanmak <xref:System.Windows.Media.Drawing> küçük resim oluşturduğunuzda nesneleri boyamak ile bir <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.Visual> nesneleri.  
  
 
  
<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Çizim nesnesi nedir?  
 A <xref:System.Windows.Media.Drawing> nesne gibi bir şekil, bit eşlem, görüntü veya metin satırının görünür içeriği açıklar. Farklı türde çizimler farklı içerik türlerini açıklar. Çizim nesneleri farklı türlerinin bir listesi verilmiştir.  
  
-   <xref:System.Windows.Media.GeometryDrawing>Şekil çizer.  
  
-   <xref:System.Windows.Media.ImageDrawing>Resim çizer.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>Metin çizer.  
  
-   <xref:System.Windows.Media.VideoDrawing>– Bir ses veya video dosyası çalar.  
  
-   <xref:System.Windows.Media.DrawingGroup>Diğer çizimleri çizer. Diğer tek bileşik çizim çizimlerini birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.Drawing>nesneleri yönlüdür; kullanabileceğiniz birçok yolu bir <xref:System.Windows.Media.Drawing> nesnesi.  
  
-   Kullanarak, bir görüntü olarak görüntüleyebilirsiniz bir <xref:System.Windows.Media.DrawingImage> ve bir <xref:System.Windows.Controls.Image> denetim.  
  
-   İle kullanabileceğiniz bir <xref:System.Windows.Media.DrawingBrush> gibi bir nesneyi boyamak için <xref:System.Windows.Controls.Page.Background%2A> , bir <xref:System.Windows.Controls.Page>.  
  
-   Görünümünü tanımlamak için kullanabileceğiniz bir <xref:System.Windows.Media.DrawingVisual>.  
  
-   İçeriğini Numaralandırılacak kullanmak bir <xref:System.Windows.Media.Visual>.  
  
 WPF diğer çizim şekil, bit eşlemler, metin ve medya özellikli nesne türlerini sağlar. Örneğin, ayrıca kullanabileceğiniz <xref:System.Windows.Shapes.Shape> şekiller çizmek için nesneleri ve <xref:System.Windows.Controls.MediaElement> denetimi video uygulamanıza eklemek için başka bir yol sağlar. Bu nedenle ne zaman kullanmalısınız <xref:System.Windows.Media.Drawing> nesneleri? Çerçeve düzeyi özelliklerinin performans avantajı kazanması için feda veya ne zaman gereksinim duyduğunuz <xref:System.Windows.Freezable> özellikleri. Çünkü <xref:System.Windows.Media.Drawing> nesneler için destek yetersizliği [düzeni](../../../../docs/framework/wpf/advanced/layout.md)giriş ve odak ile alt düzey çizimi ve arka planlar, küçük resim açıklayan için ideal hale performans avantajı sağladıkları <xref:System.Windows.Media.Visual> nesneleri.  
  
 Bir tür olduğundan <xref:System.Windows.Freezable> nesnesi <xref:System.Windows.Media.Drawing> nesneleri geçirmesine aşağıdakiler dahil çeşitli özel özellikler: olarak bildirilebilir [kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)artırmak için salt okunur yapılan birden fazla nesne arasında paylaşılan performans, kopyalanabilen ve iş parçacığı yapılan. Tarafından sağlanan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Bir şekil çizme  
 Bir şekil çizmek için kullandığınız bir <xref:System.Windows.Media.GeometryDrawing>. Geometri çiziminin <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> özelliği çizmek için Şekil açıklar kendi <xref:System.Windows.Media.GeometryDrawing.Brush%2A> özelliği açıklar nasıl şeklin iç boyandığında ve kendi <xref:System.Windows.Media.GeometryDrawing.Pen%2A> özelliği anahattı nasıl çizileceğini açıklar.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.GeometryDrawing> bir şekil çizmek için. Şeklin tarafından açıklanan bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesneleri. Şeklin iç ile boyanır bir <xref:System.Windows.Media.LinearGradientBrush> ve anahattı ile çizilmiş bir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.  
  
 Bu örnekte aşağıdaki oluşturur <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![İki elips GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Tam bir örnek için bkz: [GeometryDrawing Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-geometrydrawing.md).  
  
 Diğer <xref:System.Windows.Media.Geometry> gibi sınıfları <xref:System.Windows.Media.PathGeometry> eğriler ve yaylar oluşturarak daha karmaşık şekiller oluşturmanızı sağlar. Hakkında daha fazla bilgi için <xref:System.Windows.Media.Geometry> nesneleri bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Kullanmayan şekiller çizmek için diğer yolları hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [şekilleri ve WPF genel bakış temel çizim](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Resim çizme  
 Resim çizmek için kullandığınız bir <xref:System.Windows.Media.ImageDrawing>. Bir <xref:System.Windows.Media.ImageDrawing> nesnenin <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> özelliği çizmek için görüntü açıklar ve kendi <xref:System.Windows.Media.ImageDrawing.Rect%2A> özelliği görüntünün nerede çizilmez bölge tanımlar.  
  
 Aşağıdaki örnek (75,75) bulunan bir dikdörtgen içine bir resim çizer yani 100 x 100 piksel. Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.ImageDrawing> örnek tarafından oluşturuldu. Gri kenarlık sınırları göstermek için eklendi <xref:System.Windows.Media.ImageDrawing>.  
  
 ![Tarafından 100 100 adresindeki çizilmiş ImageDrawing &#40; 75,75 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 x 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Görüntüleri hakkında daha fazla bilgi için bkz: [Imaging genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Yürütme Ortamı (yalnızca kodu)  
  
> [!NOTE]
>  Bildirebilirsiniz rağmen bir <xref:System.Windows.Media.VideoDrawing> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], yalnızca kod kullanarak kendi medyayı yükleyebilir ve yürütebilirsiniz. Video yürütmek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullanan bir <xref:System.Windows.Controls.MediaElement> yerine.  
  
 Bir ses veya video dosyasını oynatmak için kullandığınız bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer>. Yük ve medya yürütmek için iki yolu vardır. İlk kullanmaktır bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> kendilerini ve ikinci yolu kendi oluşturmaktır <xref:System.Windows.Media.MediaTimeline> ile kullanılacak <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Bir görüntü gibi medyayı uygulamanız ile dağıtırken, bir medya dosyasını proje kaynağı olarak kullanamazsınız. Proje dosyanızda, bunun yerine medya türü ayarlamalısınız `Content` ve `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.  
  
 Kendi oluşturmadan medyayı yürütmek için <xref:System.Windows.Media.MediaTimeline>, aşağıdaki adımları gerçekleştirin.  
  
1.  Oluşturma bir <xref:System.Windows.Media.MediaPlayer> nesnesi.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2.  Kullanım <xref:System.Windows.Media.MediaPlayer.Open%2A> medya dosyasını yüklemek için yöntem.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3.  Oluşturma bir <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4.  Boyut ve ayarlayarak medyayı çizmek için konum belirtin <xref:System.Windows.Media.VideoDrawing.Rect%2A> özelliği <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5.  Ayarlama <xref:System.Windows.Media.VideoDrawing.Player%2A> özelliği <xref:System.Windows.Media.VideoDrawing> ile <xref:System.Windows.Media.MediaPlayer> oluşturduğunuz.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6.  Kullanım <xref:System.Windows.Media.MediaPlayer.Play%2A> yöntemi <xref:System.Windows.Media.MediaPlayer> media çalma başlatmak için.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> bir video dosyası bir kez oynatmak için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetim kazanmak için bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleri. <xref:System.Windows.Media.MediaTimeline> Video yinelenmesi gerektiğini belirtmenize olanak sağlar. Kullanılacak bir <xref:System.Windows.Media.MediaTimeline> ile bir <xref:System.Windows.Media.VideoDrawing>, aşağıdaki adımları gerçekleştirin:  
  
1.  Bildirme <xref:System.Windows.Media.MediaTimeline> ve zamanlama davranışlarını ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2.  Oluşturma bir <xref:System.Windows.Media.MediaClock> gelen <xref:System.Windows.Media.MediaTimeline>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3.  Oluşturma bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.MediaClock> ayarlamak için kendi <xref:System.Windows.Media.MediaPlayer.Clock%2A> özelliği.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4.  Oluşturma bir <xref:System.Windows.Media.VideoDrawing> ve Ata <xref:System.Windows.Media.MediaPlayer> için <xref:System.Windows.Media.VideoDrawing.Player%2A> özelliği <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.MediaTimeline> ile bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> art arda çalmasına.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Kullandığınızda, Not bir <xref:System.Windows.Media.MediaTimeline>, etkileşimli kullandığınız <xref:System.Windows.Media.Animation.ClockController> döndürülen <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.MediaClock> etkileşimli yöntemlerinin yerine medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.MediaPlayer>.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Metin çizme  
 Metin çizmek için kullandığınız bir <xref:System.Windows.Media.GlyphRunDrawing> ve <xref:System.Windows.Media.GlyphRun>. Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.GlyphRunDrawing> "Hello World" metninin çizmek için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumları ve yazdırma senaryoları kullanmaya yönelik bir alt düzey nesnesidir. Metin ekranına çizmek için daha basit bir şekilde kullanmaktır bir <xref:System.Windows.Controls.Label> veya <xref:System.Windows.Controls.TextBlock>. Hakkında daha fazla bilgi için <xref:System.Windows.Media.GlyphRun>, bkz: [GlyphRun Nesnesi ve karakter öğesine giriş](../../../../docs/framework/wpf/advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) genel bakış.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Bileşik çizimler  
 A <xref:System.Windows.Media.DrawingGroup> birden çok çizimi tek bileşik çizimde birleştirmenizi sağlar. Kullanarak bir <xref:System.Windows.Media.DrawingGroup>, tek bir şekil, görüntüler ve metinler birleştirebilirsiniz <xref:System.Windows.Media.Drawing> nesnesi.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingGroup> iki birleştirmek için <xref:System.Windows.Media.GeometryDrawing> nesneleri ve bir <xref:System.Windows.Media.ImageDrawing> nesnesi. Bu örnek şu çıkışı üretir.  
  
 ![Birden çok çizimler DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Bileşik çizim  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> ayrıca geçirgenlik maskeleri, dönüşümler, bit eşlem efektleri ve diğer işlemleri içeriğine uygulamanızı sağlar. <xref:System.Windows.Media.DrawingGroup>işlem, şu sırayla uygulanır: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>ve ardından <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Aşağıdaki çizimde sırayı gösterir <xref:System.Windows.Media.DrawingGroup> işlemler uygulanır.  
  
 ![DrawingGroup işlem sırası](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlem sırası  
  
 İşlemek için kullanabileceğiniz özellikler aşağıdaki tabloda açıklanmaktadır bir <xref:System.Windows.Media.DrawingGroup> nesnenin içeriği.  
  
|Özellik|Açıklama|Çizim|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|Seçili bölümlerini geçirgenliğini değiştirir <xref:System.Windows.Media.DrawingGroup> içeriği. Bir örnek için bkz: [nasıl yapılır: çizim geçirgenliğini kontrol](http://msdn.microsoft.com/library/68580652-7d32-4d27-93cc-a5148cf4d5ee).|![Geçirgenlik maskesi olan DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Aynı şekilde saydamlığını değiştirir <xref:System.Windows.Media.DrawingGroup> içeriği. Yapmak için bu özelliği kullanmak bir <xref:System.Windows.Media.Drawing> saydam veya kısmen saydam. Bir örnek için bkz: [nasıl yapılır: Çizime Geçirgenlik maskesi uygulama](http://msdn.microsoft.com/library/d77b420b-9be2-479c-a45e-82f4da30eb9f).|![Farklı geçirgenlik ayarları DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|Geçerli bir <xref:System.Windows.Media.Effects.BitmapEffect> için <xref:System.Windows.Media.DrawingGroup> içeriği. Bir örnek için bkz: [nasıl yapılır: çizime BitmapEffect uygulama](http://msdn.microsoft.com/library/c5b1de83-8d09-47fb-96db-5f174471f4b5).|![BlurBitmapEffect DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|Küçük resimleri <xref:System.Windows.Media.DrawingGroup> bir bölgeye içeriğini açıklayan kullanarak bir <xref:System.Windows.Media.Geometry>. Bir örnek için bkz: [nasıl yapılır: çizim küçük](http://msdn.microsoft.com/library/1f7d8a2c-c3c2-42cb-a542-e6796f9fb058) .|![Tanımlanan kırpma bölgesinin DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Belirtilen yönergeleriyle birlikte aygıt piksel aygıt bağımsız pikselleri tutturur. Bu özellik, ayrıntılı grafiklerinin düşük DPI ekranlarda keskin işlemeyi sağlamak için yararlıdır. Bir örnek için bkz: [çizime GuidelineSet uygulama](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-a-guidelineset-to-a-drawing.md).|![İle ve GuidelineSet olmadan DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|Dönüşümleri <xref:System.Windows.Media.DrawingGroup> içeriği. Bir örnek için bkz: [nasıl yapılır: bir dönüşüm çizime uygulama](http://msdn.microsoft.com/library/0d525f2b-682d-4d67-9660-cf46929fbabd).|![A Döndürülmüş DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Çizim bir resim olarak görüntüleme  
 Görüntülenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Controls.Image> denetlemek, kullanın bir <xref:System.Windows.Media.DrawingImage> olarak <xref:System.Windows.Controls.Image> denetimin <xref:System.Windows.Controls.Image.Source%2A> ve ayarlayın <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> görüntülemek istediğiniz çizime özelliği.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingImage> ve bir <xref:System.Windows.Controls.Image> denetiminin görüntülemek için bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek şu çıkışı üretir.  
  
 ![İki elips GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Nesneyi çizim ile Boyama  
 A <xref:System.Windows.Media.DrawingBrush> çizim nesnesi ile bir alanı boyar fırça türüdür. Çizim ile neredeyse tüm grafik nesnesini boyamak için kullanabilirsiniz. <xref:System.Windows.Media.Drawing> Özelliği bir <xref:System.Windows.Media.DrawingBrush> açıklar kendi <xref:System.Windows.Media.DrawingBrush.Drawing%2A>. İşlenecek bir <xref:System.Windows.Media.Drawing> ile bir <xref:System.Windows.Media.DrawingBrush>, fırça kullanma fırça eklemek <xref:System.Windows.Media.Drawing> özelliği ve, nesne gibi bir denetim veya panel kullanımı bir grafik boyamak için fırça.  
  
 Aşağıdaki örnekler kullanan bir <xref:System.Windows.Media.DrawingBrush> boyamak için <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> oluşturulan bir desen ile bir <xref:System.Windows.Media.GeometryDrawing>. Bu örnek şu çıkışı üretir.  
  
 ![A DrawingBrush döşeli](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush ile kullanılan GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> Sınıfı, çeşitli uzatma ve içeriği döşeme için seçenekler sağlar. Hakkında daha fazla bilgi için <xref:System.Windows.Media.DrawingBrush>, bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md) genel bakış.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Visual ile çizimi işleme  
 A <xref:System.Windows.Media.DrawingVisual> çizimi işlemek için tasarlanmış görsel nesne türüdür. Çalışma visual katmanında doğrudan üst düzeyde özelleştirilmiş bir grafik ortamı oluşturmak ve bu genel bakışta açıklanmayan geliştiriciler için bir seçenektir. Daha fazla bilgi için bkz: [kullanarak DrawingVisual nesneleri](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md) genel bakış.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext Objects  
 <xref:System.Windows.Media.DrawingContext> Sınıfı sağlar, doldurmak bir <xref:System.Windows.Media.Visual> veya <xref:System.Windows.Media.Drawing> visual içeriğe sahip. Bu tür birçok alt düzey grafik nesneleri kullanın bir <xref:System.Windows.Media.DrawingContext> çünkü grafik içeriği çok verimli bir şekilde açıklar.  
  
 Ancak <xref:System.Windows.Media.DrawingContext> çizim yöntemleri için çizim yöntemlerinin benzer görünür <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü, bunlar gerçekte çok farklı. <xref:System.Windows.Media.DrawingContext>olan bir saklama modu grafik sistemi ile kullanıldığında, while <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü anlık kip grafik sistemi ile kullanılır. Kullandığınızda, bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutları, gerçekte işleme yönergeler kümesini depoluyorsanız (tam depolama mekanizması sağlayan nesne türüne göre değişir ancak <xref:System.Windows.Media.DrawingContext>) daha sonra kullanılacak grafikleri ile sistem; gerçek zamanlı ekrana çizim değil. Ne hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] grafik sistem çalıştığını görmek [WPF Grafik işleme genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 Hiçbir zaman doğrudan örneği bir <xref:System.Windows.Media.DrawingContext>; belirli yöntemlerden çizim bağlamı gibi ancak elde edebilir <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Görsel içeriğini listeleme  
 Diğer kullanımları, ek olarak <xref:System.Windows.Media.Drawing> nesnelerini ayrıca içeriğini numaralandırmak için nesne modeli sağlar bir <xref:System.Windows.Media.Visual>.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> alma yöntemi <xref:System.Windows.Media.DrawingGroup> değerini bir <xref:System.Windows.Media.Visual> ve onu numaralandırır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/drawings-how-to-topics.md)

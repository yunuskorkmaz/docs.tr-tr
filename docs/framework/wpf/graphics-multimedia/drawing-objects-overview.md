---
title: Çizim Nesnelerine Genel Bakış
description: Nesneleri ve Windows Presentation Foundation (WPF) içinde şekilleri, bit eşlemleri, metni ve medyayı etkin bir şekilde çizmek için bunları nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- ImageDrawing objects [WPF]
- GlyphRunDrawing objects [WPF]
- GeometryDrawing objects [WPF]
- drawings [WPF], about drawings
- Drawing objects [WPF]
- DrawingGroup objects [WPF]
ms.assetid: 9b5ce5c0-e204-4320-a7a8-0b2210d62f88
ms.openlocfilehash: f00a59cd6e799e57f238c5f9b72ecc48e8445475
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853839"
---
# <a name="drawing-objects-overview"></a>Çizim Nesnelerine Genel Bakış
Bu konu <xref:System.Windows.Media.Drawing> , nesneleri tanıtır ve bunları etkin şekilde şekiller, bit eşlemler, metin ve medya çizmek için nasıl kullanacağınızı açıklar. <xref:System.Windows.Media.Drawing>Küçük resim oluştururken, bir ile boyadığınızda <xref:System.Windows.Media.DrawingBrush> veya nesneleri kullandığınızda nesneleri kullanın <xref:System.Windows.Media.Visual> .  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Çizim nesnesi nedir?  
 Bir <xref:System.Windows.Media.Drawing> nesne, şekil, bit eşlem, video veya metin satırı gibi görünür içerikleri açıklar. Farklı türdeki çizimler farklı içerik türlerini anlatmaktadır. Aşağıda, çizim nesnelerinin farklı türlerinin bir listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>– Bir resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing>– Bir ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup>– Diğer çizimleri çizer. Diğer çizimleri tek bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.Drawing>nesneler çok yönlüdür; bir nesne kullanmanın birçok yolu vardır <xref:System.Windows.Media.Drawing> .  
  
- Bir ve denetimi kullanarak bir görüntü olarak görüntüleyebilirsiniz <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> .  
  
- Bir nesnesi gibi bir <xref:System.Windows.Media.DrawingBrush> nesneyi boyamak için ile kullanabilirsiniz <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page> .  
  
- Görünümünü anlatmak için kullanabilirsiniz <xref:System.Windows.Media.DrawingVisual> .  
  
- Bunun içeriğini numaralandırmak için kullanabilirsiniz <xref:System.Windows.Media.Visual> .  
  
 WPF, şekiller, bit eşlemler, metin ve medya çizme yeteneğine sahip olan diğer nesne türlerini sağlar. Örneğin, <xref:System.Windows.Shapes.Shape> şekiller çizmek için nesneleri de kullanabilirsiniz ve <xref:System.Windows.Controls.MediaElement> Denetim uygulamanıza video eklemek için başka bir yol sağlar. Bu nedenle, nesneleri ne zaman kullanmanız gerekir <xref:System.Windows.Media.Drawing> ? Performans avantajları elde etmek veya özelliklere ihtiyaç duyduğunuzda çerçeve düzeyindeki özellikleri feda edebilirsiniz <xref:System.Windows.Freezable> . <xref:System.Windows.Media.Drawing>Nesneler [Düzen](../advanced/layout.md), giriş ve odak için destek olmadığından, bunları arka planları, klip resimlerini ve nesnelerle alt düzey çizim için ideal hale getirir <xref:System.Windows.Media.Visual> .  
  
 Nesneler bir tür nesnesi olduklarından, <xref:System.Windows.Freezable> <xref:System.Windows.Media.Drawing> aşağıdakiler dahil olmak üzere birkaç özel özellik elde ederler: Bunlar, [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak, birden fazla nesne arasında paylaşılan, performansı artırmak için salt okuma, klonlanmış ve iş parçacığı açısından güvenli hale getirilebilir. Nesneler tarafından sunulan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Şekil çiz  
 Bir şekil çizmek için bir kullanabilirsiniz <xref:System.Windows.Media.GeometryDrawing> . Geometri çiziminin <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> özelliği, çizilecek şekli açıklar, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> özelliği şeklin iç kısmının nasıl boyanması gerektiğini ve <xref:System.Windows.Media.GeometryDrawing.Pen%2A> özelliği, anahattının nasıl çizildiğini açıklar.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Media.GeometryDrawing> şekil çizmek için kullanır. Şekil, <xref:System.Windows.Media.GeometryGroup> ve iki nesne tarafından tanımlanır <xref:System.Windows.Media.EllipseGeometry> . Şeklin iç kısmı ile boyanmıştır <xref:System.Windows.Media.LinearGradientBrush> ve ana hattı ile çizilir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> .  
  
 Bu örnekte aşağıdakiler oluşturulur <xref:System.Windows.Media.GeometryDrawing> .  
  
 ![İki elips için GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Tüm örnek için bkz. [GeometryDrawing oluşturma](how-to-create-a-geometrydrawing.md).  
  
 Gibi diğer <xref:System.Windows.Media.Geometry> sınıflar, <xref:System.Windows.Media.PathGeometry> eğri ve yay oluşturarak daha karmaşık şekiller oluşturmanızı sağlar. Nesneler hakkında daha fazla bilgi için <xref:System.Windows.Media.Geometry> bkz. [geometriye genel bakış](geometry-overview.md).  
  
 Nesneleri kullanmayan şekiller çizmenin diğer yolları hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> bkz. [WPF 'de şekillere ve temel çizime genel bakış](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Görüntü çizme  
 Bir görüntü çizmek için bir kullanabilirsiniz <xref:System.Windows.Media.ImageDrawing> . Bir <xref:System.Windows.Media.ImageDrawing> nesnenin <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> özelliği, çizilecek görüntüyü tanımlar ve <xref:System.Windows.Media.ImageDrawing.Rect%2A> özelliği görüntünün çizildiği bölgeyi tanımlar.  
  
 Aşağıdaki örnek, (75, 75) konumunda bulunan bir dikdörtgene bir resim çizer ve 100 piksel 100 piksel. Aşağıdaki çizimde <xref:System.Windows.Media.ImageDrawing> örnek tarafından oluşturulan gösterilmektedir. Sınırlarını göstermek için gri bir kenarlık eklenmiştir <xref:System.Windows.Media.ImageDrawing> .  
  
 ![&#40;75, 75&#41;çizilmiş bir 100 x 100 ImageDrawing](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 ile 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Görüntüler hakkında daha fazla bilgi için bkz. [görüntülemeye genel bakış](imaging-overview.md).  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Medyayı oynat (yalnızca kod)  
  
> [!NOTE]
> Bir içinde bildirebilseniz de <xref:System.Windows.Media.VideoDrawing> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , yalnızca kodu kullanarak medyayı yükleyebilir ve oynatabilirsiniz. Videoyu oynatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , <xref:System.Windows.Controls.MediaElement> bunun yerine bir kullanın.  
  
 Ses veya video dosyası oynatmak için bir <xref:System.Windows.Media.VideoDrawing> ve kullanın <xref:System.Windows.Media.MediaPlayer> . Medyayı yüklemek ve oynatmak için kullanabileceğiniz iki yol vardır. Birincisi, ve ' ı kendi <xref:System.Windows.Media.MediaPlayer> başlarına ve <xref:System.Windows.Media.VideoDrawing> ikinci şekilde, <xref:System.Windows.Media.MediaTimeline> ve ile kullanmak için kendi oluşturmanız gerekir <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> .  
  
> [!NOTE]
> Medyayı uygulamanızla dağıtırken, bir görüntü gibi bir proje kaynağı olarak bir medya dosyası kullanamazsınız. Proje dosyanızda, bunun yerine medya türünü olarak ayarlamanız `Content` ve ya da olarak ayarlamanız gerekir `CopyToOutputDirectory` `PreserveNewest` `Always` .  
  
 Medyayı kendi oluşturmaksızın yürütmek için <xref:System.Windows.Media.MediaTimeline> aşağıdaki adımları gerçekleştirirsiniz.  
  
1. Bir <xref:System.Windows.Media.MediaPlayer> nesne oluşturun.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaPlayer.Open%2A>Ortam dosyasını yüklemek için yöntemini kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Oluşturun <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Öğesinin özelliğini ayarlayarak medyanın çizileceği boyut ve konumu belirtin <xref:System.Windows.Media.VideoDrawing.Rect%2A> <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. <xref:System.Windows.Media.VideoDrawing.Player%2A>Öğesinin özelliğini <xref:System.Windows.Media.VideoDrawing> oluşturduğunuz ile ayarlayın <xref:System.Windows.Media.MediaPlayer> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. <xref:System.Windows.Media.MediaPlayer.Play%2A> <xref:System.Windows.Media.MediaPlayer> Ortamını yürütmeye başlamak için yöntemini kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> video dosyasını bir kez çalmak için bir ve bir kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetimi kazanmak için, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> ve nesneleriyle bir kullanın <xref:System.Windows.Media.VideoDrawing> . <xref:System.Windows.Media.MediaTimeline>Videonun yinelenmesi gerekip gerekmediğini belirtmenizi sağlar. <xref:System.Windows.Media.MediaTimeline>İle ile kullanmak için <xref:System.Windows.Media.VideoDrawing> aşağıdaki adımları gerçekleştirirsiniz:  
  
1. <xref:System.Windows.Media.MediaTimeline>' İ bildirin ve zamanlama davranışlarını ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. İçinden bir oluşturun <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Media.MediaTimeline> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Oluşturun <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.MediaClock> özelliğini ayarlamak için öğesini kullanın <xref:System.Windows.Media.MediaPlayer.Clock%2A> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. ' A oluşturun <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> özelliğine atayın <xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing> .  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> videoyu art arda çalmak için ile ve ile kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 ' I kullandığınızda, <xref:System.Windows.Media.MediaTimeline> ' ın özelliğinden döndürülen etkileşimli öğesini, <xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.Clock.Controller%2A> <xref:System.Windows.Media.MediaClock> uygulamasının etkileşimli yöntemleri yerine medya kayıttan yürütmeyi denetlemek için kullanacağınızı unutmayın <xref:System.Windows.Media.MediaPlayer> .  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Metin çiz  
 Metin çizmek için bir <xref:System.Windows.Media.GlyphRunDrawing> ve kullanın <xref:System.Windows.Media.GlyphRun> . Aşağıdaki örnek, <xref:System.Windows.Media.GlyphRunDrawing> "Merhaba Dünya" metnini çizmek için bir kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun>, Sabit biçimli belge sunumu ve yazdırma senaryolarında kullanılması amaçlanan alt düzey bir nesnedir. Ekrana metin çizmenin daha basit bir yolu bir <xref:System.Windows.Controls.Label> veya bir kullanmaktır <xref:System.Windows.Controls.TextBlock> . Hakkında daha fazla bilgi için <xref:System.Windows.Media.GlyphRun> , [GlyphRun nesne ve Glifler öğesine](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) genel bakış konusuna bakın.  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Bileşik çizimler  
 <xref:System.Windows.Media.DrawingGroup>, Birden çok çizimi tek bir bileşik çizimde birleştirmenizi sağlar. Bir kullanarak <xref:System.Windows.Media.DrawingGroup> şekilleri, resimleri ve metni tek bir nesne içinde birleştirebilirsiniz <xref:System.Windows.Media.Drawing> .  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.DrawingGroup> iki <xref:System.Windows.Media.GeometryDrawing> nesneyi ve bir nesneyi birleştirmek için bir kullanır <xref:System.Windows.Media.ImageDrawing> . Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Birden çok çizimle bir DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Bileşik çizim  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup>Ayrıca, içerik için opaklık maskeleri, dönüşümler, bit eşlem efektleri ve diğer işlemleri uygulamanıza olanak sağlar. <xref:System.Windows.Media.DrawingGroup>işlemler şu sırayla uygulanır: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> , <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ,, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> , <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> ve <xref:System.Windows.Media.DrawingGroup.Transform%2A> .  
  
 Aşağıdaki çizimde, <xref:System.Windows.Media.DrawingGroup> işlemlerin uygulanma sırası gösterilmektedir.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemleri sırası  
  
 Aşağıdaki tabloda, bir nesnenin içeriğini işlemek için kullanabileceğiniz özellikler açıklanmaktadır <xref:System.Windows.Media.DrawingGroup> .  
  
|Özellik|Açıklama|Göstermektedir|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|İçeriğin seçili bölümlerinin saydamlığını değiştirir <xref:System.Windows.Media.DrawingGroup> . Bir örnek için bkz. [nasıl yapılır: çizimin saydamlığını denetleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Opaklık maskesi olan bir DrawingGroup](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|İçeriğin opaklığını tek tek değiştirir <xref:System.Windows.Media.DrawingGroup> . Saydam veya kısmen saydam hale getirmek için bu özelliği kullanın <xref:System.Windows.Media.Drawing> . Bir örnek için bkz. [nasıl yapılır: bir çizime opaklık maskesi uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Farklı opaklık ayarlarına sahip DrawingGroups](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|İçeriğe bir uygular <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Media.DrawingGroup> . Bir örnek için bkz. [nasıl yapılır: bir çizime BitmapEffect uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![BlurBitmapEffect ile DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|İçeriğini, <xref:System.Windows.Media.DrawingGroup> kullanarak betimleyen bir bölgeye kırpar <xref:System.Windows.Media.Geometry> . Bir örnek için bkz. [nasıl yapılır: çizimi kırpma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Tanımlı bir klip bölgesi olan DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Cihaz bağımsız piksellerini belirtilen yönergeleriyle cihaz pikselleriyle yaslar. Bu özellik, ayrıntılı grafiklerin düşük DPı ekranlarda keskin şekilde işlemesini sağlamak için yararlıdır. Bir örnek için bkz. [çizime bir kılavuz çizgisi kümesi uygulama](how-to-apply-a-guidelineset-to-a-drawing.md).|![Kılavuz çizgisi kümesi olmayan bir DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|İçeriği dönüştürür <xref:System.Windows.Media.DrawingGroup> . Bir örnek için bkz. [nasıl yapılır: çizime dönüşüm uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Döndürülmüş bir DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Çizimi resim olarak görüntüleme  
 Bir <xref:System.Windows.Media.Drawing> denetimi ile birlikte göstermek için <xref:System.Windows.Controls.Image> , <xref:System.Windows.Media.DrawingImage> Denetim olarak bir kullanın <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Image.Source%2A> ve <xref:System.Windows.Media.DrawingImage> nesnenin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> özelliğini, göstermek istediğiniz çizim olarak ayarlayın.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> denetimini göstermek için bir ve denetimi kullanır <xref:System.Windows.Media.GeometryDrawing> . Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![İki elips için GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Bir DrawingImage desteklenir  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Çizim ile nesne boyama  
 <xref:System.Windows.Media.DrawingBrush>, Çizim nesnesi ile bir alanı boyayan bir fırça türüdür. Çizim ile herhangi bir grafik nesnesini boyamak için kullanabilirsiniz. <xref:System.Windows.Media.Drawing>Öğesinin özelliği, öğesini <xref:System.Windows.Media.DrawingBrush> açıklar <xref:System.Windows.Media.DrawingBrush.Drawing%2A> . A <xref:System.Windows.Media.Drawing> ile birlikte işlemek için <xref:System.Windows.Media.DrawingBrush> fırçanın özelliğini kullanarak fırçaya ekleyin <xref:System.Windows.Media.Drawing> ve bir denetim veya panel gibi bir grafik nesnesini boyamak için fırçayı kullanın.  
  
 Aşağıdaki örnekler, a ' <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Shapes.Shape.Fill%2A> dan oluşturulan bir desenli bir ile boyamak için bir kullanır <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.GeometryDrawing> . Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Döşeli bir DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush ile kullanılan GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush>Sınıfı, içeriğini uzatma ve döşeme için çeşitli seçenekler sağlar. Hakkında daha fazla bilgi için <xref:System.Windows.Media.DrawingBrush> bkz. [görüntü, çizim ve görsellere](painting-with-images-drawings-and-visuals.md) genel bakış.  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Görsel ile çizim işleme  
 <xref:System.Windows.Media.DrawingVisual>, Bir çizimi işlemek için tasarlanan bir görsel nesne türüdür. Doğrudan görsel katmanda çalışmak, yüksek düzeyde özelleştirilmiş bir grafik ortamı oluşturmak isteyen geliştiriciler için bir seçenektir ve bu genel bakışta açıklanmamaktadır. Daha fazla bilgi için bkz. [DrawingVisual Objects 'ı kullanma](using-drawingvisual-objects.md) genel bakış.  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>DrawingContext nesneleri  
 <xref:System.Windows.Media.DrawingContext>Sınıfı, bir <xref:System.Windows.Media.Visual> veya öğesini görsel içerikle doldurmanıza olanak sağlar <xref:System.Windows.Media.Drawing> . Birçok alt düzey grafik nesnesi, <xref:System.Windows.Media.DrawingContext> grafik içeriğini çok verimli bir şekilde açıkladığı için bir kullanır.  
  
 <xref:System.Windows.Media.DrawingContext>Çizim yöntemleri türdeki Çizim yöntemlerine benzer görünse de <xref:System.Drawing.Graphics?displayProperty=nameWithType> , aslında çok farklıdır. <xref:System.Windows.Media.DrawingContext>, <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü bir anlık mod grafik sistemiyle kullanıldığı sırada bir tutulan mod grafik sistemiyle kullanılır. Bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlarını kullandığınızda, aslında bir dizi işleme yönergesi depoluyorsanız (tam depolama mekanizması, <xref:System.Windows.Media.DrawingContext> daha sonra grafik sistemi tarafından kullanılacak olan nesne türüne bağlıdır) ve ekrana gerçek zamanlı olarak çizmeyin. Windows Presentation Foundation (WPF) grafik sisteminin nasıl çalıştığı hakkında daha fazla bilgi için [WPF Grafik Işlemeye genel bakış ' a](wpf-graphics-rendering-overview.md)bakın.  
  
 Hiçbir şekilde doğrudan örnekleyemezsiniz <xref:System.Windows.Media.DrawingContext> ; ancak, ve gibi belirli yöntemlerden bir çizim bağlamı elde edebilirsiniz <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType> .  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Görselin Içeriğini listeleme  
 Diğer kullanımlarına ek olarak, <xref:System.Windows.Media.Drawing> nesneleri de içeriğini numaralandırmak için bir nesne modeli sağlar <xref:System.Windows.Media.Visual> .  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> değerini almak ve numaralandırmak için yöntemini kullanır <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Visual> .  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Nasıl Yapılır Konuları](drawings-how-to-topics.md)

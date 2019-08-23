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
ms.openlocfilehash: d739865a692fa5ef448eba91369015580e5eda97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916307"
---
# <a name="drawing-objects-overview"></a>Çizim Nesnelerine Genel Bakış
Bu konu, <xref:System.Windows.Media.Drawing> nesneleri tanıtır ve bunları etkin şekilde şekiller, bit eşlemler, metin ve medya çizmek için nasıl kullanacağınızı açıklar. Küçük <xref:System.Windows.Media.Drawing> resim oluştururken, bir <xref:System.Windows.Media.DrawingBrush>ile boyadığınızda veya nesneleri kullandığınızda <xref:System.Windows.Media.Visual> nesneleri kullanın.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Çizim nesnesi nedir?  
 Bir <xref:System.Windows.Media.Drawing> nesne, şekil, bit eşlem, video veya metin satırı gibi görünür içerikleri açıklar. Farklı türdeki çizimler farklı içerik türlerini anlatmaktadır. Aşağıda, çizim nesnelerinin farklı türlerinin bir listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>– Bir resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing>– Bir ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup>– Diğer çizimleri çizer. Diğer çizimleri tek bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.Drawing>nesneler çok yönlüdür; bir <xref:System.Windows.Media.Drawing> nesne kullanmanın birçok yolu vardır.  
  
- <xref:System.Windows.Media.DrawingImage> Bir<xref:System.Windows.Controls.Image> ve denetimi kullanarak bir görüntü olarak görüntüleyebilirsiniz.  
  
- Bir nesnesi gibi bir nesneyi <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page>boyamak için ile kullanabilirsiniz.  
  
- Görünümünü anlatmak için kullanabilirsiniz <xref:System.Windows.Media.DrawingVisual>.  
  
- Bunun içeriğini <xref:System.Windows.Media.Visual>numaralandırmak için kullanabilirsiniz.  
  
 WPF, şekiller, bit eşlemler, metin ve medya çizme yeteneğine sahip olan diğer nesne türlerini sağlar. Örneğin, şekiller çizmek için <xref:System.Windows.Shapes.Shape> nesneleri de kullanabilirsiniz <xref:System.Windows.Controls.MediaElement> ve denetim uygulamanıza video eklemek için başka bir yol sağlar. Bu nedenle, nesneleri ne <xref:System.Windows.Media.Drawing> zaman kullanmanız gerekir? Performans avantajları elde etmek veya özelliklere ihtiyaç <xref:System.Windows.Freezable> duyduğunuzda çerçeve düzeyindeki özellikleri feda edebilirsiniz. Nesneler <xref:System.Windows.Media.Drawing> [Düzen](../advanced/layout.md), giriş ve odak için destek olmadığından, bunları arka planları, klip resimlerini ve <xref:System.Windows.Media.Visual> nesnelerle alt düzey çizim için ideal hale getirir.  
  
 <xref:System.Windows.Media.Drawing> Nesneler bir tür <xref:System.Windows.Freezable> nesnesi olduklarından, aşağıdakiler dahil olmak üzere birkaç özel özellik elde eder: Bunlar, [kaynak](../advanced/xaml-resources.md)olarak, birden çok nesne arasında paylaşılan, performansı artırmak için salt okunabilir hale getirilir ve iş parçacığı açısından güvenli hale getirilir. Nesneler tarafından <xref:System.Windows.Freezable> sunulan farklı özellikler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Şekil çiz  
 Bir şekil çizmek için bir <xref:System.Windows.Media.GeometryDrawing>kullanabilirsiniz. Geometri çiziminin <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> özelliği <xref:System.Windows.Media.GeometryDrawing.Brush%2A> , çizilecek şekli açıklar, özelliği şeklin iç kısmının nasıl <xref:System.Windows.Media.GeometryDrawing.Pen%2A> boyanması gerektiğini ve özelliği, anahattının nasıl çizildiğini açıklar.  
  
 Aşağıdaki örnek bir <xref:System.Windows.Media.GeometryDrawing> şekil çizmek için kullanır. Şekil, <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesne tarafından tanımlanır. Şeklin iç kısmı ile <xref:System.Windows.Media.LinearGradientBrush> boyanmıştır ve ana hattı <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>ile çizilir.  
  
 Bu örnekte aşağıdakiler <xref:System.Windows.Media.GeometryDrawing>oluşturulur.  
  
 ![İki elips Için GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Tüm örnek için bkz. [GeometryDrawing oluşturma](how-to-create-a-geometrydrawing.md).  
  
 Gibi <xref:System.Windows.Media.Geometry> diğer sınıflar, <xref:System.Windows.Media.PathGeometry> eğri ve yay oluşturarak daha karmaşık şekiller oluşturmanızı sağlar. Nesneler hakkında <xref:System.Windows.Media.Geometry> daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).  
  
 Nesneleri kullanmayan <xref:System.Windows.Media.Drawing> şekiller çizmenin diğer yolları hakkında daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Görüntü çizme  
 Bir görüntü çizmek için bir <xref:System.Windows.Media.ImageDrawing>kullanabilirsiniz. Bir <xref:System.Windows.Media.ImageDrawing> <xref:System.Windows.Media.ImageDrawing.Rect%2A> nesnenin özelliği, çizilecek görüntüyü tanımlar ve özelliği görüntünün çizildiği bölgeyi tanımlar. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A>  
  
 Aşağıdaki örnek, (75, 75) konumunda bulunan bir dikdörtgene bir resim çizer ve 100 piksel 100 piksel. Aşağıdaki çizimde örnek tarafından <xref:System.Windows.Media.ImageDrawing> oluşturulan gösterilmektedir. Sınırlarını göstermek için gri bir kenarlık eklenmiştir <xref:System.Windows.Media.ImageDrawing>.  
  
 ![75, 75 &#40;&#41; ve üzerinde çizilmiş bir 100 x 100 ImageDrawing](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 ile 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Görüntüler hakkında daha fazla bilgi için bkz. [görüntülemeye genel bakış](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Medyayı oynat (yalnızca kod)  
  
> [!NOTE]
> Bir <xref:System.Windows.Media.VideoDrawing> içinde[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bildirebilseniz de, yalnızca kodu kullanarak medyayı yükleyebilir ve oynatabilirsiniz. Videoyu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]oynatmak için, bunun yerine bir <xref:System.Windows.Controls.MediaElement> kullanın.  
  
 Ses veya video dosyası oynatmak için bir <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>ve kullanın. Medyayı yüklemek ve oynatmak için kullanabileceğiniz iki yol vardır. Birincisi <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>, ve ' ı kendi başlarına ve ikinci şekilde, ve ile kullanmak için kendi oluşturmanız gerekir. <xref:System.Windows.Media.VideoDrawing>  
  
> [!NOTE]
> Medyayı uygulamanızla dağıtırken, bir görüntü gibi bir proje kaynağı olarak bir medya dosyası kullanamazsınız. Proje dosyanızda, bunun yerine medya `Content` türünü olarak ayarlamanız ve ya `Always`da olarak `PreserveNewest` ayarlamanız `CopyToOutputDirectory` gerekir.  
  
 Medyayı kendi <xref:System.Windows.Media.MediaTimeline>oluşturmaksızın yürütmek için aşağıdaki adımları gerçekleştirirsiniz.  
  
1. Bir <xref:System.Windows.Media.MediaPlayer> nesne oluşturun.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Ortam dosyasını yüklemek için yönteminikullanın.<xref:System.Windows.Media.MediaPlayer.Open%2A>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Oluşturma bir <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Öğesinin özelliğini<xref:System.Windows.Media.VideoDrawing.Rect%2A> ayarlayarak medyanın çizileceği boyut ve konumu belirtin. <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. Öğesinin özelliğini oluşturduğunuz ile ayarlayın<xref:System.Windows.Media.MediaPlayer>. <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.VideoDrawing.Player%2A>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Ortamını yürütmeye başlamak <xref:System.Windows.Media.MediaPlayer> için yönteminikullanın.<xref:System.Windows.Media.MediaPlayer.Play%2A>  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Aşağıdaki örnek, bir video <xref:System.Windows.Media.VideoDrawing> dosyasını bir <xref:System.Windows.Media.MediaPlayer> kez çalmak için bir ve bir kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetimi kazanmak için, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleriyle bir kullanın. Videonun yinelenmesi gerekip gerekmediğini belirtmenizi sağlar.<xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaTimeline> İle ile kullanmak<xref:System.Windows.Media.VideoDrawing>için aşağıdaki adımları gerçekleştirirsiniz:  
  
1. <xref:System.Windows.Media.MediaTimeline> ' İ bildirin ve zamanlama davranışlarını ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. İçinden bir <xref:System.Windows.Media.MediaClock>oluşturun. <xref:System.Windows.Media.MediaTimeline>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. Oluşturun ve özelliğini ayarlamak <xref:System.Windows.Media.MediaClock> için öğesini kullanın. <xref:System.Windows.Media.MediaPlayer.Clock%2A> <xref:System.Windows.Media.MediaPlayer>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. ' A <xref:System.Windows.Media.VideoDrawing> oluşturun <xref:System.Windows.Media.VideoDrawing.Player%2A> ve özelliğine <xref:System.Windows.Media.MediaPlayer>atayın. <xref:System.Windows.Media.VideoDrawing>  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Aşağıdaki örnek, bir videoyu <xref:System.Windows.Media.MediaTimeline> art arda <xref:System.Windows.Media.MediaPlayer> çalmak <xref:System.Windows.Media.VideoDrawing> için ile ve ile kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <xref:System.Windows.Media.MediaTimeline>' I kullandığınızda, ' ın <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliğinden <xref:System.Windows.Media.MediaClock> döndürülen etkileşimli <xref:System.Windows.Media.Animation.ClockController> öğesini, uygulamasının <xref:System.Windows.Media.MediaPlayer>etkileşimli yöntemleri yerine medya kayıttan yürütmeyi denetlemek için kullanacağınızı unutmayın.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Metin çiz  
 Metin çizmek için bir <xref:System.Windows.Media.GlyphRunDrawing> <xref:System.Windows.Media.GlyphRun>ve kullanın. Aşağıdaki örnek, "Merhaba Dünya <xref:System.Windows.Media.GlyphRunDrawing> " metnini çizmek için bir kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun> , Sabit biçimli belge sunumu ve yazdırma senaryolarında kullanılması amaçlanan alt düzey bir nesnedir. Ekrana metin çizmenin daha basit bir yolu bir <xref:System.Windows.Controls.Label> veya bir <xref:System.Windows.Controls.TextBlock>kullanmaktır. Hakkında <xref:System.Windows.Media.GlyphRun>daha fazla bilgi için, [GlyphRun nesne ve Glifler öğesine](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) genel bakış konusuna bakın.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Bileşik çizimler  
 , Birden çok çizimi tek bir bileşik çizimde birleştirmenizi sağlar.<xref:System.Windows.Media.DrawingGroup> Bir <xref:System.Windows.Media.DrawingGroup>kullanarak şekilleri, resimleri ve metni tek <xref:System.Windows.Media.Drawing> bir nesne içinde birleştirebilirsiniz.  
  
 Aşağıdaki örnek, iki <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.GeometryDrawing> nesneyi ve bir <xref:System.Windows.Media.ImageDrawing> nesneyi birleştirmek için bir kullanır. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Birden çok çizimle bir DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Bileşik çizim  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup> Ayrıca, içerik için opaklık maskeleri, dönüşümler, bit eşlem efektleri ve diğer işlemleri uygulamanıza olanak sağlar. <xref:System.Windows.Media.DrawingGroup>işlemler şu sırayla uygulanır: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A> <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>,, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>ve. <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
  
 Aşağıdaki çizimde, <xref:System.Windows.Media.DrawingGroup> işlemlerin uygulanma sırası gösterilmektedir.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemleri sırası  
  
 Aşağıdaki tabloda, bir <xref:System.Windows.Media.DrawingGroup> nesnenin içeriğini işlemek için kullanabileceğiniz özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|Göstermektedir|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|<xref:System.Windows.Media.DrawingGroup> İçeriğin seçili bölümlerinin saydamlığını değiştirir. Bir örnek için bkz [. nasıl yapılır: Çizimin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))opaklığını kontrol edin.|![Opaklık maskesi olan bir DrawingGroup](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|<xref:System.Windows.Media.DrawingGroup> İçeriğin opaklığını tek tek değiştirir. <xref:System.Windows.Media.Drawing> Saydam veya kısmen saydam hale getirmek için bu özelliği kullanın. Bir örnek için bkz [. nasıl yapılır: Çizime](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))bir opaklık maskesi uygulayın.|![Farklı opaklık ayarlarına sahip Drawinggroups](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|İçeriğe<xref:System.Windows.Media.DrawingGroup> bir <xref:System.Windows.Media.Effects.BitmapEffect> uygular. Bir örnek için bkz [. nasıl yapılır: Çizime](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))bir BitmapEffect uygulayın.|![BlurBitmapEffect Ile DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|İçeriğini, <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Geometry>kullanarak betimleyen bir bölgeye kırpar. Bir örnek için bkz [. nasıl yapılır: Bir çizimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) kırpın.|![Tanımlı bir klip bölgesi olan DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Cihaz bağımsız piksellerini belirtilen yönergeleriyle cihaz pikselleriyle yaslar. Bu özellik, ayrıntılı grafiklerin düşük DPı ekranlarda keskin şekilde işlemesini sağlamak için yararlıdır. Bir örnek için bkz. [çizime bir kılavuz çizgisi kümesi uygulama](how-to-apply-a-guidelineset-to-a-drawing.md).|![Kılavuz çizgisi kümesi olmayan bir DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|<xref:System.Windows.Media.DrawingGroup> İçeriği dönüştürür. Bir örnek için bkz [. nasıl yapılır: Çizime](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))dönüşüm uygulayın.|![Döndürülmüş bir DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Çizimi resim olarak görüntüleme  
 <xref:System.Windows.Media.Drawing> Bir <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image.Source%2A> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> denetimi ile birlikte göstermek <xref:System.Windows.Media.DrawingImage> için<xref:System.Windows.Controls.Image> , denetim olarak bir kullanın ve nesnenin özelliğini, göstermek istediğiniz çizim olarak ayarlayın. <xref:System.Windows.Controls.Image>  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Controls.Image> denetimini göstermek <xref:System.Windows.Media.GeometryDrawing>için bir ve denetimi kullanır. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![İki elips Için GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Bir DrawingImage desteklenir  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Çizim ile nesne boyama  
 <xref:System.Windows.Media.DrawingBrush> , Çizim nesnesi ile bir alanı boyayan bir fırça türüdür. Çizim ile herhangi bir grafik nesnesini boyamak için kullanabilirsiniz. Öğesinin özelliği, <xref:System.Windows.Media.Drawing> öğesini <xref:System.Windows.Media.DrawingBrush.Drawing%2A>açıklar. <xref:System.Windows.Media.DrawingBrush> A <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.Drawing> ile birlikte işlemek için fırçanın özelliğini kullanarak fırçaya ekleyin ve bir denetim veya panel gibi bir grafik nesnesini boyamak için fırçayı kullanın. <xref:System.Windows.Media.DrawingBrush>  
  
 Aşağıdaki örnekler, <xref:System.Windows.Shapes.Shape.Fill%2A> a ' <xref:System.Windows.Media.DrawingBrush> dan <xref:System.Windows.Shapes.Rectangle> oluşturulan bir desenli bir ile boyamak için bir kullanır. <xref:System.Windows.Media.GeometryDrawing> Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Döşeli bir DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush ile kullanılan GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 Sınıfı <xref:System.Windows.Media.DrawingBrush> , içeriğini uzatma ve döşeme için çeşitli seçenekler sağlar. Hakkında <xref:System.Windows.Media.DrawingBrush>daha fazla bilgi için bkz. [görüntü, çizim ve görsellere](painting-with-images-drawings-and-visuals.md) genel bakış.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Görsel ile çizim işleme  
 <xref:System.Windows.Media.DrawingVisual> , Bir çizimi işlemek için tasarlanan bir görsel nesne türüdür. Doğrudan görsel katmanda çalışmak, yüksek düzeyde özelleştirilmiş bir grafik ortamı oluşturmak isteyen geliştiriciler için bir seçenektir ve bu genel bakışta açıklanmamaktadır. Daha fazla bilgi için bkz. [DrawingVisual Objects 'ı kullanma](using-drawingvisual-objects.md) genel bakış.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext nesneleri  
 Sınıfı <xref:System.Windows.Media.DrawingContext> , bir <xref:System.Windows.Media.Visual> veya <xref:System.Windows.Media.Drawing> öğesini görsel içerikle doldurmanıza olanak sağlar. Birçok alt düzey grafik nesnesi, grafik içeriğini çok <xref:System.Windows.Media.DrawingContext> verimli bir şekilde açıkladığı için bir kullanır.  
  
 Çizim yöntemleri <xref:System.Drawing.Graphics?displayProperty=nameWithType> türdeki Çizim yöntemlerine benzer görünse de, aslında çok farklıdır. <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingContext>, <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü bir anlık mod grafik sistemiyle kullanıldığı sırada bir tutulan mod grafik sistemiyle kullanılır. Bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlarını kullandığınızda, aslında bir dizi işleme yönergesi depoluyorsanız (tam depolama mekanizması, <xref:System.Windows.Media.DrawingContext>daha sonra grafik sistemi tarafından kullanılacak nesne türüne bağlıdır). gerçek zamanlı olarak ekrana çizim değildir. Windows Presentation Foundation (WPF) grafik sisteminin nasıl çalıştığı hakkında daha fazla bilgi için [WPF Grafik Işlemeye genel bakış ' a](wpf-graphics-rendering-overview.md)bakın.  
  
 Hiçbir şekilde <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> doğrudan örnekleyemezsiniz; ancak, ve <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>gibi belirli yöntemlerden bir çizim bağlamı elde edebilirsiniz.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Görselin Içeriğini listeleme  
 Diğer kullanımlarına ek olarak, <xref:System.Windows.Media.Drawing> nesneleri de içeriğini <xref:System.Windows.Media.Visual>numaralandırmak için bir nesne modeli sağlar.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> <xref:System.Windows.Media.DrawingGroup> değerini <xref:System.Windows.Media.Visual> almak ve numaralandırmak için yöntemini kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
- [Nasıl Yapılır Konuları](drawings-how-to-topics.md)

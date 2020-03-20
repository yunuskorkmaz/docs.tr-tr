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
ms.openlocfilehash: 7a5d00eb2fb7c66e5e42d40893806e13717e1d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186535"
---
# <a name="drawing-objects-overview"></a>Çizim Nesnelerine Genel Bakış
Bu konu <xref:System.Windows.Media.Drawing> nesneleri tanılar ve verimli şekiller, bit eşlemler, metin ve medya çizmek için bunları nasıl kullanılacağını açıklar. Küçük <xref:System.Windows.Media.Drawing> resim oluştururken, nesneleri <xref:System.Windows.Media.DrawingBrush>boyarken veya <xref:System.Windows.Media.Visual> nesneleri kullanırken nesneleri kullanın.  

<a name="whatisadrawingsection"></a>
## <a name="what-is-a-drawing-object"></a>Çizim Nesnesi Nedir?  
 Nesne, <xref:System.Windows.Media.Drawing> şekil, biteş, video veya metin satırı gibi görünür içeriği açıklar. Farklı çizim türleri farklı içerik türlerini açıklar. Aşağıda, farklı çizim nesnetürlerinin listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>– Bir görüntü çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing>– Ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup>– Diğer çizimleri çizer. Diğer çizimleri tek bir bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.Drawing>nesneler çok yönlüdür; bir <xref:System.Windows.Media.Drawing> nesneyi kullanmanın birçok yolu vardır.  
  
- A <xref:System.Windows.Media.DrawingImage> ve bir <xref:System.Windows.Controls.Image> denetim kullanarak görüntü olarak görüntüleyebilirsiniz.  
  
- Bir nesneyi boyamak için a <xref:System.Windows.Media.DrawingBrush> ile <xref:System.Windows.Controls.Page.Background%2A> kullanabilirsiniz, örneğin bir <xref:System.Windows.Controls.Page>.  
  
- Bir <xref:System.Windows.Media.DrawingVisual>.  
  
- Bir <xref:System.Windows.Media.Visual>.  
  
 WPF, şekil, bit eşlem, metin ve ortam çizim yeteneğine sahip diğer nesne türleri sağlar. Örneğin, şekilleri çizmek <xref:System.Windows.Shapes.Shape> için nesneleri de kullanabilirsiniz <xref:System.Windows.Controls.MediaElement> ve denetim uygulamanıza video eklemek için başka bir yol sağlar. Peki nesneleri ne <xref:System.Windows.Media.Drawing> zaman kullanmalısınız? Performans avantajları ndan yararlanmak için çerçeve düzeyindeki <xref:System.Windows.Freezable> özelliklerden ne zaman yararlanabilirsiniz veya özelliklere ihtiyacınız olduğunda. Nesneler [Düzen,](../advanced/layout.md)giriş ve odak için destek olmadığından, arka planlar, küçük resim ve nesnelerle <xref:System.Windows.Media.Visual> düşük düzeyli çizim için onları ideal hale getiren performans avantajları sağlar. <xref:System.Windows.Media.Drawing>  
  
 Bir tür <xref:System.Windows.Freezable> nesnesi <xref:System.Windows.Media.Drawing> olduklarından, nesneler aşağıdakileri içeren birkaç özel özellik kazanırlar: birden çok nesne arasında paylaşılan, performansı artırmak için salt okunur hale getirilmiş, klonlanmış ve iş parçacığı güvenli hale getirilmiş [kaynaklar](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak bildirilebilirler. Nesneler tarafından <xref:System.Windows.Freezable> sağlanan farklı özellikler hakkında daha fazla bilgi için [Freezable Objects Overview](../advanced/freezable-objects-overview.md)'a bakın.  
  
<a name="drawinggeometriessection"></a>
## <a name="draw-a-shape"></a>Şekil Çiz  
 Bir şekil çizmek için, <xref:System.Windows.Media.GeometryDrawing>bir . Bir geometri çiziminin <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> özelliği çizilecek <xref:System.Windows.Media.GeometryDrawing.Brush%2A> şekli, özelliği şeklin iç tasarımının nasıl <xref:System.Windows.Media.GeometryDrawing.Pen%2A> boyanması gerektiğini ve özelliğinin anahattının nasıl çizilmesi gerektiğini açıklar.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.GeometryDrawing> bir şekil çizmek için a kullanır. Şekil bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesne tarafından açıklanır. Şeklin iç bir <xref:System.Windows.Media.LinearGradientBrush> ile boyanmış ve anahat ile <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>çizilir .  
  
 Bu örnek aşağıdakileri <xref:System.Windows.Media.GeometryDrawing>oluşturur.  
  
 ![İki elipsin Geometri Çizimi](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Bir Geometri Çizimi  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Tam örnek için [bkz.](how-to-create-a-geometrydrawing.md)  
  
 Eğriler ve <xref:System.Windows.Media.PathGeometry> yaylar oluşturarak daha karmaşık şekiller oluşturmanızı sağlamak gibi diğer <xref:System.Windows.Media.Geometry> sınıflar. Nesneler hakkında <xref:System.Windows.Media.Geometry> daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın.  
  
 Nesneleri kullanmayan <xref:System.Windows.Media.Drawing> şekiller çizmenin diğer yolları hakkında daha fazla bilgi için [WPF Genel Bakışı'nda Şekiller ve Temel Çizim'e](shapes-and-basic-drawing-in-wpf-overview.md)bakın.  
  
<a name="drawingimagessection"></a>
## <a name="draw-an-image"></a>Resim Çiz  
 Bir resim çizmek için, <xref:System.Windows.Media.ImageDrawing>bir . Bir <xref:System.Windows.Media.ImageDrawing> nesnenin <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> özelliği çizilecek görüntüyü açıklar <xref:System.Windows.Media.ImageDrawing.Rect%2A> ve özelliği görüntünün çizildiği bölgeyi tanımlar.  
  
 Aşağıdaki örnek, görüntüyü 100'e 100 piksel olan (75,75) bir dikdörtgenin içine çeker. Aşağıdaki resimde örnek <xref:System.Windows.Media.ImageDrawing> tarafından oluşturulan gösterir. Gri kenarlık, <xref:System.Windows.Media.ImageDrawing>'nin sınırlarını göstermek için eklendi.  
  
 ![100'e 100 Görüntü Çizilen 75,75 &#40;&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
A 100 by 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Görüntüler hakkında daha fazla bilgi için [Görüntülemeye Genel Bakış'a](imaging-overview.md)bakın.  
  
<a name="playmedia"></a>
## <a name="play-media-code-only"></a>Medya Oynatma (Yalnızca Kod)  
  
> [!NOTE]
> Bir <xref:System.Windows.Media.VideoDrawing> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bildirebilirsiniz rağmen, yalnızca yükleyebilirsiniz ve kod kullanarak medya oynatabilirsiniz. Video oynatmak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]için <xref:System.Windows.Controls.MediaElement> bunun yerine bir video kullanın.  
  
 Bir ses veya video dosyasını <xref:System.Windows.Media.VideoDrawing> oynatmak <xref:System.Windows.Media.MediaPlayer>için, bir ve bir . Medyayı yüklemenin ve oynatmanın iki yolu vardır. İlk <xref:System.Windows.Media.MediaPlayer> bir ve kendileri <xref:System.Windows.Media.VideoDrawing> tarafından kullanmak, ve ikinci yolu <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> ile kullanmak için <xref:System.Windows.Media.VideoDrawing>kendi oluşturmaktır ve .  
  
> [!NOTE]
> Uygulamanızla ortam dağıtırken, bir ortam dosyalarını bir görüntü gibi proje kaynağı olarak kullanamazsınız. Proje dosyanızda, bunun yerine ortam türünü `Content` ayarlamanız `PreserveNewest` `Always`ve ayarlamalısınız. `CopyToOutputDirectory`  
  
 Kendi <xref:System.Windows.Media.MediaTimeline>oluşturmadan medya oynatmak için, aşağıdaki adımları gerçekleştirin.  
  
1. Bir <xref:System.Windows.Media.MediaPlayer> nesne oluşturun.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Ortam <xref:System.Windows.Media.MediaPlayer.Open%2A> dosyasını yüklemek için yöntemi kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. Bir <xref:System.Windows.Media.VideoDrawing>.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. Özelliğini <xref:System.Windows.Media.VideoDrawing.Rect%2A> ayarlayarak ortamı çizmek için boyutu ve <xref:System.Windows.Media.VideoDrawing>konumu belirtin.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. <xref:System.Windows.Media.MediaPlayer> Oluşturduğunuz <xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing> özelliği ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Ortamı <xref:System.Windows.Media.MediaPlayer.Play%2A> <xref:System.Windows.Media.MediaPlayer> oynatmaya başlamak için yöntemini kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.VideoDrawing> bir <xref:System.Windows.Media.MediaPlayer> video dosyasını bir kez oynatmak için a ve a kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Ortam üzerinde ek zamanlama denetimi elde <xref:System.Windows.Media.MediaTimeline> etmek <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing> için, bir ve nesnelerle birlikte kullanın. Videonun <xref:System.Windows.Media.MediaTimeline> tekrarlanıp yinelenmeyeceğini belirtmenizi sağlar. A <xref:System.Windows.Media.VideoDrawing>ile <xref:System.Windows.Media.MediaTimeline> birlikte kullanmak için aşağıdaki adımları gerçekleştirirsiniz:  
  
1. Bildirin <xref:System.Windows.Media.MediaTimeline> ve zamanlama davranışlarını ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. Bir'den <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Media.MediaTimeline>bir oluştur.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. A <xref:System.Windows.Media.MediaPlayer> oluşturun ve <xref:System.Windows.Media.MediaClock> özelliğini <xref:System.Windows.Media.MediaPlayer.Clock%2A> ayarlamak için kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. Bir <xref:System.Windows.Media.VideoDrawing> oluşturun ve <xref:System.Windows.Media.MediaPlayer> özelliğine <xref:System.Windows.Media.VideoDrawing.Player%2A> <xref:System.Windows.Media.VideoDrawing>atamak.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.MediaTimeline> bir <xref:System.Windows.Media.MediaPlayer> videoyu <xref:System.Windows.Media.VideoDrawing> tekrar tekrar oynatmak için a ve a ile birlikte kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Bir <xref:System.Windows.Media.MediaTimeline>, 'ı kullandığınızda, etkileşimli yöntemler <xref:System.Windows.Media.Animation.Clock.Controller%2A> yerine <xref:System.Windows.Media.MediaClock> medya oynatmayı denetlemek için gelen <xref:System.Windows.Media.MediaPlayer>etkileşimli <xref:System.Windows.Media.Animation.ClockController> döndürülen leri kullandığınızı unutmayın.  
  
<a name="drawtext"></a>
## <a name="draw-text"></a>Metin Çiz  
 Metin çizmek için, <xref:System.Windows.Media.GlyphRunDrawing> bir <xref:System.Windows.Media.GlyphRun>ve bir . Aşağıdaki örnekte <xref:System.Windows.Media.GlyphRunDrawing> "Hello World" metnini çizmek için a kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 A, <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunusu ve yazdırma senaryolarıyla kullanılmak üzere tasarlanmış düşük düzeyli bir nesnedir. Ekrana metin çizmenin daha basit bir <xref:System.Windows.Controls.Label> yolu <xref:System.Windows.Controls.TextBlock>bir veya bir . Hakkında <xref:System.Windows.Media.GlyphRun>daha fazla bilgi için [GlyphRun Nesnesine Giriş ve Glyphs Elementi](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) genel bakışına bakın.  
  
<a name="compositedrawingssection"></a>
## <a name="composite-drawings"></a>Kompozit Çizimler  
 A, <xref:System.Windows.Media.DrawingGroup> birden çok çizimi tek bir bileşik çizimde birleştirmenizi sağlar. Bir <xref:System.Windows.Media.DrawingGroup>, kullanarak şekilleri, görüntüleri ve metni tek <xref:System.Windows.Media.Drawing> bir nesnede birleştirebilirsiniz.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.DrawingGroup> iki <xref:System.Windows.Media.GeometryDrawing> nesne ve <xref:System.Windows.Media.ImageDrawing> bir nesneyi birleştirmek için a kullanır. Bu örnek, aşağıdaki çıktıyı üretir.  
  
 ![Birden fazla çizimi olan bir DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Kompozit çizim  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 A <xref:System.Windows.Media.DrawingGroup> ayrıca, opaklık maskeleri, dönüşümler, bitmap efektleri ve diğer işlemleri içeriğine uygulamanızı sağlar. <xref:System.Windows.Media.DrawingGroup>işlemler <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>aşağıdaki sırayla uygulanır: <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.Transform%2A>, ve sonra .  
  
 Aşağıdaki <xref:System.Windows.Media.DrawingGroup> resimde, işlemlerin uygulandığı sıra gösterilmektedir.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemleri sırası  
  
 Aşağıdaki tabloda, bir <xref:System.Windows.Media.DrawingGroup> nesnenin içeriğini işlemek için kullanabileceğiniz özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|Illüstrasyon|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|İçeriğin seçili bölümlerinin <xref:System.Windows.Media.DrawingGroup> donukluğunu değiştirir. Örneğin, [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90))|![Opaklık maskesi olan drawinggroup](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|Düzgün içeriğini donukluk <xref:System.Windows.Media.DrawingGroup> değiştirir. <xref:System.Windows.Media.Drawing> Saydam veya kısmen saydam yapmak için bu özelliği kullanın. Örneğin, [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90))|![Farklı opaklık ayarlarına sahip Çizim Grupları](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|İçeriği için geçerlidir. <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Media.DrawingGroup> Örneğin, [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90))|![BlurBitmapEffect ile DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|<xref:System.Windows.Media.DrawingGroup> İçeriği bir <xref:System.Windows.Media.Geometry>' kullanarak tanımladığınız bir bölgeye klipsler. Örneğin, [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90))|![Tanımlı bir klip bölgesine sahip Çizim Grubu](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Aygıtbağımsız piksellerini belirtilen yönergeler boyunca aygıt piksellerine yakalar. Bu özellik, ince ayrıntılı grafiklerin düşük DPI ekranlarda keskin bir şekilde işlenmesini sağlamak için yararlıdır. Örneğin, [bkz.](how-to-apply-a-guidelineset-to-a-drawing.md)|![Kılavuz Seti olan ve olmayan bir Çizim Grubu](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|<xref:System.Windows.Media.DrawingGroup> İçeriği dönüştürür. Örneğin, [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90))|![Döndürülmüş Çizim Grubu](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>
## <a name="display-a-drawing-as-an-image"></a>Çizimi Görüntü Olarak Görüntüleme  
 Bir <xref:System.Windows.Media.Drawing> <xref:System.Windows.Controls.Image> denetimle bir ekran <xref:System.Windows.Media.DrawingImage> için, <xref:System.Windows.Controls.Image> a <xref:System.Windows.Controls.Image.Source%2A> denetimininki olarak kullanın ve nesnenin <xref:System.Windows.Media.DrawingImage> <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> özelliğini görüntülemek istediğiniz çizime ayarlayın.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.DrawingImage> bir <xref:System.Windows.Controls.Image> ve bir <xref:System.Windows.Media.GeometryDrawing>denetim görüntülemek için bir denetim kullanır. Bu örnek, aşağıdaki çıktıyı üretir.  
  
 ![İki elipsin Geometri Çizimi](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Bir Çizim Görüntüsü  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>
## <a name="paint-an-object-with-a-drawing"></a>Çizimle Nesneyi Boyama  
 A, <xref:System.Windows.Media.DrawingBrush> bir alanı çizim nesnesiyle boyayen bir fırça türüdür. Bir çizim ile hemen hemen herhangi bir grafik nesne boyamak için kullanabilirsiniz. Bir <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush> özelliği açıklar <xref:System.Windows.Media.DrawingBrush.Drawing%2A>onun . Bir <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush>ile işlemek için, fırçanın <xref:System.Windows.Media.Drawing> özelliğini kullanarak fırçaya ekleyin ve fırçayı denetim veya panel gibi bir grafik nesnesini boyamak için kullanın.  
  
 Aşağıdaki örnekler de <xref:System.Windows.Media.DrawingBrush> bir <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.GeometryDrawing>.'den oluşturulan bir desenle a'yı boyamak için kullanır. Bu örnek, aşağıdaki çıktıyı üretir.  
  
 ![Karo Çizim Fırçası](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush ile kullanılan Bir GeometriÇizimi  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 Sınıf, <xref:System.Windows.Media.DrawingBrush> içeriğini germe ve döşeme için çeşitli seçenekler sunar. Hakkında <xref:System.Windows.Media.DrawingBrush>daha fazla bilgi için [Resimler, Çizimler ve Görsellerle Resim'e](painting-with-images-drawings-and-visuals.md) genel bakış bakın.  
  
<a name="renderingwithvisualsection"></a>
## <a name="render-a-drawing-with-a-visual"></a>Görsel Çizim Oluşturma  
 A, <xref:System.Windows.Media.DrawingVisual> çizimi işlemek için tasarlanmış görsel nesne türüdür. Doğrudan görsel katmanda çalışmak, son derece özelleştirilmiş bir grafik ortamı oluşturmak isteyen geliştiriciler için bir seçenektir ve bu genel bakışta açıklanmaz. Daha fazla bilgi için [Bkz. ÇizimGörsel Nesneleri Kullanma](using-drawingvisual-objects.md) genel bakışı.  
  
<a name="drawingcontextobjects"></a>
## <a name="drawingcontext-objects"></a>ÇizimBağlam Nesneleri  
 Sınıf, <xref:System.Windows.Media.DrawingContext> görsel içerikli bir <xref:System.Windows.Media.Visual> veya <xref:System.Windows.Media.Drawing> bir doldurmanızı sağlar. Grafik içeriği çok verimli bir <xref:System.Windows.Media.DrawingContext> şekilde açıkladığı için bu tür alt düzey grafik nesnelerinin çoğu a kullanır.  
  
 Çizim <xref:System.Windows.Media.DrawingContext> yöntemleri <xref:System.Drawing.Graphics?displayProperty=nameWithType> türünün çizim yöntemlerine benzer görünse de, aslında çok farklıdırlar. <xref:System.Windows.Media.DrawingContext><xref:System.Drawing.Graphics?displayProperty=nameWithType> türün hemen mod grafik sistemi ile kullanılırken, korunmuş mod grafik sistemi ile kullanılır. Bir <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlarını kullandığınızda, aslında bir dizi işleme yönergelerini depoluyorsunuz (tam depolama mekanizması daha <xref:System.Windows.Media.DrawingContext>sonra grafik sistemi tarafından kullanılacak nesnenin türüne bağlı olsa da; gerçek zamanlı olarak ekrana çizim değildir. Windows Presentation Foundation (WPF) grafik sisteminin nasıl çalıştığı hakkında daha fazla bilgi için [WPF Grafik Oluşturma Genel Bakışı'na](wpf-graphics-rendering-overview.md)bakın.  
  
 Hiçbir zaman doğrudan bir <xref:System.Windows.Media.DrawingContext>ani lik atamayın; ancak, belirli yöntemlerden bir çizim bağlamı <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> edinebilirsiniz, gibi ve. <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>  
  
<a name="enumeratevisualcontents"></a>
## <a name="enumerate-the-contents-of-a-visual"></a>Görsel bir içeriğin sayısal  
 Diğer kullanımlarına ek <xref:System.Windows.Media.Drawing> olarak, nesneler bir <xref:System.Windows.Media.Visual>nesnenin içeriğini sıralamak için bir nesne modeli de sağlar.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> a <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.Visual> değerini almak ve sayısallamak için yöntemi kullanır.  
  
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
- [Nasıl Dır Konular](drawings-how-to-topics.md)

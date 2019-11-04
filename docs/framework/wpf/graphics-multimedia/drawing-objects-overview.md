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
ms.openlocfilehash: d4527c331308ff6cd517705212e09428216d2378
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459734"
---
# <a name="drawing-objects-overview"></a>Çizim Nesnelerine Genel Bakış
Bu konu <xref:System.Windows.Media.Drawing> nesneleri tanıtır ve bunları etkin şekilde şekiller, bit eşlemler, metin ve medya çizmek için nasıl kullanacağınızı açıklar. Küçük resim oluştururken <xref:System.Windows.Media.Drawing> nesneleri kullanın, bir <xref:System.Windows.Media.DrawingBrush>boyayın veya <xref:System.Windows.Media.Visual> nesneleri kullanın.  

<a name="whatisadrawingsection"></a>   
## <a name="what-is-a-drawing-object"></a>Çizim nesnesi nedir?  
 Bir <xref:System.Windows.Media.Drawing> nesnesi, şekil, bit eşlem, video veya metin satırı gibi görünür içerikleri açıklar. Farklı türdeki çizimler farklı içerik türlerini anlatmaktadır. Aşağıda, çizim nesnelerinin farklı türlerinin bir listesi verilmiştir.  
  
- <xref:System.Windows.Media.GeometryDrawing>: bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>: bir resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>: metin çizer.  
  
- <xref:System.Windows.Media.VideoDrawing> – bir ses veya video dosyası çalar.  
  
- <xref:System.Windows.Media.DrawingGroup>: diğer çizimleri çizer. Diğer çizimleri tek bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.Drawing> nesneler çok yönlüdür; <xref:System.Windows.Media.Drawing> nesnesini kullanmanın birçok yolu vardır.  
  
- Bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> denetimi kullanarak bir görüntü olarak görüntüleyebilirsiniz.  
  
- Bir <xref:System.Windows.Controls.Page><xref:System.Windows.Controls.Page.Background%2A> gibi bir nesneyi boyamak için bir <xref:System.Windows.Media.DrawingBrush> kullanabilirsiniz.  
  
- <xref:System.Windows.Media.DrawingVisual>görünümünü anlatmak için kullanabilirsiniz.  
  
- <xref:System.Windows.Media.Visual>içeriğini numaralandırmak için kullanabilirsiniz.  
  
 WPF, şekiller, bit eşlemler, metin ve medya çizme yeteneğine sahip olan diğer nesne türlerini sağlar. Örneğin, şekiller çizmek için <xref:System.Windows.Shapes.Shape> nesneleri de kullanabilirsiniz ve <xref:System.Windows.Controls.MediaElement> denetimi uygulamanıza video eklemek için başka bir yol sağlar. Bu nedenle <xref:System.Windows.Media.Drawing> nesneleri ne zaman kullanmalısınız? Performans avantajları elde etmek veya <xref:System.Windows.Freezable> özelliklere ihtiyaç duyduğunuzda, çerçeve düzeyindeki özellikleri feda edebilirsiniz. <xref:System.Windows.Media.Drawing> nesneler [Düzen](../advanced/layout.md), giriş ve odak için destek olmadığından, bunları arka planların, küçük resimlerin ve <xref:System.Windows.Media.Visual> nesnelerle alt düzey çizim için açıklamak için ideal hale getirir.  
  
 Bir tür <xref:System.Windows.Freezable> nesne olduklarından, <xref:System.Windows.Media.Drawing> nesneleri aşağıdakiler dahil olmak üzere birkaç özel özellik elde ederler: [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak, birden fazla nesne arasında paylaşılan, performansı artırmak için salt okunabilir hale getirilir, klonlanmış ve yapılabilir iş parçacığı güvenli. <xref:System.Windows.Freezable> nesneleri tarafından sunulan farklı özellikler hakkında daha fazla bilgi için, [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md)bölümüne bakın.  
  
<a name="drawinggeometriessection"></a>   
## <a name="draw-a-shape"></a>Şekil çiz  
 Bir şekil çizmek için <xref:System.Windows.Media.GeometryDrawing>kullanırsınız. Geometri çiziminin <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> özelliği, çizilecek şekli açıklar, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> özelliği şeklin iç kısmının nasıl boyanması gerektiğini ve <xref:System.Windows.Media.GeometryDrawing.Pen%2A> özelliği, anahattının nasıl çizildiğini açıklar.  
  
 Aşağıdaki örnek bir şekil çizmek için <xref:System.Windows.Media.GeometryDrawing> kullanır. Şekil bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesnesi tarafından tanımlanır. Şeklin iç kısmı bir <xref:System.Windows.Media.LinearGradientBrush> ile boyanmıştır ve ana hattı <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>ile çizilir.  
  
 Bu örnek, aşağıdaki <xref:System.Windows.Media.GeometryDrawing>oluşturur.  
  
 ![İki elips için GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexampleinline)]  
  
 Tüm örnek için bkz. [GeometryDrawing oluşturma](how-to-create-a-geometrydrawing.md).  
  
 <xref:System.Windows.Media.PathGeometry> gibi diğer <xref:System.Windows.Media.Geometry> sınıflar, eğriler ve yaylar oluşturarak daha karmaşık şekiller oluşturmanızı sağlar. <xref:System.Windows.Media.Geometry> nesneler hakkında daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).  
  
 <xref:System.Windows.Media.Drawing> nesneleri kullanmayan şekiller çizmenin diğer yolları hakkında daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](shapes-and-basic-drawing-in-wpf-overview.md).  
  
<a name="drawingimagessection"></a>   
## <a name="draw-an-image"></a>Görüntü çizme  
 Bir görüntü çizmek için <xref:System.Windows.Media.ImageDrawing>kullanırsınız. <xref:System.Windows.Media.ImageDrawing> nesnenin <xref:System.Windows.Media.ImageDrawing.ImageSource%2A> özelliği, çizilecek görüntüyü açıklar ve <xref:System.Windows.Media.ImageDrawing.Rect%2A> özelliği görüntünün çizildiği bölgeyi tanımlar.  
  
 Aşağıdaki örnek, (75, 75) konumunda bulunan bir dikdörtgene bir resim çizer ve 100 piksel 100 piksel. Aşağıdaki çizimde, örnek tarafından oluşturulan <xref:System.Windows.Media.ImageDrawing> gösterilmektedir. <xref:System.Windows.Media.ImageDrawing>sınırlarını göstermek için gri bir kenarlık eklenmiştir.  
  
 ![75, 75 ve üzerinde &#40;çizilmiş bir 100 x 100 ImageDrawing&#41;](./media/graphicsmm-simple-imagedrawing-offset.png "graphicsmm_simple_imagedrawing_offset")  
100 ile 100 ImageDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawing100by100inline)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawing100by100Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawing100by100inline)]  
  
 Görüntüler hakkında daha fazla bilgi için bkz. [görüntülemeye genel bakış](imaging-overview.md).  
  
<a name="playmedia"></a>   
## <a name="play-media-code-only"></a>Medyayı oynat (yalnızca kod)  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<xref:System.Windows.Media.VideoDrawing> bildirebilseniz de, yalnızca kodu kullanarak medyayı yükleyebilir ve oynatabilirsiniz. Videoyu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]oynatmak için, bunun yerine bir <xref:System.Windows.Controls.MediaElement> kullanın.  
  
 Ses veya video dosyası oynatmak için bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer>kullanırsınız. Medyayı yüklemek ve oynatmak için kullanabileceğiniz iki yol vardır. Birincisi bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> kendileri ve ikinci yöntem, <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing>birlikte kullanmak üzere kendi <xref:System.Windows.Media.MediaTimeline> oluşturmaktır.  
  
> [!NOTE]
> Medyayı uygulamanızla dağıtırken, bir görüntü gibi bir proje kaynağı olarak bir medya dosyası kullanamazsınız. Proje dosyanızda, bunun yerine medya türünü `Content` olarak ayarlamanız ve `CopyToOutputDirectory` ' i `PreserveNewest` ' ye `Always` ' e ayarlamanız gerekir.  
  
 Medyayı kendi <xref:System.Windows.Media.MediaTimeline>oluşturmadan yürütmek için aşağıdaki adımları gerçekleştirirsiniz.  
  
1. <xref:System.Windows.Media.MediaPlayer> nesnesi oluşturun.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline1)]  
  
2. Medya dosyasını yüklemek için <xref:System.Windows.Media.MediaPlayer.Open%2A> yöntemini kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline2)]  
  
3. <xref:System.Windows.Media.VideoDrawing>oluşturun.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline3)]  
  
4. <xref:System.Windows.Media.VideoDrawing><xref:System.Windows.Media.VideoDrawing.Rect%2A> özelliğini ayarlayarak medyayı çizmek için boyut ve konum belirtin.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline4)]  
  
5. <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.VideoDrawing.Player%2A> özelliğini oluşturduğunuz <xref:System.Windows.Media.MediaPlayer> ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline5](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline5)]  
  
6. Medyayı yürütmeye başlamak için <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaPlayer.Play%2A> yöntemini kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline6](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline6)]  
  
 Aşağıdaki örnek, bir video dosyasını bir kez oynatmak için bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetimi kazanmak için, <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleriyle bir <xref:System.Windows.Media.MediaTimeline> kullanın. <xref:System.Windows.Media.MediaTimeline>, videonun yinelenmesi gerekip gerekmediğini belirtmenizi sağlar. Bir <xref:System.Windows.Media.VideoDrawing><xref:System.Windows.Media.MediaTimeline> kullanmak için aşağıdaki adımları gerçekleştirirsiniz:  
  
1. <xref:System.Windows.Media.MediaTimeline> bildirin ve zamanlama davranışlarını ayarlayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline1)]  
  
2. <xref:System.Windows.Media.MediaTimeline><xref:System.Windows.Media.MediaClock> oluşturun.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline2)]  
  
3. <xref:System.Windows.Media.MediaPlayer> oluşturun ve <xref:System.Windows.Media.MediaPlayer.Clock%2A> özelliğini ayarlamak için <xref:System.Windows.Media.MediaClock> kullanın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline3)]  
  
4. <xref:System.Windows.Media.VideoDrawing> oluşturun ve <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing><xref:System.Windows.Media.VideoDrawing.Player%2A> özelliğine atayın.  
  
     [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline4](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline4)]  
  
 Aşağıdaki örnek, bir videoyu sürekli olarak oynatmak için bir <xref:System.Windows.Media.MediaPlayer> ve bir <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaTimeline> kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <xref:System.Windows.Media.MediaTimeline>kullandığınızda, <xref:System.Windows.Media.MediaPlayer>etkileşimli yöntemleri yerine medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliğinden döndürülen etkileşimli <xref:System.Windows.Media.Animation.ClockController> kullanacağınızı unutmayın.  
  
<a name="drawtext"></a>   
## <a name="draw-text"></a>Metin çiz  
 Metin çizmek için bir <xref:System.Windows.Media.GlyphRunDrawing> ve <xref:System.Windows.Media.GlyphRun>kullanırsınız. Aşağıdaki örnek, "Merhaba Dünya" metnini çizmek için bir <xref:System.Windows.Media.GlyphRunDrawing> kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GlyphRunDrawingExample.cs#glyphrundrawingexampleinline)]
 [!code-xaml[DrawingMiscSnippets_snip#GlyphRunDrawingExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GlyphRunExample.xaml#glyphrundrawingexampleinline)]  
  
 <xref:System.Windows.Media.GlyphRun>, sabit biçimli belge sunumu ve yazdırma senaryolarında kullanılması amaçlanan alt düzey bir nesnedir. Ekrana metin çizmenin daha basit bir yolu <xref:System.Windows.Controls.Label> veya <xref:System.Windows.Controls.TextBlock>kullanmaktır. <xref:System.Windows.Media.GlyphRun>hakkında daha fazla bilgi için bkz. [GlyphRun nesne ve Glifler öğesine giriş](../advanced/introduction-to-the-glyphrun-object-and-glyphs-element.md) genel bakış.  
  
<a name="compositedrawingssection"></a>   
## <a name="composite-drawings"></a>Bileşik çizimler  
 <xref:System.Windows.Media.DrawingGroup> birden çok çizimi tek bir bileşik çizimde birleştirmenizi sağlar. Bir <xref:System.Windows.Media.DrawingGroup>kullanarak şekilleri, resimleri ve metni tek bir <xref:System.Windows.Media.Drawing> nesnesi içinde birleştirebilirsiniz.  
  
 Aşağıdaki örnek, iki <xref:System.Windows.Media.GeometryDrawing> nesnesini ve bir <xref:System.Windows.Media.ImageDrawing> nesnesini birleştirmek için bir <xref:System.Windows.Media.DrawingGroup> kullanır. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Birden çok çizimle bir DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
Bileşik çizim  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <xref:System.Windows.Media.DrawingGroup> Ayrıca, içeriğe opaklık maskeleri, dönüşümler, bit eşlem efektleri ve diğer işlemler uygulamanıza olanak sağlar. <xref:System.Windows.Media.DrawingGroup> işlemler şu sırada uygulanır: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>ve <xref:System.Windows.Media.DrawingGroup.Transform%2A>.  
  
 Aşağıdaki çizimde <xref:System.Windows.Media.DrawingGroup> işlemlerinin uygulanma sırası gösterilmektedir.  
  
 ![DrawingGroup işlem sırası](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup işlemleri sırası  
  
 Aşağıdaki tabloda <xref:System.Windows.Media.DrawingGroup> nesnesinin içeriğini yönetmek için kullanabileceğiniz özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|Göstermektedir|  
|--------------|-----------------|------------------|  
|<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>|<xref:System.Windows.Media.DrawingGroup> içeriğinin seçili bölümlerinin saydamlığını değiştirir. Bir örnek için bkz. [nasıl yapılır: çizimin saydamlığını denetleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748242(v=vs.90)).|![Opaklık maskesi olan bir DrawingGroup](./media/graphicsmm-opmask.png "graphicsmm_opmask")|  
|<xref:System.Windows.Media.DrawingGroup.Opacity%2A>|<xref:System.Windows.Media.DrawingGroup> içeriğinin saydamlığını tek tek değiştirir. <xref:System.Windows.Media.Drawing> saydam veya kısmen saydam hale getirmek için bu özelliği kullanın. Bir örnek için bkz. [nasıl yapılır: bir çizime opaklık maskesi uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms753195(v=vs.90)).|![Farklı opaklık ayarlarına sahip DrawingGroups](./media/graphicsmm-opacity.png "graphicsmm_opacity")|  
|<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>|<xref:System.Windows.Media.DrawingGroup> içeriğine <xref:System.Windows.Media.Effects.BitmapEffect> uygular. Bir örnek için bkz. [nasıl yapılır: bir çizime BitmapEffect uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752341(v=vs.90)).|![BlurBitmapEffect ile DrawingGroup](./media/graphicsmm-bitmap.png "graphicsmm_bitmap")|  
|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|<xref:System.Windows.Media.DrawingGroup> içeriğini <xref:System.Windows.Media.Geometry>kullanarak betimleyen bir bölgeye kırpar. Bir örnek için bkz. [nasıl yapılır: çizimi kırpma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms743068(v=vs.90)) .|![Tanımlı bir klip bölgesi olan DrawingGroup](./media/graphicsmm-clipgeom.png "graphicsmm_clipgeom")|  
|<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>|Cihaz bağımsız piksellerini belirtilen yönergeleriyle cihaz pikselleriyle yaslar. Bu özellik, ayrıntılı grafiklerin düşük DPı ekranlarda keskin şekilde işlemesini sağlamak için yararlıdır. Bir örnek için bkz. [çizime bir kılavuz çizgisi kümesi uygulama](how-to-apply-a-guidelineset-to-a-drawing.md).|![Kılavuz çizgisi kümesi olmayan bir DrawingGroup](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")|  
|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|<xref:System.Windows.Media.DrawingGroup> içeriğini dönüştürür. Bir örnek için bkz. [nasıl yapılır: çizime dönüşüm uygulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms742304(v=vs.90)).|![Döndürülmüş bir DrawingGroup](./media/graphicsmm-rotate.png "graphicsmm_rotate")|  
  
<a name="usingimagedrawing"></a>   
## <a name="display-a-drawing-as-an-image"></a>Çizimi resim olarak görüntüleme  
 Bir <xref:System.Windows.Controls.Image> denetimiyle <xref:System.Windows.Media.Drawing> göstermek için, <xref:System.Windows.Controls.Image> denetiminin <xref:System.Windows.Controls.Image.Source%2A> olarak bir <xref:System.Windows.Media.DrawingImage> kullanın ve <xref:System.Windows.Media.DrawingImage> nesnesinin <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> özelliğini, göstermek istediğiniz çizime ayarlayın.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.GeometryDrawing>göstermek için bir <xref:System.Windows.Media.DrawingImage> ve <xref:System.Windows.Controls.Image> denetimini kullanır. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![İki elips için GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
Bir DrawingImage desteklenir  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
<a name="renderingwithdrawingbrushsection"></a>   
## <a name="paint-an-object-with-a-drawing"></a>Çizim ile nesne boyama  
 <xref:System.Windows.Media.DrawingBrush> çizim nesnesi olan bir alanı boyayan bir fırça türüdür. Çizim ile herhangi bir grafik nesnesini boyamak için kullanabilirsiniz. Bir <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing> özelliği <xref:System.Windows.Media.DrawingBrush.Drawing%2A>açıklar. Bir <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.DrawingBrush>işlemek için fırçanın <xref:System.Windows.Media.Drawing> özelliğini kullanarak fırçaya ekleyin ve bir denetim veya panel gibi bir grafik nesnesini boyamak için fırçayı kullanın.  
  
 Aşağıdaki örneklerde, bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.GeometryDrawing>oluşturulan bir desenli <xref:System.Windows.Shapes.Shape.Fill%2A> boyamak için bir <xref:System.Windows.Media.DrawingBrush> kullanılmaktadır. Bu örnek aşağıdaki çıktıyı üretir.  
  
 ![Döşeli bir DrawingBrush](./media/graphicsmm-drawingbrush-geometrydrawing.png "graphicsmm_drawingbrush_geometrydrawing")  
DrawingBrush ile kullanılan GeometryDrawing  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingBrushExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 <xref:System.Windows.Media.DrawingBrush> sınıfı, içeriğini uzatma ve döşeme için çeşitli seçenekler sağlar. <xref:System.Windows.Media.DrawingBrush>hakkında daha fazla bilgi için bkz. [görüntü, çizim ve görsellere](painting-with-images-drawings-and-visuals.md) genel bakış.  
  
<a name="renderingwithvisualsection"></a>   
## <a name="render-a-drawing-with-a-visual"></a>Görsel ile çizim işleme  
 <xref:System.Windows.Media.DrawingVisual>, bir çizimi işlemek için tasarlanan bir görsel nesne türüdür. Doğrudan görsel katmanda çalışmak, yüksek düzeyde özelleştirilmiş bir grafik ortamı oluşturmak isteyen geliştiriciler için bir seçenektir ve bu genel bakışta açıklanmamaktadır. Daha fazla bilgi için bkz. [DrawingVisual Objects 'ı kullanma](using-drawingvisual-objects.md) genel bakış.  
  
<a name="drawingcontextobjects"></a>   
## <a name="drawingcontext-objects"></a>DrawingContext nesneleri  
 <xref:System.Windows.Media.DrawingContext> sınıfı, bir <xref:System.Windows.Media.Visual> veya <xref:System.Windows.Media.Drawing> görsel içerikle doldurmanıza olanak sağlar. Birçok alt düzey grafik nesnesi, grafik içeriğini çok verimli bir şekilde açıkladığı için bir <xref:System.Windows.Media.DrawingContext> kullanır.  
  
 <xref:System.Windows.Media.DrawingContext> çizim yöntemleri <xref:System.Drawing.Graphics?displayProperty=nameWithType> türünün Çizim yöntemlerine benzer görünse de, aslında çok farklıdır. <xref:System.Windows.Media.DrawingContext>, bir tutulan mod grafik sistemiyle birlikte kullanılır, ancak <xref:System.Drawing.Graphics?displayProperty=nameWithType> türü bir anlık mod grafik sistemiyle kullanılır. <xref:System.Windows.Media.DrawingContext> nesnenin çizim komutlarını kullandığınızda, aslında bir dizi işleme yönergesi depoluyorsanız (tam depolama mekanizması, daha sonra grafik sistemi tarafından kullanılacak olan <xref:System.Windows.Media.DrawingContext>nesne türüne bağlıdır). ekranı gerçek zamanlı olarak çizmeyin. Windows Presentation Foundation (WPF) grafik sisteminin nasıl çalıştığı hakkında daha fazla bilgi için [WPF Grafik Işlemeye genel bakış ' a](wpf-graphics-rendering-overview.md)bakın.  
  
 Hiçbir <xref:System.Windows.Media.DrawingContext>doğrudan bir örnekleyemezsiniz; Ancak, <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>gibi belirli yöntemlerden bir çizim bağlamı elde edebilirsiniz.  
  
<a name="enumeratevisualcontents"></a>   
## <a name="enumerate-the-contents-of-a-visual"></a>Görselin Içeriğini listeleme  
 <xref:System.Windows.Media.Drawing> nesneler, diğer kullanımlarına ek olarak, bir <xref:System.Windows.Media.Visual>içeriğini numaralandırmak için de bir nesne modeli sağlar.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.DrawingGroup> değerini almak ve numaralandırmak için <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> yöntemini kullanır.  
  
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

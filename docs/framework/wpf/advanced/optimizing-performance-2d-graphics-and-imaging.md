---
title: 'Performansı İyileştirme: 2B Grafikleri ve Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933349"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Performansı İyileştirme: 2B Grafikleri ve Görüntüleme
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], uygulama gereksinimleriniz için iyileştirelebilecek çok sayıda 2B grafik ve görüntüleme işlevi sağlar. Bu konuda, bu alanlardaki performans iyileştirmesi hakkında bilgi verilmektedir.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Çizim ve şekiller  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]grafik çizim <xref:System.Windows.Media.Drawing> içeriğini <xref:System.Windows.Shapes.Shape> göstermek için hem hem de nesneleri sağlar. <xref:System.Windows.Media.Drawing> Ancak nesneler <xref:System.Windows.Shapes.Shape> nesnelerden daha basit yapılardır ve daha iyi performans özellikleri sağlar.  
  
 , Ekrana bir grafik şekli çizmenizi sağlar.<xref:System.Windows.Shapes.Shape> <xref:System.Windows.FrameworkElement> Sınıfından türetildiklerinden, <xref:System.Windows.Shapes.Shape> nesneler panolar ve çoğu denetim içinde kullanılabilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]grafik ve işleme hizmetlerine birçok farklı erişim katmanı sunar. Üst katmanda <xref:System.Windows.Shapes.Shape> nesnelerin kullanımı kolaydır ve düzen ve olay işleme gibi birçok yararlı özellik sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıma çok sayıda kullanıma yönelik Şekil nesnesi sağlar. Tüm şekil nesneleri <xref:System.Windows.Shapes.Shape> sınıfından devralınır. <xref:System.Windows.Shapes.Ellipse>Kullanılabilir şekil nesneleri <xref:System.Windows.Shapes.Line> ,<xref:System.Windows.Shapes.Path> ,,<xref:System.Windows.Shapes.Rectangle>, ve içerir. <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>  
  
 <xref:System.Windows.Media.Drawing>Diğer taraftan nesneler, <xref:System.Windows.FrameworkElement> sınıftan türemez ve şekilleri, resimleri ve metni işlemek için daha hafif bir uygulama sağlar.  
  
 Dört tür <xref:System.Windows.Media.Drawing> nesne vardır:  
  
- <xref:System.Windows.Media.GeometryDrawing>Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>Bir resim çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Metin çizer.  
  
- <xref:System.Windows.Media.DrawingGroup>Diğer çizimleri çizer. Diğer çizimleri tek bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 <xref:System.Windows.Media.GeometryDrawing> Nesnesi geometri içeriğini işlemek için kullanılır. , Ve gibi bu <xref:System.Windows.Media.CombinedGeometry> <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.PathGeometry>sınıftan türetilen somut sınıflar ve ayrıca,,, ve için isabet testi ve kırpma desteği sağlamak için bir yol sağlar. <xref:System.Windows.Media.Geometry> Geometri nesneleri, bir denetimin bölgesini tanımlamak (örneğin, veya bir görüntüye uygulanacak klip bölgesini tanımlamak için) kullanılabilir. Geometri nesneleri, dikdörtgenler ve daireler gibi basit bölgeler veya iki ya da daha fazla geometri nesnesinden oluşturulan bileşik bölgeler olabilir. <xref:System.Windows.Media.PathSegment>, Ve <xref:System.Windows.Media.ArcSegment> <xref:System.Windows.Media.BezierSegment>gibi birleştiren nesneler ile daha karmaşık geometrik bölgeler oluşturulabilir. <xref:System.Windows.Media.QuadraticBezierSegment>  
  
 Yüzeyde, <xref:System.Windows.Media.Geometry> sınıfı <xref:System.Windows.Shapes.Shape> ve sınıfı oldukça benzerdir. Her ikisi de 2B grafik işlemede kullanılır ve her ikisi de bunlardan türetilmiş benzer somut sınıflara sahiptir; Örneğin, <xref:System.Windows.Media.EllipseGeometry> ve. <xref:System.Windows.Shapes.Ellipse> Ancak, bu iki sınıf kümesi arasında önemli farklılıklar vardır. Bir tane <xref:System.Windows.Media.Geometry> için sınıfta, <xref:System.Windows.Shapes.Shape> sınıfının kendisini çizme özelliği gibi bazı işlevleri eksiktir. Bir geometri nesnesi çizmek için, DrawingContext, çizim veya yol gibi başka bir sınıf (yolun bir şekil olduğunu belirtmekte) çizim işlemini gerçekleştirmek için kullanılması gerektiğini unutmayın. Fill, vuruş ve vuruş kalınlığı gibi işleme özellikleri, geometri nesnesini çizen sınıfta bulunur, ancak Şekil nesnesi bu özellikleri içerir. Bu farkı düşünmenin bir yolu, bir geometri nesnesinin bir bölgeyi tanımladığından bir daire, örneğin bir şekil nesnesinin bir bölgeyi tanımladığından, bu bölgenin nasıl doldurulduğunu ve özetlenmediğini tanımlar ve Düzen sistemine katılır.  
  
 Nesneler <xref:System.Windows.Shapes.Shape> <xref:System.Windows.FrameworkElement> sınıftan türetildiğinden, bunları kullanarak uygulamanıza önemli ölçüde daha fazla bellek tüketimi eklenebilir. Grafik içeriğinizin <xref:System.Windows.FrameworkElement> özelliklerine gerçekten ihtiyacınız yoksa, daha hafif <xref:System.Windows.Media.Drawing> nesneleri kullanmayı düşünün.  
  
 Nesneler hakkında <xref:System.Windows.Media.Drawing> daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry nesneleri  
 Nesne <xref:System.Windows.Media.StreamGeometry> , geometrik şekiller oluşturmaya <xref:System.Windows.Media.PathGeometry> yönelik hafif bir alternatiftir. Karmaşık bir <xref:System.Windows.Media.StreamGeometry> geometriyi açıklamanız gerektiğinde bir kullanın. <xref:System.Windows.Media.StreamGeometry>birçok <xref:System.Windows.Media.PathGeometry> nesneyi işlemek için iyileştirilmiştir ve birçok ayrı <xref:System.Windows.Media.PathGeometry> nesne kullanmaya kıyasla daha iyi çalışır.  
  
 Aşağıdaki örnek, içinde <xref:System.Windows.Media.StreamGeometry> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir üçgen oluşturmak için öznitelik sözdizimini kullanır.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Nesneler hakkında <xref:System.Windows.Media.StreamGeometry> daha fazla bilgi için bkz. [StreamGeometry kullanarak şekil oluşturma](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual nesneleri  
 <xref:System.Windows.Media.DrawingVisual> Nesnesi şekilleri, resimleri veya metni işlemek için kullanılan basit bir çizim sınıfıdır. Bu sınıf, performansı artıran düzen veya olay işleme sağlamadığından hafif olarak değerlendirilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir. Daha fazla bilgi için bkz. [DrawingVisual nesnelerini kullanma](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Görüntüler  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]görüntüleme, Windows 'un önceki sürümlerindeki görüntüleme özelliklerine göre önemli bir geliştirme sağlar. Genellikle Microsoft Windows Grafik Cihaz Arabirimi (GDI) veya Microsoft Windows GDI+ uygulama programlama arabirimi (API) tarafından bir bit eşlem görüntüleme veya ortak denetimde görüntü kullanma gibi görüntüleme özellikleri. Bu API 'nin sunduğu temel görüntüleme işlevselliği, ancak codec genişletilebilirliği ve yüksek uygunlukta görüntü desteği gibi özellikleri destekler. WPF Görüntüleme API 'SI, GDI ve GDI+ 'ın eksiklılarını aşmak için yeniden tasarlanmıştır ve uygulamalarınızda resimleri görüntülemeye ve kullanmaya yönelik yeni bir API kümesi sağlar.  
  
 Görüntüleri kullanırken, daha iyi performans kazanmak için aşağıdaki önerileri göz önünde bulundurun:  
  
- Uygulamanız, küçük resim görüntülerini görüntülemenizi gerektiriyorsa görüntünün azaltılmış boyutlu bir sürümünü oluşturmayı düşünün. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntünüzü yükler ve tam boyutuna göre kodunu çözer. Görüntünün yalnızca küçük resim sürümünü istiyorsanız, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gereksiz görüntünün tam boyutuna göre kodunu çözer ve daha sonra küçük resim boyutuna ölçeklendirir. Bu gereksiz yükü önlemek için, resmin kodunu bir küçük [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] resme çözme ya da bir küçük resim boyutu görüntüsünü yükleme isteğinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bulabilirsiniz.  
  
- Her zaman görüntünün kodunu, varsayılan boyuta değil istenen boyuta göre çözün. Yukarıda belirtildiği gibi, resminizin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunu, varsayılan tam boyuta değil, istenen boyuta göre çözme isteği. Yalnızca uygulamanızın çalışma kümesini değil, yürütme hızını da azaltmış olursunuz.  
  
- Mümkünse, görüntüleri birden çok görüntüden oluşan film şeridi gibi tek bir görüntüde birleştirin.  
  
- Daha fazla bilgi için bkz. [Imaging 'e genel bakış](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Herhangi bir bit eşlemin ölçeğini canlandırdığınızda, varsayılan yüksek kaliteli görüntü yeniden örnekleme algoritması bazen çerçeve hızının azalmasına neden olacak şekilde yeterli sistem kaynağı tüketebilir, bu da animasyonların stutter çalışmasına neden olabilir. <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> Nesnesinin özelliğini olarak<xref:System.Windows.Media.BitmapScalingMode.LowQuality>ayarlayarak , bir bit eşlemi ölçeklendirirken daha yumuşak <xref:System.Windows.Media.RenderOptions> bir animasyon oluşturabilirsiniz. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>modu, işleme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] altyapısından, görüntüleri işlerken kalite için iyileştirilmiş algoritmadan hız için iyileştirilmiş bir algoritmaya geçiş gerçekleştirmesini söyler.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.BitmapScalingMode> bir görüntü nesnesi için nasıl ayarlanacağını gösterir.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>Cachingipucu  
 Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.TileBrush> gibi<xref:System.Windows.Media.VisualBrush>nesnelerin işlenmiş içeriğini önbelleğe almaz. Sahne <xref:System.Windows.Media.TileBrush> içindeki içeriğin içeriği ve kullanımı değişmediği statik senaryolarda, bu, video belleği üzerinde işlem yaptığından bu mantıklı olur. Statik olmayan bir <xref:System.Windows.Media.TileBrush> şekilde kullanıldığında (örneğin, statik <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> döndürme bir 3B nesnenin yüzeyine eşlendiğinde), bu çok anlamlı değildir. Varsayılan davranışı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , içerik değiştirilmese de, her çerçeve için <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> tüm içeriğini yeniden işlemeye yöneliktir.  
  
 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> Nesnenin özelliğini olarak<xref:System.Windows.Media.CachingHint.Cache>ayarlayarak , döşeli fırça nesnelerinin önbelleğe alınmış sürümlerini <xref:System.Windows.Media.RenderOptions> kullanarak performansı artırabilirsiniz.  
  
 Ve <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> özellik <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> değerleri, <xref:System.Windows.Media.TileBrush> nesnenin ölçekteki değişiklikler nedeniyle ne zaman yeniden oluşturulması gerektiğini tespit eden göreli boyut değerleridir. Örneğin, <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> özelliği 2,0 olarak ayarlayarak, <xref:System.Windows.Media.TileBrush> tek için önbellek, boyutu geçerli önbelleğin boyutunu iki kez aştığında yeniden üretilmelidir.  
  
 Aşağıdaki örnek, için <xref:System.Windows.Media.DrawingBrush>önbelleğe alma ipucu seçeneğinin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
- [Animasyon İpuçları ve Püf Noktaları](../graphics-multimedia/animation-tips-and-tricks.md)

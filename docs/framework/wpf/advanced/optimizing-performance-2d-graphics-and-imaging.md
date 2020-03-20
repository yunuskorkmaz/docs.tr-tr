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
ms.openlocfilehash: 03b2b64736407bf54c9bf957fe93d2d3d6e343f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186775"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Performansı İyileştirme: 2B Grafikleri ve Görüntüleme
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulama gereksinimleriniz için optimize edilebilen çok çeşitli 2B grafik ve görüntüleme işlevleri sağlar. Bu konu, bu alanlarda performans optimizasyonu hakkında bilgi sağlar.  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>Çizim ve Şekiller  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]grafik <xref:System.Windows.Media.Drawing> çizim <xref:System.Windows.Shapes.Shape> içeriğini temsil etmek için hem de nesneleri sağlar. Ancak, <xref:System.Windows.Media.Drawing> nesneler nesnelere göre <xref:System.Windows.Shapes.Shape> daha basit yapılardır ve daha iyi performans özellikleri sağlar.  
  
 A <xref:System.Windows.Shapes.Shape> ekrana bir grafik şekli çizmenizi sağlar. <xref:System.Windows.FrameworkElement> Sınıftan türetildiği için, <xref:System.Windows.Shapes.Shape> nesneler panellerin ve denetimlerin çoğunda kullanılabilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]grafik ve render hizmetlerine çeşitli katmanlar sunar. Üst katmanda, <xref:System.Windows.Shapes.Shape> nesnelerin kullanımı kolaydır ve düzen ve olay işleme gibi birçok yararlı özellik sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanıma hazır şekil nesneleri bir dizi sağlar. Tüm şekil nesneleri <xref:System.Windows.Shapes.Shape> sınıftan devralır. Kullanılabilir şekil nesneleri <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle>, , ve .  
  
 <xref:System.Windows.Media.Drawing>nesneler, diğer taraftan, <xref:System.Windows.FrameworkElement> sınıftan türetin ve şekiller, görüntüler ve metin işleme için daha hafif bir uygulama sağlar.  
  
 Dört tür <xref:System.Windows.Media.Drawing> nesne vardır:  
  
- <xref:System.Windows.Media.GeometryDrawing>Bir şekil çizer.  
  
- <xref:System.Windows.Media.ImageDrawing>Bir görüntü çizer.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Metin çizer.  
  
- <xref:System.Windows.Media.DrawingGroup>Diğer çizimleri çizer. Diğer çizimleri tek bir bileşik çizimde birleştirmek için bir çizim grubu kullanın.  
  
 Nesne <xref:System.Windows.Media.GeometryDrawing> geometri içeriğini işlemek için kullanılır. Sınıf <xref:System.Windows.Media.Geometry> ve ondan türetilen somut sınıflar, <xref:System.Windows.Media.CombinedGeometry>gibi <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, ve , 2D grafik işleme için bir araç sağlamak, hem de isabet testi ve kırpma desteği sağlar. Geometri nesneleri, örneğin bir denetimin bölgesini tanımlamak veya görüntüye uygulanacak küçük bölgeyi tanımlamak için kullanılabilir. Geometri nesneleri dikdörtgenler ve daireler gibi basit bölgeler veya iki veya daha fazla geometri nesnesinden oluşturulan bileşik bölgeler olabilir. Daha karmaşık geometrik bölgeler, <xref:System.Windows.Media.PathSegment>türemiş nesneleri birleştirerek oluşturulabilir, gibi <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, ve <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Yüzeyde, <xref:System.Windows.Media.Geometry> sınıf ve <xref:System.Windows.Shapes.Shape> sınıf oldukça benzerdir. Her ikisi de 2D grafik işleme kullanılır ve her ikisi de onlardan türeyen benzer somut sınıflar var, örneğin, <xref:System.Windows.Media.EllipseGeometry> ve <xref:System.Windows.Shapes.Ellipse>. Ancak, bu iki sınıf kümesi arasında önemli farklar vardır. İlk olarak, <xref:System.Windows.Media.Geometry> sınıf, kendisini çizme yeteneği <xref:System.Windows.Shapes.Shape> gibi sınıfın bazı işlevlerinden yoksundur. Bir geometri nesnesi çizmek için, Çizim Bağlamı, Çizim veya Yol gibi başka bir sınıf (Bir Yol'un Şekil olduğunu belirtmekte yarar vardır) çizim işlemini gerçekleştirmek için kullanılmalıdır. Dolgu, kontur ve kontur kalınlığı gibi oluşturma özellikleri geometri nesnesini çizen sınıfta, şekil nesnesi ise bu özellikleri içerir. Bu farkı düşünmenin bir yolu, bir geometri nesnesinin bir bölgeyi, örneğin bir daireyi tanımlaması, şekil nesnesinin bir bölgeyi tanımlaması, o bölgenin nasıl doldurulup özetlenmiş olduğunu tanımlaması ve düzen sistemine katılmasıdır.  
  
 Nesneler <xref:System.Windows.Shapes.Shape> <xref:System.Windows.FrameworkElement> sınıftan türediğinden, bunları kullanmak uygulamanızda önemli ölçüde daha fazla bellek tüketimi ekleyebilirsiniz. Grafik içeriğiniz için <xref:System.Windows.FrameworkElement> gerçekten özelliklere ihtiyacınız yoksa, daha hafif <xref:System.Windows.Media.Drawing> nesneleri kullanmayı düşünün.  
  
 Nesneler hakkında <xref:System.Windows.Media.Drawing> daha fazla bilgi için Bkz. [Çizim Nesneleri Genel Bakış.](../graphics-multimedia/drawing-objects-overview.md)  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>StreamGeometri Nesneleri  
 Nesne <xref:System.Windows.Media.StreamGeometry> geometrik şekiller <xref:System.Windows.Media.PathGeometry> oluşturmak için hafif bir alternatiftir. Karmaşık <xref:System.Windows.Media.StreamGeometry> bir geometriyi tanımlamanız gerektiğinde a kullanın. <xref:System.Windows.Media.StreamGeometry>birçok <xref:System.Windows.Media.PathGeometry> nesneyi işlemek için optimize edilmiş ve birçok <xref:System.Windows.Media.PathGeometry> ayrı nesne yle karşılaştırıldığında daha iyi performans gösterir.  
  
 Aşağıdaki örnekte üçgen <xref:System.Windows.Media.StreamGeometry> oluşturmak için öznitelik sözdizimi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanır.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Nesneler hakkında <xref:System.Windows.Media.StreamGeometry> daha fazla bilgi için [bkz.](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>ÇizimGörsel Nesneler  
 Nesne, <xref:System.Windows.Media.DrawingVisual> şekilleri, görüntüleri veya metni işlemek için kullanılan hafif bir çizim sınıfıdır. Bu sınıf, performansını artıran düzen veya olay işleme sağlamadığından hafif olarak kabul edilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir. Daha fazla bilgi için [Bkz. ÇizimGörsel Nesneleri Kullanma.](../graphics-multimedia/using-drawingvisual-objects.md)  
  
<a name="Images"></a>
## <a name="images"></a>Görüntüler  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]görüntüleme, Windows'un önceki sürümlerinde görüntüleme yetenekleri üzerinde önemli bir iyileşme sağlar. Biteş görüntüleme veya ortak denetimde görüntü kullanma gibi görüntüleme özellikleri öncelikle Microsoft Windows Graphics Device Interface (GDI) veya Microsoft Windows GDI+ uygulama programlama arabirimi (API) tarafından ele alınır. Bu API temel görüntüleme işlevselliği sağladı, ancak codec genişletilebilirlik ve yüksek doğruluk görüntü desteği desteği gibi özellikleri yoktu. WPF Görüntüleme API'sı, GDI ve GDI+'nın eksikliklerini aşmak ve uygulamalarınızdaki görüntüleri görüntülemek ve kullanmak için yeni bir API seti sağlamak üzere yeniden tasarlandı.  
  
 Görüntüleri kullanırken, daha iyi performans elde etmek için aşağıdaki önerileri göz önünde bulundurun:  
  
- Uygulamanız küçük resim görüntülerini görüntülemenizi gerektiriyorsa, görüntünün azaltılmış boyutlu bir sürümünü oluşturmayı düşünün. Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntünüzü yükler ve tam boyutuna kadar çözer. Yalnızca resmin küçük resim sürümünü istiyorsanız, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gereksiz görüntünün tam boyutuna kadar deşifre eder ve ardından küçük resim boyutuna küçültür. Bu gereksiz yükü önlemek için, görüntüyü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] küçük resim boyutuna göre çözmeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya küçük resim boyutu görüntüsünü yüklemeyi isteyebilirsiniz.  
  
- Görüntüyü her zaman varsayılan boyuta değil, istediğiniz boyutta deşifre edin. Yukarıda belirtildiği gibi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan tam boyutu değil, istenilen boyutta görüntü deşifre etmek için istek. Yalnızca uygulamanızın çalışma kümesini değil, yürütme hızını da azaltırsınız.  
  
- Mümkünse, görüntüleri birden çok görüntüden oluşan bir film şeridi gibi tek bir görüntüde birleştirin.  
  
- Daha fazla bilgi için [Görüntülemegenel bakış](../graphics-multimedia/imaging-overview.md)bilgisine bakın.  
  
### <a name="bitmapscalingmode"></a>Bitmapscalingmode  
 Herhangi bir bit eşlemeölçeğini animasyonyaparken, varsayılan yüksek kaliteli görüntü yeniden örnekleme algoritması bazen kare hızı bozulmasına neden olacak yeterli sistem kaynaklarını tüketebilir ve animasyonların kekemeliğe neden olabilir. Nesnenin <xref:System.Windows.Media.BitmapScalingMode.LowQuality> <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> özelliğini <xref:System.Windows.Media.RenderOptions> ayarlayarak, bit eşlemi ölçeklerken daha düzgün bir animasyon oluşturabilirsiniz. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>modu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleri işlerken, işleme motoruna kalite için optimize edilmiş bir algoritmadan hız için optimize edilmiş bir algoritmaya geçmesini söyler.  
  
 Aşağıdaki örnek, bir görüntü <xref:System.Windows.Media.BitmapScalingMode> nesnesinin nasıl ayarlanır olduğunu gösterir.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>Önbelleğe Almaİpucu  
 Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak, nesnelerin işlenen <xref:System.Windows.Media.TileBrush> içeriğini önbelleğe almaz, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>gibi ve . Sahnedeki içeriğin veya kullanımının <xref:System.Windows.Media.TileBrush> değişmediği statik senaryolarda, video belleği muhafaza ettiği için bu mantıklıdır. Statik içeriğe sahip bir <xref:System.Windows.Media.TileBrush> nesnenin statik olmayan bir şekilde kullanılması (örneğin, statik <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> bir statik veya dönen bir 3B nesnenin yüzeyine eşlendiğinde) o kadar da anlamlı değildir. Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] davranış, içerik değişmese bile, <xref:System.Windows.Media.DrawingBrush> tüm <xref:System.Windows.Media.VisualBrush> içeriği veya her kare için yeniden işlemektir.  
  
 Nesnenin <xref:System.Windows.Media.RenderOptions.CachingHint%2A> özelliğini <xref:System.Windows.Media.RenderOptions> ayarlayarak, <xref:System.Windows.Media.CachingHint.Cache> karo fırça nesnelerinönbelleğe alınmış sürümlerini kullanarak performansı artırabilirsiniz.  
  
 Ve <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> özellik değerleri, ölçekteki değişiklikler <xref:System.Windows.Media.TileBrush> nedeniyle nesnenin ne zaman yeniden oluşturulmasını belirleyen göreli boyut değerleridir. Örneğin, <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> özelliği 2,0 olarak ayarlayarak, boyutu <xref:System.Windows.Media.TileBrush> geçerli önbelleğin iki katını aştığında yalnızca önbelleğin yeniden oluşturulması gerekir.  
  
 Aşağıdaki örnek, önbelleğe <xref:System.Windows.Media.DrawingBrush>alma ipucu seçeneğinin nasıl kullanılacağını gösterir.  
  
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

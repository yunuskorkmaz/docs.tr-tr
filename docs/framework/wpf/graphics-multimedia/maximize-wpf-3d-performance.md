---
title: 3B performansını en üst düzeye çıkarma
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 414a4677a1e05cd69c382e35194328d6ce1bddf9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744603"
---
# <a name="maximize-wpf-3d-performance"></a>WPF 3B Performansını En Üst Düzeye Çıkarma
3B denetimleri derlemek ve uygulamalarınıza 3B sahneler eklemek için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullandığınızda, performans iyileştirmesini göz önünde bulundurmanız önemlidir. Bu konu, uygulamanız için performans etkilerine sahip 3B sınıfların ve özelliklerin bir listesini ve bunları kullanırken performansı iyileştirmeye yönelik önerileri sağlar.  
  
 Bu konuda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B özelliklerinin Gelişmiş bir şekilde anlaşıldığı varsayılmaktadır. Bu belgedeki öneriler, "işleme katmanı 2" için geçerlidir (kabaca, pixel shader sürüm 2,0 ve köşe gölgelendirici sürüm 2,0 ' ni destekleyen donanımlar). Daha ayrıntılı bilgi için bkz. [grafik Işleme katmanları](../advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Performans etkisi: yüksek  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Fırça hızı (en hızlı en yavaş):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (önbelleğe alınmış)<br /><br /> <xref:System.Windows.Media.VisualBrush> (önbelleğe alınmış)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (önbelleğe alınmamış)<br /><br /> <xref:System.Windows.Media.VisualBrush> (önbelleğe alınmamış)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Bir <xref:System.Windows.Controls.Viewport3D> içeriğini Viewport3D's dikdörtgenine açıkça kırpmanız [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] gerekmiyorsa `Viewport3D.ClipToBounds` false olarak ayarlayın. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bir diğer ad kırpması çok yavaş olabilir ve `ClipToBounds` <xref:System.Windows.Controls.Viewport3D>varsayılan olarak etkinleştirilir (yavaş).|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Fare isabet sınamasını gerçekleştirirken bir <xref:System.Windows.Controls.Viewport3D> içeriğini göz önünde bulunduristemediğiniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] durumlarda `Viewport3D.IsHitTestVisible` false olarak ayarlayın.  3B içerik için isabet testi, yazılımda yapılır ve büyük kafeslerde yavaş olabilir. <xref:System.Windows.UIElement.IsHitTestVisible%2A>, <xref:System.Windows.Controls.Viewport3D>varsayılan olarak etkinleştirilir (yavaş).|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Yalnızca farklı malzemeler veya dönüşümler gerektiren farklı modeller oluşturun.  Aksi takdirde, çok sayıda <xref:System.Windows.Media.Media3D.GeometryModel3D> örneğini aynı malzemelerle bir kez daha büyük <xref:System.Windows.Media.Media3D.GeometryModel3D> ve <xref:System.Windows.Media.Media3D.MeshGeometry3D> örneklerine birleştirir.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Kafes animasyonu — her çerçeve için bir kafesin tek köşesi değiştirildiğinde, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]her zaman verimli değildir.  Her köşe değiştirildiğinde değişiklik bildirimlerinin performans etkisini en aza indirmek için, köşe başına değişiklik yapmadan önce kafesi görsel ağaçtan ayırın.  Ağ değiştirildikten sonra görsel ağaca yeniden iliştirin.  Ayrıca, bu şekilde canlandırılacak kafeslerin boyutunu en aza indirmeye çalışın.|  
|3B düzgünleştirme|İşleme hızını artırmak için, ekli özellik <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> `Aliased`olarak ayarlayarak <xref:System.Windows.Controls.Viewport3D> çoklu örnekleme özelliğini devre dışı bırakın.  Varsayılan olarak, 3B düzgünleştirme, her piksel için 4 örnek içeren Windows üzerinde etkindir.|  
|Metin|3B sahnedeki canlı metin (bir <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush>) yavaş olabilir. Metin değişmediği takdirde, bunun yerine metnin görüntülerini (<xref:System.Windows.Media.Imaging.RenderTargetBitmap>aracılığıyla) kullanmayı deneyin.|  
|<xref:System.Windows.Media.TileBrush>|Fırçanın içeriği statik olmadığından, bir <xref:System.Windows.Media.VisualBrush> veya <xref:System.Windows.Media.DrawingBrush> bir 3B sahnede kullanmanız gerekiyorsa, fırçayı önbelleğe almayı deneyin (iliştirilmiş <xref:System.Windows.Media.RenderOptions.CachingHint%2A> özelliği `Cache`olarak ayarlama).  Önbelleğe alınan fırçaların çok sık yeniden üretilmemesi, ancak istediğiniz kalite düzeyini sürdürmemesi için, en düşük ve en yüksek ölçek ayarlama eşiklerini (iliştirilmiş özelliklerle <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> ve <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) ayarlayın.  Varsayılan olarak, <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush> önbelleğe alınmaz, yani fırçayla boyanmış bir şeyin yeniden oluşturulması gereken her şey, fırçanın tüm içeriğinin bir ara yüzeye yeniden oluşturulması gerekir.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>, etkilenen tüm içerikleri donanım hızlandırma olmadan işlenecek şekilde zorlar.  En iyi performans için <xref:System.Windows.Media.Effects.BitmapEffect>kullanmayın.|  
  
## <a name="performance-impact-medium"></a>Performans etkisi: Orta  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bir ağ, paylaşılan köşelerle bir dizi üçgen olarak tanımlandığında ve bu köşeler aynı konuma, normal ve doku koordinatlarına sahip olduğunda, her bir paylaşılan köşeyi yalnızca bir kez tanımlayın ve ardından <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>, üçgenlerinizi dizine göre tanımlayın.|  
|<xref:System.Windows.Media.ImageBrush>|Boyut üzerinde açık denetime sahip olduğunuzda (<xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve/veya <xref:System.Windows.Media.ImageBrush>) doku boyutlarını en aza indirmeye çalışın.  Daha düşük çözünürlüklü dokuların görsel kalitesini azalyacağını unutmayın, bu nedenle kalite ve performans arasındaki doğru dengeyi bulmayı deneyin.|  
|Opaklık|Yarı saydam 3B içeriğini (yansıma gibi) işlerken, `Viewport3D.Opacity` 1 ' den küçük bir değere ayarlayarak ayrı bir yarı saydam <xref:System.Windows.Controls.Viewport3D> oluşturmak yerine fırçalar veya malzemelerde (<xref:System.Windows.Media.Brush.Opacity%2A> veya <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>aracılığıyla) opaklık özelliklerini kullanın.|  
|<xref:System.Windows.Controls.Viewport3D>|Sahnede kullandığınız <xref:System.Windows.Controls.Viewport3D> nesne sayısını en aza indirin.  Her bir model için ayrı Viewport3D örnekleri oluşturmak yerine aynı Viewport3D birçok 3B model yerleştirin.|  
|<xref:System.Windows.Freezable>|Genellikle <xref:System.Windows.Media.Media3D.MeshGeometry3D>, <xref:System.Windows.Media.Media3D.GeometryModel3D>, fırçalar ve malzemeler kullanmak faydalıdır.  All, `Freezable`türetildiklerinden beri multiparentable.|  
|<xref:System.Windows.Freezable>|Özellikleri uygulamanızda değişmeden kalacaksa Freezable nesneleri üzerinde <xref:System.Windows.Freezable.Freeze%2A> yöntemi çağırın.  Dondurma, çalışma kümesini azaltabilir ve hızı artırabilir.|  
|<xref:System.Windows.Media.Brush>|Fırçanın içeriği değişmeyecektir <xref:System.Windows.Media.VisualBrush> veya <xref:System.Windows.Media.DrawingBrush> yerine <xref:System.Windows.Media.ImageBrush> kullanın.  2B içerik <xref:System.Windows.Media.Imaging.RenderTargetBitmap> aracılığıyla bir <xref:System.Windows.Controls.Image> dönüştürülebilir ve sonra bir <xref:System.Windows.Media.ImageBrush>kullanılabilir.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Gerçekten <xref:System.Windows.Media.Media3D.GeometryModel3D>arka yüzlerini görmeniz gerekmiyorsa <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> kullanmayın.|  
|<xref:System.Windows.Media.Media3D.Light>|Hafif hız (en hızlı en yavaş):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Ağ boyutlarını şu sınırlar altında tutmaya çalışın:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20.001 <xref:System.Windows.Media.Media3D.Point3D> örnekleri<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60.003 <xref:System.Int32> örnekleri|  
|<xref:System.Windows.Media.Media3D.Material>|Malzeme hızı (en hızlı en yavaş):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B, görünmez fırçalardan (siyah çevresel fırçalar, şifresiz Fırçalar vb.) tutarlı bir şekilde geri almaz.  Bunları sahninizden kaldırmayı göz önünde bulundurun.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Bir <xref:System.Windows.Media.Media3D.MaterialGroup> içindeki her <xref:System.Windows.Media.Media3D.Material> başka bir işleme geçişine neden olur. bu nedenle, çok sayıda malzeme dahil, hatta basit malzemeler dahil olmak üzere GPU 'inizdeki Fill taleplerini önemli ölçüde artırabilir  <xref:System.Windows.Media.Media3D.MaterialGroup>malzemelerin sayısını en aza indirin.|  
  
## <a name="performance-impact-low"></a>Performans etkisi: düşük  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Animasyon veya veri bağlamaya ihtiyaç duymazsanız, birden çok dönüşüm içeren bir dönüşüm grubu kullanmak yerine tek bir <xref:System.Windows.Media.Media3D.MatrixTransform3D>kullanın, bu, başka bir şekilde dönüşüm grubunda bağımsız olarak mevcut olacak tüm dönüşümler ürün olarak ayarlanıyor.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahnedeki ışıkların sayısını en aza indirin. Sahnede çok fazla ışık, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazılım işlemeye geri dönmesine zorlayacaktır.  Sınırlar 110 <xref:System.Windows.Media.Media3D.DirectionalLight> nesneler, 70 <xref:System.Windows.Media.Media3D.PointLight> nesneler veya 40 <xref:System.Windows.Media.Media3D.SpotLight> nesneleri.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Nesneleri ayrı <xref:System.Windows.Media.Media3D.ModelVisual3D> örneklerine yerleştirerek, nesneleri statik nesnelerden ayırın.  Dönüştürülmüş sınırları önbelleğe aldığından, ModelVisual3D "daha ağır" <xref:System.Windows.Media.Media3D.GeometryModel3D>.  Geometrymodel3d 'nin geometrisini bir model olarak iyileştirilir; ModelVisual3D bir sahne düğümü olacak şekilde iyileştirilmiştir.  Geometrymodel3d 'nin geometrisini paylaşılan örneklerini sahneye koymak için ModelVisual3D kullanın.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahnede ışıkların sayısını değiştirme sayısını en aza indirin.  Her ışık sayısı değişikliği, yapılandırma daha önce mevcut olmadığı ve bu nedenle kendi gölgelendiriciye sahip olmadığı müddetçe bir gölgelendirici yeniden oluşturma ve yeniden derlemeyi zorlar.|  
|Ampul|Siyah Işıklar görünmez, ancak işleme süresine eklenir; bunları dışarıda bırakmayı düşünün.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bir MeshGeometry3D's <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>ve <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>gibi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]büyük koleksiyonların oluşturma süresini en aza indirmek için, değer popülasyonu öncesinde koleksiyonları önceden boyutlandırın. Mümkünse, koleksiyonların oluşturucuları, diziler veya listeler gibi önceden doldurulmuş veri yapılarını geçirin.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)

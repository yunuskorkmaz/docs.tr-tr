---
title: WPF 3B Performansını En Üst Düzeye Çıkarma
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: e1a90406423e36dd10b8b108e076fe73f99947f0
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133856"
---
# <a name="maximize-wpf-3d-performance"></a>WPF 3B Performansını En Üst Düzeye Çıkarma
' Yi kullanarak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B denetimleri oluşturun ve uygulamalarınıza 3B sahneler ekleyin, performans iyileştirmesini göz önünde bulundurmanız önemlidir. Bu konu, uygulamanız için performans etkilerine sahip 3B sınıfların ve özelliklerin bir listesini ve bunları kullanırken performansı iyileştirmeye yönelik önerileri sağlar.  
  
 Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B özellikleri hakkında gelişmiş bir anlama olduğunu varsayar. Bu belgedeki öneriler, "işleme katmanı 2" için geçerlidir (kabaca, pixel shader sürüm 2,0 ve köşe gölgelendirici sürüm 2,0 ' ni destekleyen donanımlar). Daha ayrıntılı bilgi için bkz. [grafik Işleme katmanları](../advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Performans etkisi: Yüksek  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Fırça hızı (en hızlı en yavaş):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>alındığından<br /><br /> <xref:System.Windows.Media.VisualBrush>alındığından<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>önbelleğe alınmamış<br /><br /> <xref:System.Windows.Media.VisualBrush>önbelleğe alınmamış|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Bir `Viewport3D.ClipToBounds` Viewport3D'sdikdörtgenininiçeriğiniaçıkçakırpmanızgerekmiyorsa<xref:System.Windows.Controls.Viewport3D> false olarak ayarlayın. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]kötü diğer ad kırpma çok yavaş olabilir ve `ClipToBounds` <xref:System.Windows.Controls.Viewport3D>varsayılan olarak etkin (yavaş) olur.|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Fare `Viewport3D.IsHitTestVisible` isabet testi gerçekleştirirken bir <xref:System.Windows.Controls.Viewport3D> içeriğini düşünmeniz gerekmiyorsa [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] false olarak ayarlayın.  3B içerik için isabet testi, yazılımda yapılır ve büyük kafeslerde yavaş olabilir. <xref:System.Windows.UIElement.IsHitTestVisible%2A>, varsayılan <xref:System.Windows.Controls.Viewport3D>olarak etkin (yavaş).|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Yalnızca farklı malzemeler veya dönüşümler gerektiren farklı modeller oluşturun.  Aksi takdirde, aynı malzemelerle <xref:System.Windows.Media.Media3D.GeometryModel3D> çok sayıda örnek birleşim ve dönüştürmeleri birkaç büyük <xref:System.Windows.Media.Media3D.GeometryModel3D> ve <xref:System.Windows.Media.Media3D.MeshGeometry3D> örneğe dönüştüren şekilde deneyin.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Kafes animasyonu — her bir kafesin kare temelinde tek tek köşelerin değiştirilmesi, içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]her zaman etkili değildir.  Her köşe değiştirildiğinde değişiklik bildirimlerinin performans etkisini en aza indirmek için, köşe başına değişiklik yapmadan önce kafesi görsel ağaçtan ayırın.  Ağ değiştirildikten sonra görsel ağaca yeniden iliştirin.  Ayrıca, bu şekilde canlandırılacak kafeslerin boyutunu en aza indirmeye çalışın.|  
|3B düzgünleştirme|İşleme hızını artırmak için iliştirilmiş özelliği <xref:System.Windows.Controls.Viewport3D> <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> ' ye `Aliased`ayarlayarak bir üzerinde çoklu örnekleme 'yı devre dışı bırakın.  Varsayılan olarak, 3B düzgünleştirme, her piksel için 4 örnek içeren Windows üzerinde etkindir.|  
|Metin|3B sahnede canlı metin ( <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush>içinde olduğu için) yavaş olabilir. Metin değişmediği takdirde (aracılığıyla <xref:System.Windows.Media.Imaging.RenderTargetBitmap>) metnin görüntülerini kullanmayı deneyin.|  
|<xref:System.Windows.Media.TileBrush>|Fırçanın içeriği statik olmadığı için <xref:System.Windows.Media.VisualBrush> 3B sahnede a veya a <xref:System.Windows.Media.DrawingBrush> kullanmanız gerekiyorsa, fırçayı önbelleğe almayı deneyin (ekli özelliği <xref:System.Windows.Media.RenderOptions.CachingHint%2A> ' ye `Cache`ayarlayarak).  En düşük ve en yüksek ölçek eşiği ayarlama eşiklerini (iliştirilmiş özelliklerle <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>birlikte) ayarlayın, böylece, istenen kalite düzeyini sürdürirken, önbelleğe alınmış fırçaların çok sık yeniden üretilmemesi sağlanır.  Varsayılan <xref:System.Windows.Media.DrawingBrush> olarak ve <xref:System.Windows.Media.VisualBrush> önbelleğe alınmaz, yani fırçayla boyanmış bir şeyin yeniden oluşturulması gereken her şey, fırçanın tüm içeriğinin bir ara yüzeye yeniden işlenmesi gerekir.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>etkilenen tüm içerikleri donanım hızlandırma olmadan işlenecek şekilde zorlar.  En iyi performans için kullanmayın <xref:System.Windows.Media.Effects.BitmapEffect>.|  
  
## <a name="performance-impact-medium"></a>Performans etkisi: Orta  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bir ağ, paylaşılan köşelerle bir çift üçgen olarak tanımlandığında ve bu köşeler aynı konuma, normal ve doku koordinatlarına sahip olduğunda, her bir paylaşılan köşeyi yalnızca bir kez tanımlayın ve sonra da üçgenlerinizi ile <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>dizine göre tanımlayın.|  
|<xref:System.Windows.Media.ImageBrush>|Boyut üzerinde (bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve/ <xref:System.Windows.Media.ImageBrush>veya ' i kullanırken) kesin denetim varsa doku boyutlarını en aza indirmenize çalışın.  Daha düşük çözünürlüklü dokuların görsel kalitesini azalyacağını unutmayın, bu nedenle kalite ve performans arasındaki doğru dengeyi bulmayı deneyin.|  
|Opaklık|Yarı saydam 3B içeriğini (örneğin, yansıma) işlerken, 1 ' den küçük bir <xref:System.Windows.Media.Brush.Opacity%2A> değere ayarlayarak `Viewport3D.Opacity` ayrı bir yarı saydam <xref:System.Windows.Controls.Viewport3D> oluşturmak <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>yerine fırçalar veya malzemeler üzerinde opaklık özelliklerini (veya aracılığıyla) kullanın.|  
|<xref:System.Windows.Controls.Viewport3D>|Sahnede kullandığınız <xref:System.Windows.Controls.Viewport3D> nesne sayısını en aza indirin.  Her bir model için ayrı Viewport3D örnekleri oluşturmak yerine aynı Viewport3D birçok 3B model yerleştirin.|  
|<xref:System.Windows.Freezable>|Genellikle, <xref:System.Windows.Media.Media3D.MeshGeometry3D> <xref:System.Windows.Media.Media3D.GeometryModel3D>, fırçalar ve malzemeler kullanmak faydalıdır.  All, öğesinden `Freezable`türetildiklerinden beri multiparentable.|  
|<xref:System.Windows.Freezable>|Özellikleri uygulamanızda <xref:System.Windows.Freezable.Freeze%2A> değişmeden kalacaksa, Freezable nesneleri üzerindeki yöntemi çağırın.  Dondurma, çalışma kümesini azaltabilir ve hızı artırabilir.|  
|<xref:System.Windows.Media.Brush>|Fırçanın <xref:System.Windows.Media.ImageBrush> içeriği değişmeyecektir <xref:System.Windows.Media.VisualBrush> veya <xref:System.Windows.Media.DrawingBrush> bunun yerine kullanın.  2B içerik bir <xref:System.Windows.Controls.Image> ile <xref:System.Windows.Media.Imaging.RenderTargetBitmap> öğesine dönüştürülebilir <xref:System.Windows.Media.ImageBrush>ve daha sonra ' de kullanılabilir.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Gerçekten arka <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> yüzlerini <xref:System.Windows.Media.Media3D.GeometryModel3D>görmeniz gerekmiyorsa kullanmayın.|  
|<xref:System.Windows.Media.Media3D.Light>|Hafif hız (en hızlı en yavaş):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Ağ boyutlarını şu sınırlar altında tutmaya çalışın:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20.001 <xref:System.Windows.Media.Media3D.Point3D> örnek<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60.003 <xref:System.Int32> örnek|  
|<xref:System.Windows.Media.Media3D.Material>|Malzeme hızı (en hızlı en yavaş):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3B, görünmez fırçaların (siyah çevresel fırçalar, şifresiz Fırçalar vb.) tutarlı bir şekilde devre dışı kalmıyor.  Bunları sahninizden kaldırmayı göz önünde bulundurun.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Her <xref:System.Windows.Media.Media3D.Material> biri başka <xref:System.Windows.Media.Media3D.MaterialGroup> bir işleme geçişine neden olur. bu nedenle, çok sayıda malzeme, hatta basit malzemeler dahil olmak üzere, GPU 'inizdeki Fill taleplerini önemli ölçüde artırabilir.  İçindeki malzeme sayısını en aza indirin <xref:System.Windows.Media.Media3D.MaterialGroup>.|  
  
## <a name="performance-impact-low"></a>Performans etkisi: Düşük  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Birden çok dönüşüm içeren bir dönüşüm grubu kullanmak yerine, animasyon veya veri bağlama gerekmez, tek <xref:System.Windows.Media.Media3D.MatrixTransform3D>bir kullanın, başka bir şekilde dönüşüm grubunda bağımsız olarak mevcut olacak tüm dönüşümler ürün olarak ayarlanıyor.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahnedeki ışıkların sayısını en aza indirin. Sahnede çok fazla ışık yazılım işlemeye geri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dönmesine zorlayacaktır.  Sınırlar kabaca 110 <xref:System.Windows.Media.Media3D.DirectionalLight> nesne, 70 <xref:System.Windows.Media.Media3D.PointLight> nesne veya 40 <xref:System.Windows.Media.Media3D.SpotLight> nesnelerdir.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Nesneleri ayrı <xref:System.Windows.Media.Media3D.ModelVisual3D> örneklere yerleştirerek, nesneleri statik nesnelerden ayırın.  ModelVisual3D, dönüştürülmüş sınırları önbelleğe aldığından, <xref:System.Windows.Media.Media3D.GeometryModel3D> "daha ağır" bir değer.  Geometrymodel3d 'nin geometrisini bir model olarak iyileştirilir; ModelVisual3D bir sahne düğümü olacak şekilde iyileştirilmiştir.  Geometrymodel3d 'nin geometrisini paylaşılan örneklerini sahneye koymak için ModelVisual3D kullanın.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahnede ışıkların sayısını değiştirme sayısını en aza indirin.  Her ışık sayısı değişikliği, yapılandırma daha önce mevcut olmadığı ve bu nedenle kendi gölgelendiriciye sahip olmadığı müddetçe bir gölgelendirici yeniden oluşturma ve yeniden derlemeyi zorlar.|  
|Ampul|Siyah Işıklar görünmez, ancak işleme süresine eklenir; bunları dışarıda bırakmayı düşünün.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Bir MeshGeometry3D's <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>, ,<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> vegibi<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>büyük koleksiyonların yapı süresini en aza indirmek için, değer popülasyonu öncesinde koleksiyonları önceden boyutlandırın. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Mümkünse, koleksiyonların oluşturucuları, diziler veya listeler gibi önceden doldurulmuş veri yapılarını geçirin.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)

---
title: 3B Performansı En Üst Düzeye Çıkarın
ms.date: 03/30/2017
helpviewer_keywords:
- 3D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 3825ea8e57c6863e2ee654072efda623db21c2a8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112004"
---
# <a name="maximize-wpf-3d-performance"></a>WPF 3B Performansını En Üst Düzeye Çıkarma
3B denetimler oluşturmak ve uygulamalarınızda 3B sahneler eklemek [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] için kullandığınızdan, performans optimizasyonu dikkate almak önemlidir. Bu konu, uygulamanız için performans etkileri olan 3B sınıfların ve özelliklerin yanı sıra bunları kullandığınızda performansı en iyi duruma getiren önerilerin bir listesini sağlar.  
  
 Bu konu, 3B [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özelliklerin gelişmiş bir şekilde anlaşılmasını varsayar. Bu belgedeki öneriler, kabaca piksel gölgeli sürüm 2.0 ve vertex shader sürüm 2.0'ı destekleyen donanım olarak tanımlanan "rendering tier 2" için geçerlidir. Daha fazla bilgi için [Grafik Oluşturma Katmanları'na](../advanced/graphics-rendering-tiers.md)bakın.  
  
## <a name="performance-impact-high"></a>Performans Etkisi: Yüksek  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Fırça hızı (en hızlıdan en yavaşa):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(önbelleğe alınmış)<br /><br /> <xref:System.Windows.Media.VisualBrush>(önbelleğe alınmış)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(önlenmemiş)<br /><br /> <xref:System.Windows.Media.VisualBrush>(önlenmemiş)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Viewport3D'nin dikdörtgenine `Viewport3D.ClipToBounds` [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a <xref:System.Windows.Controls.Viewport3D> içeriği açıkça kesmeniz gerekmediğinde false olarak ayarlayın. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]antialiased kırpma çok yavaş olabilir `ClipToBounds` ve varsayılan olarak (yavaş) <xref:System.Windows.Controls.Viewport3D>etkindir.|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Fare `Viewport3D.IsHitTestVisible` isabet testi yaparken içeriği [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Viewport3D> göz önünde bulundurmanız gerekmediğinde false olarak ayarlayın.  Hit test 3D içerik yazılım yapılır ve büyük meshes ile yavaş olabilir. <xref:System.Windows.UIElement.IsHitTestVisible%2A>üzerinde varsayılan <xref:System.Windows.Controls.Viewport3D>olarak etkin (yavaş)|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Farklı modelleri yalnızca farklı Malzemeler veya Dönüşümler gerektirdiğinde oluşturun.  Aksi takdirde, aynı Malzemeler <xref:System.Windows.Media.Media3D.GeometryModel3D> ile birçok örnekleri birleştirmeyi deneyin ve <xref:System.Windows.Media.Media3D.GeometryModel3D> <xref:System.Windows.Media.Media3D.MeshGeometry3D> birkaç büyük ve örnekleri dönüştürür.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Kafes animasyonu-bir kafesin tek tek tepelerini kare başına olarak değiştirme- [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]her zaman verimli değildir.  Her tepe noktası değiştirildiğinde değişiklik bildirimlerinin performans etkisini en aza indirmek için, tepe başına değişiklik yapmadan önce kafesi görsel ağaçtan ayırın.  Kafes değiştirildikten sonra, onu görsel ağaca yeniden takın.  Ayrıca, bu şekilde animasyonlu olacak meshes boyutunu en aza indirmeye çalışın.|  
|3D Antialiasing|İşleme hızını artırmak için, bağlı özelliği <xref:System.Windows.Controls.Viewport3D> <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> ' ye `Aliased`ayarlayarak çoklu örneklemeyi devre dışı  Varsayılan olarak, 3B antialiasing piksel başına 4 örnek ile Windows'da etkinleştirilir.|  
|Metin|Bir 3B sahnede ki canlı metin (canlı <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>çünkü bir veya) yavaş olabilir. Metin değişmeyecekse, metnin <xref:System.Windows.Media.Imaging.RenderTargetBitmap>resimlerini (üzerinden) kullanmayı deneyin.|  
|<xref:System.Windows.Media.TileBrush>|Fırçanın içeriği <xref:System.Windows.Media.VisualBrush> statik <xref:System.Windows.Media.DrawingBrush> olmadığından bir veya 3B sahnede kullanmanız gerekiyorsa, fırçayı önbelleğe almayı <xref:System.Windows.Media.RenderOptions.CachingHint%2A> deneyin `Cache`(bağlı özelliği ayarı.  Önbelleğe alınan fırçaların çok sık yeniden oluşturulmayacak <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>şekilde minimum ve maksimum ölçek geçersiz alma eşiklerini (ekli özellikler ve) ayarlayın ve istediğiniz kalite düzeyini koruyun.  Varsayılan olarak <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> ve önbelleğe alınmaz, yani fırçayla boyanmış her şey yeniden işlenmesi gerektiğinde, fırçanın tüm içeriği önce bir ara yüzeye yeniden işlenmelidir.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>etkilenen tüm içeriği donanım ivmesi olmadan işlenmeyi zorlar.  En iyi performans için, kullanmayın. <xref:System.Windows.Media.Effects.BitmapEffect>|  
  
## <a name="performance-impact-medium"></a>Performans Etkisi: Orta  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bir kafes ortak vertices ile bitişik üçgenler olarak tanımlanır ve bu vertices aynı konuma sahip, normal ve doku koordinatları, her paylaşılan <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>vertex sadece bir kez tanımlayın ve sonra dizin ile üçgenler tanımlayın .|  
|<xref:System.Windows.Media.ImageBrush>|Boyut üzerinde açık denetime sahip olduğunuzda doku boyutlarını en aza <xref:System.Windows.Media.Imaging.RenderTargetBitmap> indirmeye <xref:System.Windows.Media.ImageBrush>çalışın (ve/veya bir tane kullanıyorsanız).  Daha düşük çözünürlüklü dokuların görsel kaliteyi azaltabileceğini unutmayın, bu nedenle kalite ve performans arasında doğru dengeyi bulmaya çalışın.|  
|Opak -lık|Yarı saydam 3B içeriği (yansımalar gibi) oluştururken, 1'den daha küçük <xref:System.Windows.Media.Brush.Opacity%2A> bir <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>değere ayarlayarak `Viewport3D.Opacity` ayrı <xref:System.Windows.Controls.Viewport3D> bir yarı saydam oluşturmak yerine fırçalar veya malzemeler (üzerinden veya) üzerindeki donukluk özelliklerini kullanın.|  
|<xref:System.Windows.Controls.Viewport3D>|Bir sahnede <xref:System.Windows.Controls.Viewport3D> kullandığınız nesne sayısını en aza indirin.  Her model için ayrı Viewport3D örnekleri oluşturmak yerine birçok 3B modeli aynı Viewport3D'ye koyun.|  
|<xref:System.Windows.Freezable>|Genellikle, Fırçalar ve Malzemeler <xref:System.Windows.Media.Media3D.MeshGeometry3D> <xref:System.Windows.Media.Media3D.GeometryModel3D>yeniden kullanmak için yararlıdır.  Hepsi çok ebeveynlidir, çünkü `Freezable`onlar.|  
|<xref:System.Windows.Freezable>|<xref:System.Windows.Freezable.Freeze%2A> Freezables'daki yöntemi, uygulamalarınızda özellikleri değişmeden kaldığında arayın.  Donma çalışma kümesini azaltabilir ve hızı artırabilir.|  
|<xref:System.Windows.Media.Brush>|Fırçanın <xref:System.Windows.Media.VisualBrush> içeriğinin değişmeyeceğinin yerine veya <xref:System.Windows.Media.DrawingBrush> ne zaman kullanılacağını kullanın. <xref:System.Windows.Media.ImageBrush>  2B içerik bir <xref:System.Windows.Controls.Image> via <xref:System.Windows.Media.Imaging.RenderTargetBitmap> dönüştürülebilir ve daha <xref:System.Windows.Media.ImageBrush>sonra bir .|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Arka yüzlerinizi <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> görmeniz gerekmedikçe kullanmayın. <xref:System.Windows.Media.Media3D.GeometryModel3D>|  
|<xref:System.Windows.Media.Media3D.Light>|Işık hızı (en hızlıdan en yavaşa):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Kafes boyutlarını bu sınırlar altında tutmaya çalışın:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20.001 <xref:System.Windows.Media.Media3D.Point3D> örnek<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60.003 <xref:System.Int32> örnek|  
|<xref:System.Windows.Media.Media3D.Material>|Malzeme hızı (en hızlıdan en yavaşa):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D, görünmez fırçaları (siyah ortam fırçaları, açık fırçalar, vb.) tutarlı bir şekilde devre dışı bırakmaz.  Bunları sahnenizden atlayıp kullanmayı düşünün.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Her <xref:System.Windows.Media.Media3D.Material> biri <xref:System.Windows.Media.Media3D.MaterialGroup> başka bir işleme geçişine neden olur, bu nedenle birçok malzeme, hatta basit malzemeler de dahil olmak üzere, GPU'nuzdaki dolgu taleplerini önemli ölçüde artırabilir.  Cihazınızdaki malzeme sayısını <xref:System.Windows.Media.Media3D.MaterialGroup>en aza indirin.|  
  
## <a name="performance-impact-low"></a>Performans Etkisi: Düşük  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Animasyon veya veri bağlama gerekmez, bunun yerine birden çok dönüşüm içeren bir <xref:System.Windows.Media.Media3D.MatrixTransform3D>dönüştürme grubu kullanarak, tek bir kullanın , aksi takdirde dönüştürme grubunda bağımsız olarak var olacak tüm dönüşümlerin ürünü olarak ayar.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahnenizdeki ışık sayısını en aza indirin. Bir sahnede çok fazla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ışık yazılım işleme geri düşmeye zorlar.  Sınırlar kabaca 110 <xref:System.Windows.Media.Media3D.DirectionalLight> nesne, 70 <xref:System.Windows.Media.Media3D.PointLight> nesne veya <xref:System.Windows.Media.Media3D.SpotLight> 40 nesnedir.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Separate moving objects from static objects by putting them in separate <xref:System.Windows.Media.Media3D.ModelVisual3D> instances.  ModelVisual3D dönüştürülmüş sınırları <xref:System.Windows.Media.Media3D.GeometryModel3D> önbelleğe çünkü "ağır" dır.  GeometryModel3D bir model olarak optimize edilsin; ModelVisual3D bir sahne düğümü olarak optimize edilsin.  GeometryModel3D'nin paylaşılan örneklerini sahneye koymak için ModelVisual3D'yi kullanın.|  
|<xref:System.Windows.Media.Media3D.Light>|Olay yerindeki ışık sayısını kaç kez değiştirdiğinizi en aza indirin.  Işık sayımının her değişimi, bu yapılandırma daha önce var olmadıkça (ve böylece gölgelendirmeönse) gölgeli bir rejenerasyon ve yeniden derlemeyi zorlar.|  
|Açık|Siyah ışıklar görünür olmayacaktır, ancak zaman işlemek için eklersiniz; onları atlayarak düşünün.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bir MeshGeometry3D gibi büyük [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]koleksiyonların inşaat süresini en <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>aza <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>indirmek <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>için, , , , ve , değer popülasyonönce koleksiyonları ön boyutu. Mümkünse, koleksiyonların oluşturucularını diziler veya Listeler gibi önceden doldurulmuş veri yapılarını geçirin.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)

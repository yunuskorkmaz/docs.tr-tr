---
title: "WPF 3B Performansını En Üst Düzeye Çıkarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45053762a4782544531a09c92531b26f99663016
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="maximize-wpf-3d-performance"></a>WPF 3B Performansını En Üst Düzeye Çıkarma
Kullandığınız gibi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B denetimleri oluşturmak ve 3B Sahne uygulamalarınızda dahil etmek için performans en iyi duruma getirme göz önünde bulundurmanız önemlidir. Bu konu, 3B sınıfları ve performans etkileri birlikte kullanıldıklarında performansını iyileştirmek için önerilerini uygulamanız için sahip özellikler listesini sağlar.  
  
 Gelişmiş anlaşıldığını bu konuda [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B özellikleri. Bu belgedeki öneriler "işleme katmanına 2" uygulamak — kabaca, piksel gölgelendirici sürüm 2.0 ve köşe gölgelendirici sürüm 2.0 destekleyen bir donanım tanımlanmış. Daha fazla ayrıntı için bkz: [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Performans etkisi: yüksek  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Fırça hızı (yavaş için hızlı):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(önbelleğe alınmış)<br /><br /> <xref:System.Windows.Media.VisualBrush>(önbelleğe alınmış)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(önbelleğe alınmamış)<br /><br /> <xref:System.Windows.Media.VisualBrush>(önbelleğe alınmamış)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Ayarlama `Viewport3D.ClipToBounds` olması gerekmez olduğunca false [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] açıkça içeriğini küçük bir <xref:System.Windows.Controls.Viewport3D> Viewport3D'ın dikdörtgen için. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]antialiased kırpma çok yavaş olabilir ve `ClipToBounds` (yavaş) varsayılan olarak etkin <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Ayarlama `Viewport3D.IsHitTestVisible` yüklemeniz gerekmez olduğunca false [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriğini dikkate alınması gereken bir <xref:System.Windows.Controls.Viewport3D> zaman gerçekleştirme Fare isabet testi.  İsabet testi 3D içerik yazılımda yapılır ve büyük kafesleri yavaş olabilir. <xref:System.Windows.UIElement.IsHitTestVisible%2A>(yavaş) varsayılan olarak etkin <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Yalnızca bunlar farklı malzeme ya da dönüşümler gerektirdiğinde farklı modelleri oluşturun.  Aksi takdirde, birçok birleşim çalıştığınızda <xref:System.Windows.Media.Media3D.GeometryModel3D> aynı malzemeler ve dönüşümler örnekleriyle birkaç büyük içine <xref:System.Windows.Media.Media3D.GeometryModel3D> ve <xref:System.Windows.Media.Media3D.MeshGeometry3D> örnekleri.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Animasyon kafes — çerçeve başına temelinde kafes tek tek köşe değiştirme — her zaman içinde etkin değilse [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Her köşe değiştirildiğinde değişiklik bildirimleri performans etkisini en aza indirmek için köşe başına değişiklik yapmadan önce görsel ağaç kafes kullanımdan çıkarın.  Mesh değiştirilmiş sonra görsel ağacına yeniden bağlayın.  Ayrıca, bu şekilde animasyonlu kafesleri boyutunu küçültmeyi deneyin.|  
|3B düzgünleştirme|İşleme hızını artırmak için düzgünleştirmek çoklu örnekleme devre dışı bir <xref:System.Windows.Controls.Viewport3D> ekli özellik ayarlayarak <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> için `Aliased`.  Varsayılan olarak, 3B düzgünleştirme devre dışı bırakıldı [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] ve etkin [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] piksel başına 4 örnekleri ile.|  
|Metin|3B Sahne metin Canlı (olduğu için Canlı bir <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush>) yavaş olabilir. Metin görüntülerini kullanmayı deneyin (aracılığıyla <xref:System.Windows.Media.Imaging.RenderTargetBitmap>) sürece metin değişir.|  
|<xref:System.Windows.Media.TileBrush>|Kullanmanız gerekiyorsa bir <xref:System.Windows.Media.VisualBrush> veya <xref:System.Windows.Media.DrawingBrush> fırça içeriği statik olduğundan, 3B Sahne fırça önbelleğe almayı deneyin (ekli özellik ayarı <xref:System.Windows.Media.RenderOptions.CachingHint%2A> için `Cache`).  Minimum ve maksimum ölçek geçersiz kılma eşikleri ayarlayın (ekli özellikler ile <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> ve <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) böylece önbelleğe alınmış Fırçalar çok sık istenen, kalite düzeyini hala koruyarak yeniden olmaz.  Varsayılan olarak, <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush> , her zaman bir şey fırça ile boyandığında yeniden oluşturulmuş olması gerekir, fırça tüm içeriğini ilk ara yüzeye yeniden oluşturulması gerekir, yani önbelleğe alınmaz.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>donanım hızlandırma işlenmek üzere tüm etkilenen içeriği zorlar.  En iyi performans için kullanmayın <xref:System.Windows.Media.Effects.BitmapEffect>.|  
  
## <a name="performance-impact-medium"></a>Performans etkisi: Orta  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bir ağ paylaşılan köşeleri üçgenle bitişik renklerin olarak tanımlanır ve bu köşeleri aynı konumda, normal ve doku koordinatlarına sahip olduğunda, her paylaşılan köşe yalnızca bir kez ve ardından, üçgenler diziniyle tarafından tanımlamaya <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>.|  
|<xref:System.Windows.Media.ImageBrush>|Doku boyutları boyutu üzerinde açık denetim olduğunda en aza indirmek deneyin (kullanırken bir <xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve/veya bir <xref:System.Windows.Media.ImageBrush>).  Daha düşük çözünürlük dokuları görsel kalite azaltmak, kalite ve performans arasında doğru dengeyi bulmak nedenle deneyin unutmayın.|  
|Opaklık|Yarı saydam 3B (yansımaları gibi) içerik işlenirken Fırçalar veya malzemeleri opaklık özelliklerini kullanın (aracılığıyla <xref:System.Windows.Media.Brush.Opacity%2A> veya <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) ayrı bir yarı saydam oluşturmak yerine <xref:System.Windows.Controls.Viewport3D> ayarlayarak `Viewport3D.Opacity` 1'den daha düşük bir değere.|  
|<xref:System.Windows.Controls.Viewport3D>|Sayısını en aza <xref:System.Windows.Controls.Viewport3D> Sahne kullanmakta olduğunuz nesneleri.  Her model için ayrı Viewport3D örnekleri oluşturma yerine aynı Viewport3D birçok 3B modelleri yerleştirin.|  
|<xref:System.Windows.Freezable>|Genellikle yeniden yararlı <xref:System.Windows.Media.Media3D.MeshGeometry3D>, <xref:System.Windows.Media.Media3D.GeometryModel3D>, Fırçalar ve malzemeleri.  Türetilmiş bu yana multiparentable tümü `Freezable`.|  
|<xref:System.Windows.Freezable>|Çağrı <xref:System.Windows.Freezable.Freeze%2A> özelliklerini kalacak zaman Freezables yöntemi değişmeden uygulamanızda.  Dondurma çalışma kümesi azaltın ve hızını artırır.|  
|<xref:System.Windows.Media.Brush>|Kullanım <xref:System.Windows.Media.ImageBrush> yerine <xref:System.Windows.Media.VisualBrush> veya <xref:System.Windows.Media.DrawingBrush> zaman fırça içeriğini değiştirmez.  2B içerik dönüştürülebilir bir <xref:System.Windows.Controls.Image> aracılığıyla <xref:System.Windows.Media.Imaging.RenderTargetBitmap> ve ardından kullanılan bir <xref:System.Windows.Media.ImageBrush>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|Kullanmayan <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> , bekleyen yüzler görmek gerçekten gerekli olmadıkça, <xref:System.Windows.Media.Media3D.GeometryModel3D>.|  
|<xref:System.Windows.Media.Media3D.Light>|Hafif hızı (yavaş için hızlı):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Bu sınırlar kafes boyutları tutmaya çalışın:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20,001 <xref:System.Windows.Media.Media3D.Point3D> örnekleri<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60,003 <xref:System.Int32> örnekleri|  
|<xref:System.Windows.Media.Media3D.Material>|Malzeme hızı (yavaş için hızlı):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3B görünmez Fırçalar dışında (siyah ortam Fırçalar, Temizle Fırçalar, vb.) tutarlı bir şekilde kabul etmez.  Bu, Sahne atlama göz önünde bulundurun.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Her <xref:System.Windows.Media.Media3D.Material> içinde bir <xref:System.Windows.Media.Media3D.MaterialGroup> kadar birçok malzemeleri dahil olmak üzere başka bir işleme geçişini neden bile basit malzemeler, dolgu taleplerine, GPU göre önemli ölçüde artırabilir.  İçinde malzemeleri sayısını en aza indirmek için <xref:System.Windows.Media.Media3D.MaterialGroup>.|  
  
## <a name="performance-impact-low"></a>Performans etkisi: düşük  
  
|Özellik|Öneri|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Animasyon gerekmez veya veri bağlama, birden çok dönüşümler içeren dönüştürme Grup kullanmak yerine tek bir kullanmak olduğunda <xref:System.Windows.Media.Media3D.MatrixTransform3D>, aksi takdirde dönüştürme grubunda bağımsız olarak düşünelim tüm dönüşümler ürün olması için ayarlama.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahne ışık sayısını en aza indirin. Bir görünüm içinde çok fazla ışık zorlayacağı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazılım işlemeye geri dönmesi için.  110 kısıtlamalardır kabaca <xref:System.Windows.Media.Media3D.DirectionalLight> nesneleri, 70 <xref:System.Windows.Media.Media3D.PointLight> nesneleri veya 40 <xref:System.Windows.Media.Media3D.SpotLight> nesneleri.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Ayrı ayrı koyarak statik nesnelerden nesneleri taşıma <xref:System.Windows.Media.Media3D.ModelVisual3D> örnekleri.  ModelVisual3D "daha ağır" den <xref:System.Windows.Media.Media3D.GeometryModel3D> dönüştürülmüş sınırları ön belleğe aldığından.  GeometryModel3D bir model olması için optimize edilmiştir; ModelVisual3D Sahne düğümü için optimize edilmiştir.  GeometryModel3D paylaşılan örneklerini Sahne yerleştirilecek ModelVisual3D kullanın.|  
|<xref:System.Windows.Media.Media3D.Light>|Sahne ışık sayısını değiştirme sayısını en aza indirin.  Açık sayısı her değişiklik, bu yapılandırma önceden var (ve dolayısıyla kendi gölgelendirici önbelleğe alınmış olan sürece) gölgelendirici yeniden oluşturma ve yeniden derlenmek zorlar.|  
|Açık|Siyah ışık görünmeyecektir, ancak bunlar işleme zamanı ekler; bunları atlama göz önünde bulundurun.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Büyük koleksiyonlarda yapım süresini en aza indirmek için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], MeshGeometry3D's gibi <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>, ve <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>, değer popülasyon önce koleksiyonları önceden boyutu. Mümkünse, koleksiyonları oluşturucular önceden doldurulmuş veri yapılarını dizileri veya listeleri gibi geçirin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)

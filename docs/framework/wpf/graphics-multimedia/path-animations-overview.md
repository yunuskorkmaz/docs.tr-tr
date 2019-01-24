---
title: Yol Animasyonlarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 610ef2721bef18e1cb1e87500a9dc9cf2729c867
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614263"
---
# <a name="path-animations-overview"></a>Yol Animasyonlarına Genel Bakış
<a name="introduction"></a> Bu konu, çıkış değerleri oluşturmak için bir geometrik yol kullanmanıza olanak sağlayan yol animasyonları tanıtır. Yol animasyonları, taşıma ve karmaşık yollar üzerindeki nesneler döndürmek için kullanışlıdır.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için aşina olmalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları özellikleri. Animasyon özelliklerine bir giriş için bkz [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Kullandığınız bir <xref:System.Windows.Media.PathGeometry> bir yol animasyonu tanımlamak için nesne da aşina olmalısınız <xref:System.Windows.Media.PathGeometry> ve farklı türde <xref:System.Windows.Media.PathSegment> nesneleri. Daha fazla bilgi için [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>Yol animasyonu nedir?  
 Yol animasyonu türüdür <xref:System.Windows.Media.Animation.AnimationTimeline> kullanan bir <xref:System.Windows.Media.PathGeometry> giriş olarak. Bir kaynak için ayar yerine veya özelliğe göre (From/To/By yaptığınız gibi animasyon) veya (anahtar-çerçeve animasyon için kullandığınız gibi) anahtar çerçeveler kullanarak, geometrik yol tanımlayın ve ayarlamak için kullanın `PathGeometry` yolu animasyonun özellik. Yol Animasyon ilerledikçe yolundan x, y ve açı bilgilerini okur ve çıktısını oluşturmak için bu bilgileri kullanır.  
  
 Yol animasyonları çok karmaşık bir yolda bir nesne animasyon için kullanışlıdır. Bir nesnenin yol kullanmaktır taşımak için tek yönlü bir <xref:System.Windows.Media.MatrixTransform> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> karmaşık bir yolda bir nesneyi dönüştürmek için. Aşağıdaki örnek bu tekniği kullanarak gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> animasyon uygulamak için nesne <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Düğmeye uygulanır ve eğik bir yolu boyunca taşımak neden olur. Çünkü <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliği `true`, dikdörtgen yol tanjantını döndürür.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Kullanılan yolu sözdizimi hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnekte bkz [yol işaretleme söz dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) genel bakış. Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Kullanarak bir özellik için bir yol animasyon uygulayabilirsiniz bir <xref:System.Windows.Media.Animation.Storyboard> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod kullanarak veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodda yöntemi. Yol animasyon oluşturmak için de kullanabilirsiniz bir <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özellikler için geçerlidir. Animasyonlara uygulama için farklı yöntemler hakkında daha fazla bilgi için bkz. [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Yol animasyon türü  
 Özellik değerlerini animasyonlar oluşturması nedeniyle farklı özellik türleri için farklı animasyon türü vardır. Alan özelliği oynatmak bir <xref:System.Double> (gibi <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği bir <xref:System.Windows.Media.TranslateTransform>), üreten bir animasyon kullandığınız <xref:System.Double> değerleri. Alan özelliği oynatmak bir <xref:System.Windows.Point>, üreten bir animasyon kullandığınız <xref:System.Windows.Point> değerleri ve benzeri.  
  
 Yol animasyon sınıfları ait <xref:System.Windows.Media.Animation> ad alanı ve şu adlandırma kuralını kullanır:  
  
 *\<türü >* `AnimationUsingPath`  
  
 Burada  *\<türü >* sınıfı canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki yol animasyon sınıfları sağlar.  
  
|Özellik türü|Karşılık gelen yol animasyon sınıfı|Örnek|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> oluşturur <xref:System.Windows.Media.Matrix> değerlerini kendi <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. İle kullanıldığında bir <xref:System.Windows.Media.MatrixTransform>, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> bir nesnenin yol taşıyabilirsiniz. Ayarlarsanız <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliği <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> için `true`, ayrıca yolun nesne döndürür.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> oluşturur <xref:System.Windows.Point> gelen x ve y-koordinatlarını değerleri kendi <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Kullanarak bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> alan özelliği oynatmak <xref:System.Windows.Point> değerleri, bir nesnenin yol taşıyabilirsiniz. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nesne döndüremez.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> oluşturur <xref:System.Double> değerlerini kendi <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Ayarlayarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> belirtebileceğiniz özelliği olup olmadığını <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> çıktı olarak x koordinatını, y koordinatını ya da yolun açısını kullanır. Kullanabileceğiniz bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> nesneyi döndürme veya x veya y ekseni taşımak için.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Yol animasyonu giriş  
 Her yol animasyon sınıfı sağlar bir <xref:System.Windows.Media.PathGeometry> özelliği, giriş belirtmek için. Yol animasyonu kullanan <xref:System.Windows.Media.PathGeometry> çıkış değerleri oluşturmak için. <xref:System.Windows.Media.PathGeometry> Sınıfı yay, eğriler ve satırlardan oluşan birden çok karmaşık şekiller açıklamanıza olanak sağlar.  
  
 Temelini bir <xref:System.Windows.Media.PathGeometry> koleksiyonudur <xref:System.Windows.Media.PathFigure> nesneleri; bu nesnelerin her şekil merkezinde açıkladığı için bu şekilde adlandırılmış <xref:System.Windows.Media.PathGeometry>. Her <xref:System.Windows.Media.PathFigure> bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> nesneleri, her biri bir parçası şekilde açıklar.  
  
 Parçaların birçok türü vardır.  
  
|Segment türü|Açıklama|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Elips yay iki nokta arasındaki oluşturur.|  
|<xref:System.Windows.Media.BezierSegment>|Üçüncü dereceden Bezier eğrisi iki nokta arasındaki oluşturur.|  
|<xref:System.Windows.Media.LineSegment>|İki nokta arasındaki bir satır oluşturur.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Üçüncü derece Bezier eğrileri bir dizi oluşturur.|  
|<xref:System.Windows.Media.PolyLineSegment>|Satırları bir dizi oluşturur.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|İkinci derece Bezier eğrileri bir dizi oluşturur.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|İkinci dereceden Bezier eğrisi oluşturur.|  
  
 Segmentte bir <xref:System.Windows.Media.PathFigure> segmentin son noktası sonraki kesimin başlangıç noktası olarak kullanan tek bir geometrik şekil birleştirilir. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Özelliği bir <xref:System.Windows.Media.PathFigure> içinden ilk segment çizilmez noktasını belirtir. Önceki kesime bitiş noktasında izleyen her bir kesim başlatır. Örneğin, bir dikey çizgi `10,50` için `10,150` ayarlayarak tanımlanabilir <xref:System.Windows.Media.PathFigure.StartPoint%2A> özelliğini `10,50` ve oluşturma bir <xref:System.Windows.Media.LineSegment> ile bir <xref:System.Windows.Media.LineSegment.Point%2A> özelliğini `10,150`.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> nesneleri bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ayarlamak için özel bir kısaltılmış sözdizimi kullanabilirsiniz <xref:System.Windows.Media.PathGeometry.Figures%2A> özelliği bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için [yol işaretleme söz dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) genel bakış.  
  
 Kullanılan yolu sözdizimi hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnekte bkz [yol işaretleme söz dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) genel bakış.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028)
- [Yol İşaretleme Söz Dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)

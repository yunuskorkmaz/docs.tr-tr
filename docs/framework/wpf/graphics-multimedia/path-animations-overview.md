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
ms.openlocfilehash: 466e22a5b40ddb4f3674422ac7620832b44be51d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="path-animations-overview"></a>Yol Animasyonlarına Genel Bakış
<a name="introduction"></a> Bu konu, çıkış değerlerini oluşturmak için geometrik yol kullanmanıza olanak yol animasyonları tanıtır. Yol animasyonları karmaşık yollarda nesneleri döndürme ve taşıma için kullanışlıdır.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için aşina olmalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları özellikleri. Animasyon özelliklerine giriş için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Kullandığınız çünkü bir <xref:System.Windows.Media.PathGeometry> yol animasyonu tanımlamak için nesneyi da aşina olmalısınız <xref:System.Windows.Media.PathGeometry> ve farklı türde <xref:System.Windows.Media.PathSegment> nesneleri. Daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>Yol animasyonu nedir?  
 Yol animasyonu türünde <xref:System.Windows.Media.Animation.AnimationTimeline> kullanan bir <xref:System.Windows.Media.PathGeometry> giriş olarak. Bir kaynak için ayarı yerine veya özelliği tarafından (From/To/By yaptığınız gibi animasyon) veya anahtar çerçeveler (anahtar çerçeve animasyon için kullandığınız gibi) kullanarak, geometrik yolunu tanımlayın ve ayarlamak için kullanın `PathGeometry` yolu animasyonun özellik. Yol Animasyon ilerledikçe yolundan x, y ve açı bilgilerini okur ve çıktısını oluşturmak için bu bilgileri kullanır.  
  
 Yol animasyonları çok karmaşık bir yolda bir nesne animasyonu için faydalıdır. Bir yol boyunca bir nesneyi kullanmaktır taşımak için tek yönlü bir <xref:System.Windows.Media.MatrixTransform> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> karmaşık bir yolda bir nesne dönüştürmek için. Aşağıdaki örnek, kullanarak bu tekniği gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> hale getirmeyi nesnesine <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Bir düğmeye uygulanan ve eğri bir yol boyunca taşımak neden olur. Çünkü <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliği ayarlanmış `true`, dikdörtgen yol tanjantını döndürür.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Kullanılan yol sözdizimi hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek, bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) genel bakış. Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Kullanarak bir özellik için bir yol animasyon uygulayabilirsiniz bir <xref:System.Windows.Media.Animation.Storyboard> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kod kullanarak veya <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodda yöntemi. Yol animasyonu oluşturmak için de kullanabilirsiniz bir <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özellikleri için geçerlidir. Animasyonları uygulamak için farklı yöntemler hakkında daha fazla bilgi için bkz: [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Yol animasyon türleri  
 Animasyon özellik değerleri oluşturması nedeniyle farklı özellik türleri için farklı animasyon türü vardır. Alan bir özelliği animasyon uygulamak için bir <xref:System.Double> (gibi <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği bir <xref:System.Windows.Media.TranslateTransform>), üreten bir animasyon kullandığınız <xref:System.Double> değerleri. Alan bir özelliği animasyon uygulamak için bir <xref:System.Windows.Point>, üreten bir animasyon kullandığınız <xref:System.Windows.Point> değerleri ve benzeri.  
  
 Yol animasyon sınıfları ait <xref:System.Windows.Media.Animation> ad alanı ve aşağıdaki adlandırma kuralını kullanın:  
  
 *\<türü >* `AnimationUsingPath`  
  
 Burada  *\<türü >* sınıfı canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki yol animasyon sınıfları sağlar.  
  
|Özellik türü|Karşılık gelen yol animasyon sınıfı|Örnek|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> oluşturur <xref:System.Windows.Media.Matrix> gelen değerleri kendi <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. İle kullanıldığında bir <xref:System.Windows.Media.MatrixTransform>, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> bir yol boyunca bir nesneyi taşıyabilirsiniz. Ayarlarsanız <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliği <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> için `true`, ayrıca yol Eğriler boyunca nesneyi döndürür.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> oluşturur <xref:System.Windows.Point> değerleri gelen x ve y-koordinatları, kendi <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Kullanarak bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> alan bir özelliği animasyon için <xref:System.Windows.Point> değerleri, bir yol boyunca bir nesneyi taşıyabilirsiniz. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nesneleri döndürülemiyor.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> oluşturur <xref:System.Double> gelen değerleri kendi <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Ayarlayarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> özelliği belirtebilirsiniz olup olmadığını <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> x koordinatını, y koordinatını ya da yolun açısını çıktı olarak kullanır. Kullanabileceğiniz bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> nesneyi döndürme veya x ekseni veya y ekseni taşımak için.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Yol animasyon girişi  
 Her yol animasyon sınıfı sağlayan bir <xref:System.Windows.Media.PathGeometry> kendi giriş belirtmek için özellik. Yol animasyonu kullanan <xref:System.Windows.Media.PathGeometry> çıkış değerleri oluşturmak için. <xref:System.Windows.Media.PathGeometry> Sınıfı yaylar, eğriler ve satırlardan oluşan birden çok karmaşık şekilleri açıklamaya olanak sağlar.  
  
 Merkezinde bir <xref:System.Windows.Media.PathGeometry> koleksiyonudur <xref:System.Windows.Media.PathFigure> nesneleri; bu nesnelerin her şekil merkezinde açıklar çünkü böylece adlı <xref:System.Windows.Media.PathGeometry>. Her <xref:System.Windows.Media.PathFigure> bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> nesneleri, şekil bir parçasını her biri açıklanmaktadır.  
  
 Birçok türde segment vardır.  
  
|Segment türü|Açıklama|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|İki nokta arasında elips bir yay oluşturur.|  
|<xref:System.Windows.Media.BezierSegment>|Bir küp Bezier eğrisini iki nokta arasındaki oluşturur.|  
|<xref:System.Windows.Media.LineSegment>|İki nokta arasında bir çizgi oluşturur.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Küp Bezier eğrileri bir dizi oluşturur.|  
|<xref:System.Windows.Media.PolyLineSegment>|Bir dizi satır oluşturur.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|İkinci derece Bezier eğrileri bir dizi oluşturur.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|İkinci dereceden Bezier eğrisi oluşturur.|  
  
 Segmentlerinde bir <xref:System.Windows.Media.PathFigure> uç noktası bir parçasının sonraki segmentin başlangıç noktası olarak kullanan tek bir geometrik şekil birleştirilir. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Özelliği bir <xref:System.Windows.Media.PathFigure> içinden ilk kesim çizilmez noktasını belirtir. Sonraki her segment önceki kesime uç noktada başlatır. Örneğin, dikey satırından `10,50` için `10,150` ayarlayarak tanımlanabilir <xref:System.Windows.Media.PathFigure.StartPoint%2A> özelliğine `10,50` ve oluşturma bir <xref:System.Windows.Media.LineSegment> ile bir <xref:System.Windows.Media.LineSegment.Point%2A> özellik ayarı `10,150`.  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> nesneleri bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ayarlamak için özel bir kısaltılmış sözdizimi kullanabilirsiniz <xref:System.Windows.Media.PathGeometry.Figures%2A> özelliği bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) genel bakış.  
  
 Kullanılan yol sözdizimi hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek, bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) genel bakış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Yol İşaretleme Söz Dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)

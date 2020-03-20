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
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181875"
---
# <a name="path-animations-overview"></a>Yol Animasyonlarına Genel Bakış
<a name="introduction"></a>Bu konu, çıktı değerleri oluşturmak için geometrik bir yol kullanmanızı sağlayan yol animasyonlarını tanıtır. Yol animasyonları, nesneleri karmaşık yollar boyunca taşımak ve döndürmek için yararlıdır.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için animasyon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine aşina olmalısınız. Animasyon özelliklerine giriş için [Animasyona Genel Bakış'a](animation-overview.md)bakın.  
  
 Bir yol <xref:System.Windows.Media.PathGeometry> animasyonu tanımlamak için bir nesne kullandığınızdan, aynı zamanda aşina <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.PathSegment> nesnelerin farklı türleri olmalıdır. Daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın.  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>Yol Animasyonu Nedir?  
 Yol animasyonu, a <xref:System.Windows.Media.Animation.AnimationTimeline> <xref:System.Windows.Media.PathGeometry> girişi olarak kullanan bir türdür. Kimden, To veya By özelliği (Kimden/To/By animasyonu için yaptığınız gibi) ayarlamak veya anahtar kareleri kullanmak (anahtar kare animasyonu için `PathGeometry` kullandığınız gibi) yerine, geometrik bir yol tanımlar ve yol animasyonunun özelliğini ayarlamak için kullanırsınız. Yol animasyonu ilerledikçe, yoldaki x, y ve açı bilgilerini okur ve çıktısını oluşturmak için bu bilgileri kullanır.  
  
 Yol animasyonları karmaşık bir yol boyunca bir nesneyi animasyon için çok yararlıdır. Bir nesneyi bir yol boyunca hareket <xref:System.Windows.Media.MatrixTransform> ettirmenin <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> bir yolu, bir nesneyi karmaşık bir yol boyunca dönüştürmek için a ve a kullanmaktır. Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform>. özelliğianimasyon nesnesini kullanarak bu tekniği gösterir. Bir <xref:System.Windows.Media.MatrixTransform> düğmeye uygulanır ve eğri bir yol boyunca hareket etmesini neden olur. <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> Özellik ayarlandığı için, `true`dikdörtgen yolun teğet boyunca döner.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Örnekte kullanılan yol sözdizimi hakkında daha fazla bilgi için [Yol İşaretleyici sözdizimine](path-markup-syntax.md) genel bakış bakın. Tam örnek için [Yol Animasyon Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)bakın.  
  
 Bir in <xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kodu kullanarak veya koddaki <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanarak bir özellik için bir yol animasyonu uygulayabilirsiniz. Bir yol animasyonu oluşturmak <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özele uygulamak için de kullanabilirsiniz. Animasyonları uygulamak için farklı yöntemler hakkında daha fazla bilgi için, [Emlak Animasyon Teknikleri Genel Bakış'a](property-animation-techniques-overview.md)bakın.  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>Yol Animasyon Türleri  
 Animasyonlar özellik değerleri oluşturduğundan, farklı özellik türleri için farklı animasyon türleri vardır. Bir <xref:System.Double> özelliği <xref:System.Windows.Media.TranslateTransform.X%2A> (örneğin, bir <xref:System.Windows.Media.TranslateTransform>özelliği) alan bir özelliği canlandırmak için, <xref:System.Double> değerler üreten bir animasyon kullanırsınız. Bir özelliği canlandırmak için , <xref:System.Windows.Point>değerler üreten <xref:System.Windows.Point> bir animasyon kullanırsınız ve böyle devam edin.  
  
 Yol animasyon sınıfları <xref:System.Windows.Media.Animation> ad alanına aittir ve aşağıdaki adlandırma kuralını kullanır:  
  
 * \<Tip>*`AnimationUsingPath`  
  
 * \<Tür>* sınıf animasyonları değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki yol animasyon sınıfları sağlar.  
  
|Özellik türü|Karşılık gelen yol animasyon sınıfı|Örnek|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.Matrix> kendi <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>değerlerinden değerler üretir. Bir <xref:System.Windows.Media.MatrixTransform>, a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> ile kullanıldığında bir nesneyi bir yol boyunca hareket ettirebilir. Özelliğini <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> `true`ayarlarsanız, nesneyi yolun eğrileri boyunca döndürür.  
  
 A, <xref:System.Windows.Media.Animation.PointAnimationUsingPath> <xref:System.Windows.Point> x- <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>ve y-koordinatlarından değerler üretir. Değerleri alan <xref:System.Windows.Media.Animation.PointAnimationUsingPath> <xref:System.Windows.Point> bir özelliği canlandırmak için a kullanarak, bir nesneyi bir yol boyunca taşıyabilirsiniz. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nesneleri döndüremez.  
  
 A, <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> <xref:System.Double> kendi <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>değerlerinden değerler üretir. <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> Özelliği ayarlayarak, x-koordinatını, y-koordinatını veya çıkış olarak yolun açısını <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> kullanıp kullanmadığını belirtebilirsiniz. A'yı <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> bir nesneyi döndürmek veya x ekseni veya y ekseni boyunca taşımak için kullanabilirsiniz.  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>Yol Animasyon Girişi  
 Her yol animasyon <xref:System.Windows.Media.PathGeometry> sınıfı, girişini belirtmek için bir özellik sağlar. Yol animasyonu, <xref:System.Windows.Media.PathGeometry> çıktı değerlerini oluşturmak için kullanır. Sınıf, <xref:System.Windows.Media.PathGeometry> yaylar, eğriler ve çizgilerden oluşan birden çok karmaşık figürü açıklamanızı sağlar.  
  
 Bir <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.PathFigure> nesnelerin kalbinde bir nesne koleksiyonudur; bu nesneler, her şekil 'de <xref:System.Windows.Media.PathGeometry>ayrı bir şekil açıkladığı için bu nesnelere bu şekilde adlandırılır. Her <xref:System.Windows.Media.PathFigure> biri, her <xref:System.Windows.Media.PathSegment> biri figürün bir kesimini açıklayan bir veya daha fazla nesneden oluşur.  
  
 Birçok segment türü vardır.  
  
|Segment Türü|Açıklama|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|İki nokta arasında eliptik bir yay oluşturur.|  
|<xref:System.Windows.Media.BezierSegment>|İki nokta arasında kübik Bezier eğrisi oluşturur.|  
|<xref:System.Windows.Media.LineSegment>|İki nokta arasında bir çizgi oluşturur.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Bir dizi kübik Bezier eğrisi oluşturur.|  
|<xref:System.Windows.Media.PolyLineSegment>|Bir dizi satır oluşturur.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Bir dizi kuadratik Bezier eğrisi oluşturur.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Bir kuadratik Bezier eğrisi oluşturur.|  
  
 A'daki <xref:System.Windows.Media.PathFigure> segmentler, bir sonraki parçanın başlangıç noktası olarak bir kesimin bitiş noktasını kullanan tek bir geometrik şekle ayrılır. Bir <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> özelliği, ilk kesimin çizildiği noktayı belirtir. Sonraki her segment önceki bölümün bitiş noktasında başlar. Örneğin, dikey bir `10,50` çizgi `10,150` özelliği <xref:System.Windows.Media.PathFigure.StartPoint%2A> ayarlayarak `10,50` ve <xref:System.Windows.Media.LineSegment> bir <xref:System.Windows.Media.LineSegment.Point%2A> özellik ayarı ile `10,150`bir tanımlanabilir.  
  
 Nesneler hakkında <xref:System.Windows.Media.PathGeometry> daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın.  
  
 'de, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Media.PathGeometry.Figures%2A> bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için [bkz.](path-markup-syntax.md)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Örnekte kullanılan yol sözdizimi hakkında daha fazla bilgi için [Yol İşaretleyici sözdizimine](path-markup-syntax.md) genel bakış bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yol Animasyon Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Yol Biçimlendirme Sözdizimi](path-markup-syntax.md)
- [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)

---
title: Dönüşümlere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: 84d52da4eb51256f9de898f4553136deb2d9ab0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566762"
---
# <a name="transforms-overview"></a>Dönüşümlere Genel Bakış
Bu konuda nasıl kullanılacağını açıklar [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> döndürme, ölçeklendirme, taşıma için sınıflar (çevirme) ve eğme <xref:System.Windows.FrameworkElement> nesneleri.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Bir dönüşüm nedir?  
 A <xref:System.Windows.Media.Transform> nasıl harita veya dönüştürme, bir koordinat noktasına başka bir koordinat tanımlar. Bu eşleme bir dönüşüm tarafından açıklanan <xref:System.Windows.Media.Matrix>, üç satır koleksiyonu üç sütunlarının sahip olduğu <xref:System.Double> değerleri.  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) satır ağırlıklı matrisleri kullanır. Vektörler satır vektörleri olarak, sütun vektörleri değil ifade edilir.  
  
 Aşağıdaki tabloda yapısını gösteren bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matris.  
  
### <a name="a-2-d-transformation-matrix"></a>2-D dönüştürme matrisi  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Varsayılan: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Varsayılan: 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Varsayılan: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Varsayılan: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Varsayılan: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Varsayılan: 0,0|1.0|  
  
 Matris değerlerini değiştirerek, döndürme, ölçeklendirme, eğme taşıyın ve (çevirme) bir nesne. Örneğin, üçüncü satırın ilk sütunundaki değeri değiştirin ( <xref:System.Windows.Media.Matrix.OffsetX%2A> değeri) 100'e bunu nesneyi 100 birim x ekseni boyunca taşımak için kullanabilirsiniz. İkinci satırın ikinci sütunundaki değeri 3 değiştirirseniz, bir nesneyi üç kez geçerli yüksekliğiyle uzatmak için kullanabilirsiniz. Her iki değeri değiştirirseniz, nesneyi 100 birim x ekseni boyunca taşıyın ve yüksekliğinin 3 faktörüyle uzatma. Windows Presentation Foundation (WPF) yalnızca afin dönüşümler desteklediğinden, sağdaki sütundaki değerleri her zaman 0, 0, 1.  
  
 Windows Presentation Foundation (WPF) doğrudan matris değerlerini yönetmenize olanak sağlar, ancak Ayrıca birkaç sağlar <xref:System.Windows.Media.Transform> temel matris yapısının nasıl yapılandırıldığını bilmeden bir nesneyi dönüştürmenizi etkinleştiren sınıfları. Örneğin, <xref:System.Windows.Media.ScaleTransform> sınıfı ayarlayarak nesneyi ölçeklendirmenizi sağlar, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> bir dönüştürme matrisi düzenleme yerine özellikleri. Benzer şekilde, <xref:System.Windows.Media.RotateTransform> sınıfı bir nesne yalnızca ayarlayarak döndürmenizi sağlar, <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Dönüşüm sınıfları  
 Windows Presentation Foundation (WPF) aşağıdakileri sağlar [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> sınıflar ortak dönüşüm işlemleri için:  
  
|örneği|Açıklama|Örnek|Çizim|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Bir öğe tarafından belirtilen döndüğü <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Nesne Döndürme](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Döndürme çizimi](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Bir öğe tarafından belirtilen ölçeklendirir <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> tutarlar.|[Öğe Ölçeklendirme](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Ölçeklendirme çizim](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Bir öğe tarafından belirtilen Eğer <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> tutarlar.|[Bir Öğeyi Eğme](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Çizim eğme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Taşır (çevirir) tarafından belirtilen bir öğe <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> tutarlar.|[Bir Öğeyi Çevirme](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Çeviri çizimi](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Daha karmaşık dönüşümleri oluşturmak için Windows Presentation Foundation (WPF) aşağıdaki iki sınıfı sağlar:  
  
|örneği|Açıklama|Örnek|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Grupları birden çok <xref:System.Windows.Media.TransformGroup> nesnelerini tek <xref:System.Windows.Media.Transform> , sonra Özellikler dönüştürmek için uygulayabilirsiniz.|[Nesneye Birden Çok Dönüşüm Uygulama](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Tarafından sağlanmayan özel dönüşümleri oluşturur <xref:System.Windows.Media.Transform> sınıfları. Kullandığınızda, bir <xref:System.Windows.Media.MatrixTransform>, Matrisi doğrudan düzenlersiniz.|[Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) de sağlar [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] dönüşümler. Daha fazla bilgi için bkz: <xref:System.Windows.Media.Media3D.Transform3D> sınıfı.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Ortak dönüştürme özellikleri  
 Nesneyi dönüştürmek için bir yoldur uygun bildirmek için <xref:System.Windows.Media.Transform> yazın ve nesne dönüştürme özelliğine uygulamak. Farklı türde nesne farklı tür dönüşüm özellikleri vardır. Aşağıdaki tabloda birçok yaygın olarak kullanılan Windows Presentation Foundation (WPF) türlerini ve bunların dönüşüm özellikleri listeler.  
  
|Tür|Dönüşüm özellikleri|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Dönüşümler ve koordinat sistemleri  
 Nesneyi dönüştürmek, yalnızca nesne dönüştürülmez, bu nesnenin bulunduğu koordinat dönüştürme. Varsayılan olarak, hedef nesnenin koordinat sistemi başlangıcı sırasında bir dönüştürme ortalanır: (0,0). Tek özel durum <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> çeviri efekti nerede ortalanır bakılmaksızın aynı olduğundan ayarlamak için bir merkez özelliği yoktur.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Shapes.Rectangle> öğesi, bir tür <xref:System.Windows.FrameworkElement>, kendi varsayılan merkezinde 45 derece (0, 0). Aşağıdaki çizimde döndürme etkisini gösterir.  
  
 ![45 derece döndürülen FrameworkElement &#40;0,0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
(0,0) noktasında 45 derece döndürülmüş bir dikdörtgen öğesi  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Varsayılan olarak, sol üst köşesindeki öğeyi döndürür (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, Ve <xref:System.Windows.Media.SkewTransform> sınıfları dönüştürmenin uygulandığı noktayı belirtmenizi sağlayan CenterX ve CenterY özelliklerini sağlar.  
  
 Sonraki örnekte de kullanır bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Shapes.Rectangle> öğesini 45 derece; ancak bu kez <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerinin böylece <xref:System.Windows.Media.RotateTransform> merkezine sahip (25, 25). Aşağıdaki çizimde döndürme etkisini gösterir.  
  
 ![45 derece döndürülen Geometry &#40;25, 25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
(25, 25) noktasında 45 derece döndürülmüş bir dikdörtgen öğesi  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>FrameworkElement dönüştürme  
 Dönüştürmeler uygulamak için bir <xref:System.Windows.FrameworkElement>, oluşturma bir <xref:System.Windows.Media.Transform> ve iki özelliklerden biri için geçerlidir, <xref:System.Windows.FrameworkElement> sınıfı sağlar:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Düzen geçişinden önce uygulanan bir dönüşüm. Dönüşüm uygulandıktan sonra Düzen sistemi dönüştürülmüş boyutunu ve konumunu öğesi işler.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> – Öğesinin görünümünü değiştirir, ancak Düzen geçişi tamamlandıktan sonra uygulanan bir dönüşüm. Kullanarak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği yerine <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği, başarım faydaları elde edebilirsiniz.  
  
 Hangi özelliği kullanmalısınız? Sağladığı performans avantajları nedeniyle kullanmak <xref:System.Windows.UIElement.RenderTransform%2A> özellikle kullandığınızda olası animasyonlu her özellik <xref:System.Windows.Media.Transform> nesneleri. Kullanım <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği ölçeklendirme, döndürme veya eğme ve öğenin dönüştürülmüş boyutu ayarlaması için üst öğenin gerektiğinde. İle kullanıldığında, Not <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği <xref:System.Windows.Media.TranslateTransform> nesneleri gibi görünüyor öğeler üzerinde hiçbir etkisi yoktur. Düzen sistemi, işleme bir parçası olarak özgün konumuna çevrilmiş öğeyi döndürür. olmasıdır.  
  
 Düzende hakkında ek bilgi için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md) genel bakış.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Örnek: FrameworkElement döndürme 45 dereceyi  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.RotateTransform> 45 derece saat yönünde bir düğmeyi döndürmek için. Düğme bulunan bir <xref:System.Windows.Controls.StackPanel> , diğer iki düğmesi vardır.  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.RotateTransform> (0, 0) noktası etrafında döndürür. Örnek bir merkezi değer belirtmediğinden düğmesi, sol üst köşe noktası hakkında (0, 0) döndürür. <xref:System.Windows.Media.RotateTransform> Uygulanan <xref:System.Windows.UIElement.RenderTransform%2A> özelliği. Aşağıdaki çizimde dönüşümün sonucunu gösterir.  
  
 ![RenderTransform kullanılarak dönüştürülen düğme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Sol üst köşeden 45 derece saat yönünde bir döndürme  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Sonraki örnek de kullanan bir <xref:System.Windows.Media.RotateTransform> düğmesi 45 derece saat yönünde, ancak aynı zamanda döndürmek için ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> için düğmesinin (0,5, 0,5). Değeri <xref:System.Windows.UIElement.RenderTransformOrigin%2A> düğme boyutuna göre bir özelliktir. Sonuç olarak, döndürme, sol üst köşe yerine düğmenin merkezine uygulanır. Aşağıdaki çizimde dönüşümün sonucunu gösterir.  
  
 ![Ortasından dönüştürülen düğme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Merkezi etrafında 45 derece saat yönünde bir döndürme  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği yerine <xref:System.Windows.UIElement.RenderTransform%2A> özelliği döndür düğmesi.  Bu düzen sistemi tarafından tam geçiş tetikleyen düğmesi düzenini etkileyen dönüştürmeyi neden olur. Sonuç olarak, düğme döndürülmüş ve boyutuna değiştiğinden sonra yeniden konumlandırılır. Aşağıdaki çizimde dönüşümün sonucunu gösterir.  
  
 ![LayoutTransform kullanılarak dönüştürülen düğme](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform düğmeyi döndürmek için kullanılır  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Dönüşümleri animasyon ekleme  
 Öğesinden devraldığı <xref:System.Windows.Media.Animation.Animatable> sınıfı, <xref:System.Windows.Media.Transform> sınıfları ettirilebilir. Animasyon uygulamak için bir <xref:System.Windows.Media.Transform>, animasyon istediğiniz özelliğine uyumlu bir türde bir animasyon uygulamak.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.DoubleAnimation> ile bir <xref:System.Windows.Media.RotateTransform> yapmak için bir <xref:System.Windows.Controls.Button> tıklandığında yerinde döndürme.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252). Animasyon hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable Özellikleri  
 Sınıfından devraldığı için <xref:System.Windows.Freezable> sınıfı, <xref:System.Windows.Media.Transform> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Transform> nesneleri olarak bildirilebilir [kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)artırmak için salt okunur yapılan birden fazla nesne arasında paylaşılan performans, kopyalanabilen ve iş parçacığı yapılan. Tarafından sağlanan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252)

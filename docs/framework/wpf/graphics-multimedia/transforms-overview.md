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
ms.openlocfilehash: 6f7cbd91be83c96b25248f87ddc377159ba39b64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762384"
---
# <a name="transforms-overview"></a>Dönüşümlere Genel Bakış
Bu konu nasıl kullanılacağını açıklar [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> döndürme, ölçeklendirme, taşımak için sınıflar (çevirme) ve eğme <xref:System.Windows.FrameworkElement> nesneleri.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Dönüşüm nedir?  
 A <xref:System.Windows.Media.Transform> harita veya noktaları bir koordinat alanından başka bir koordinat alanına dönüştürme işlemini tanımlar. Bu eşleme dönüştürme tarafından açıklanan <xref:System.Windows.Media.Matrix>, üç sütunlarını içeren üç satır koleksiyonu <xref:System.Double> değerleri.  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF), satır ağırlıklı matrisler kullanır. Vektör satır vektörleri olarak, sütun vektörleri ifade edilir.  
  
 Aşağıdaki tablo yapısını gösterir. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matris.  
  
### <a name="a-2-d-transformation-matrix"></a>Bir 2B bir dönüştürme matrisi  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Varsayılan: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Varsayılan: 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Varsayılan: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Varsayılan: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Varsayılan: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Varsayılan: 0.0|1.0|  
  
 Matris değerlerini işleyerek, döndürme, ölçeklendirme, eğme taşıyın ve (çevirme) bir nesne. Örneğin, üçüncü satırda ilk sütunundaki değeri değiştirin ( <xref:System.Windows.Media.Matrix.OffsetX%2A> değeri) 100'e, nesneyi 100 birim x ekseni boyunca taşımak için kullanabilirsiniz. İkinci satırın ikinci sütundaki değeri 3 olarak değiştirirseniz, üç kez geçerli yükseklik nesneye esnetme için kullanabilirsiniz. Her iki değeri değiştirirseniz, nesne 100 birim x ekseni boyunca taşımak ve 3 faktörüyle yükseklik esnetme. Windows Presentation Foundation (WPF), yalnızca afin dönüşümler'i desteklediğinden, sağdaki sütundaki değerleri her zaman 0, 0, 1.  
  
 Windows Presentation Foundation (WPF), matris değerlerini doğrudan yönetmenize olanak sağlar, ancak ayrıca bazı sağlar <xref:System.Windows.Media.Transform> matris temelindeki nasıl yapılandırıldığını farkında olmadan bir nesneyi dönüştürmek sağlayan sınıflar. Örneğin, <xref:System.Windows.Media.ScaleTransform> sınıf ayarlayarak bir nesneyi ölçeklendirmenizi sağlar, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> bir dönüştürme matrisi düzenleme yerine özellikleri. Benzer şekilde, <xref:System.Windows.Media.RotateTransform> sınıfı sağlar, yalnızca ayarlayarak bir nesneyi döndürmek kendi <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Dönüşüm sınıfları  
 Windows Presentation Foundation (WPF), aşağıdakileri sağlar [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> ortak dönüşüm işlemleri için sınıflar:  
  
|örneği|Açıklama|Örnek|Çizim|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Bir öğe tarafından belirtilen döndürür <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Nesne Döndürme](how-to-rotate-an-object.md)|![Döndürme çizimi](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Bir öğe tarafından belirtilen ölçeklendirir <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> tutarlarıdır.|[Öğe Ölçeklendirme](how-to-scale-an-element.md)|![Ölçeklendirme çizim](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Bir öğe tarafından belirtilen eğriltir <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> tutarlarıdır.|[Bir Öğeyi Eğme](how-to-skew-an-element.md)|![Çizim eğme](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Taşır (çevrilir) tarafından belirtilen öğenin <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> tutarlarıdır.|[Bir Öğeyi Çevirme](how-to-translate-an-element.md)|![Çeviri çizimi](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Windows Presentation Foundation (WPF), daha karmaşık dönüşümler oluşturmak için aşağıdaki iki sınıf sağlar:  
  
|örneği|Açıklama|Örnek|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Grupları birden çok <xref:System.Windows.Media.TransformGroup> nesnelerini tek <xref:System.Windows.Media.Transform> , ardından özellikleri dönüştürmek için uygulayabilirsiniz.|[Nesneye Birden Çok Dönüşüm Uygulama](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Tarafından sağlanmayan özel dönüştürmeler oluşturur <xref:System.Windows.Media.Transform> sınıfları. Kullandığınızda, bir <xref:System.Windows.Media.MatrixTransform>, bir matris doğrudan düzenlemezsiniz.|[Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) de sağlar [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] dönüşümler. Daha fazla bilgi için <xref:System.Windows.Media.Media3D.Transform3D> sınıfı.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Genel dönüşüm özellikleri  
 Bir nesneyi dönüştürmek için bir yoludur uygun bildirmek için <xref:System.Windows.Media.Transform> yazın ve nesne dönüştürme özelliğini uygulayın. Farklı türde nesne farklı türde dönüşüm özellikleri vardır. Aşağıdaki tabloda birçok yaygın olarak kullanılan Windows Presentation Foundation (WPF) türleri ve dönüştürme özelliklerini listeler.  
  
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
## <a name="transformations-and-coordinate-systems"></a>Dönüşümler ve koordinat sistemi  
 Bir nesneyi dönüştürdüğünüzde, nesnenin yalnızca dönüştürmeyen, koordinat bu nesnenin bulunduğu dönüştürün. Varsayılan olarak, bir dönüştürme kaynak hedef nesnenin koordinat sistemi ortalanır: (0,0). Tek özel durum <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> çeviri efekti burada ortalanır bağımsız olarak aynı olduğundan ayarlamak için bir merkez özelliği yoktur.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Shapes.Rectangle> öğesinde, bir tür <xref:System.Windows.FrameworkElement>, kendi varsayılan merkezinde 45 derece (0, 0). Aşağıdaki çizimde, döndürme etkisini gösterir.  
  
 ![FrameworkElement hakkında 45 derece döndürülmüş &#40;0,0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Bir dikdörtgen öğesi noktası (0,0) 45 derece döndürülmüş  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Varsayılan olarak, sol üst köşesinin öğeyi döndürür (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, Ve <xref:System.Windows.Media.SkewTransform> sınıfları dönüştürme uygulandığı noktayı belirtmenize olanak verir CenterX ve CenterY özellikleri sağlar.  
  
 Sonraki örnekte de kullanır bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Shapes.Rectangle> öğesini 45 derece; ancak bu kez <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özellikleri ayarlanır böylece <xref:System.Windows.Media.RotateTransform> merkezine sahip (25, 25). Aşağıdaki çizimde, döndürme etkisini gösterir.  
  
 ![45 derecenin döndürülen Geometry &#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
(25, 25) noktasında 45 derece döndürülmüş bir dikdörtgen öğesi  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>FrameworkElement dönüştürme  
 Dönüştürmeler uygulamak için bir <xref:System.Windows.FrameworkElement>, oluşturun bir <xref:System.Windows.Media.Transform> ve iki özelliklerden biri için geçerli olan <xref:System.Windows.FrameworkElement> sınıfı sağlar:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Düzen geçişinden önce uygulanır dönüştürmesi. Dönüştürme uygulandıktan sonra dönüştürülen boyutunu ve konumunu öğesinin düzen sistemi işler.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A> Öğesinin görünümünü değiştirir ancak Düzen geçişi tamamlandıktan sonra uygulanır dönüştürmesi. Kullanarak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği yerine <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği performans avantajlarını elde edebilirsiniz.  
  
 Hangi özelliğin kullanmalısınız? Sağladığı performans avantajlarını nedeniyle <xref:System.Windows.UIElement.RenderTransform%2A> animasyonlu özellikle kullandığınızda, mümkün olduğunda özellik <xref:System.Windows.Media.Transform> nesneleri. Kullanım <xref:System.Windows.FrameworkElement.LayoutTransform%2A> ölçekleme, döndürme veya eğriltme sırasında özellik ve gerektiğinde dönüştürülmüş öğenin boyutunu için ayarlanacak öğenin üst. İle kullanıldığında, Not <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği <xref:System.Windows.Media.TranslateTransform> nesneleri görünür öğeler üzerinde hiçbir etkisi yoktur. Düzen sistemi, işleme bir parçası olarak özgün konumuna çevrilmiş öğeyi döndürür. olmasıdır.  
  
 Düzende hakkında ek bilgi için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bkz: [Düzen](../advanced/layout.md) genel bakış.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Örnek: FrameworkElement döndürme 45 derece  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.RotateTransform> 45 derece saat yönünde bir düğme döndürmek için. Düğme bulunan bir <xref:System.Windows.Controls.StackPanel> , diğer iki düğme vardır.  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.RotateTransform> noktası hakkında (0, 0) döndürür. Örnek bir orta değer belirtmediğinden düğmenin sol üst köşe olan noktası hakkında (0, 0) döndürür. <xref:System.Windows.Media.RotateTransform> Uygulanan <xref:System.Windows.UIElement.RenderTransform%2A> özelliği. Aşağıdaki çizimde, dönüştürme sonucunu gösterir.  
  
 ![RenderTransform kullanılarak dönüştürülen düğme](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Sol üst köşesinden 45 derece saat yönünde bir döndürme  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Sonraki örnekte de kullanan bir <xref:System.Windows.Media.RotateTransform> 45 derece saat yönünde bir düğme, ancak aynı zamanda döndürmek için ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> düğmenin (0,5, 0,5). Değerini <xref:System.Windows.UIElement.RenderTransformOrigin%2A> düğmeyi boyutuna göre bir özelliktir. Sonuç olarak, dönüş Merkezi yerine, sol üst köşesindeki düğmeye uygulanır. Aşağıdaki çizimde, dönüştürme sonucunu gösterir.  
  
 ![Dönüştürülen ortasından düğme](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Center etrafında 45 derece saat yönünde bir döndürme  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Aşağıdaki örnekte <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği yerine <xref:System.Windows.UIElement.RenderTransform%2A> düğmeyi döndürmek için özellik.  Bu düzen sistemi tarafından tam geçiş tetikleyen düğmenin düzeni etkilemesi dönüşümü neden olur. Sonuç olarak, düğmeyi döndürülmüş ve boyutunu değiştiği için sonra yeniden konumlandırılır. Aşağıdaki çizimde, dönüştürme sonucunu gösterir.  
  
 ![LayoutTransform kullanılarak dönüştürülen düğme](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Döndür düğmesi için kullanılan LayoutTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Dönüşümler animasyon ekleme  
 Devralındığı çünkü <xref:System.Windows.Media.Animation.Animatable> sınıfı <xref:System.Windows.Media.Transform> sınıfları ettirilebilir. Animasyon uygulamak için bir <xref:System.Windows.Media.Transform>, animasyon uygulamak istediğiniz özelliğine uyumlu bir türe ilişkin bir animasyon uygulayın.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.DoubleAnimation> ile bir <xref:System.Windows.Media.RotateTransform> yapmak için bir <xref:System.Windows.Controls.Button> döndürme tıklandığında bir yerde.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252). Animasyonlar hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable Özellikleri  
 Öğesinden devralındığından <xref:System.Windows.Freezable> sınıfı <xref:System.Windows.Media.Transform> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Transform> nesneleri olarak bildirilebilir [kaynakları](../advanced/xaml-resources.md)geliştirmek için salt okunur yapılan birden fazla nesne arasında paylaşılan performans, kopyalanan ve iş parçacığı açısından güvenli hale. Tarafından sağlanan farklı özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> nesneleri bkz [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Nasıl Yapılır Konuları](transformations-how-to-topics.md)
- [2B dönüşümleri örneği](https://go.microsoft.com/fwlink/?LinkID=158252)

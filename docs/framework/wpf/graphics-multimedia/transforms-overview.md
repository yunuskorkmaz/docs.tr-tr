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
ms.openlocfilehash: 49fb0109e1d7db065f7e241955f30cb038699020
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187461"
---
# <a name="transforms-overview"></a>Dönüşümlere Genel Bakış
Bu konu, <xref:System.Windows.Media.Transform> <xref:System.Windows.FrameworkElement> nesneleri döndürmek, ölçeklendirmek, taşımak (çevirmek) ve eğriltmek için 2-B sınıflarının nasıl kullanılacağını açıklar.  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>Dönüşüm Nedir?  
 A, <xref:System.Windows.Media.Transform> bir koordinat alanından başka bir koordinat alanına noktaların nasıl eşlenebildiğini veya dönüştürüldüğünü tanımlar. Bu <xref:System.Windows.Media.Matrix>eşleme, üç değer sütununa <xref:System.Double> sahip üç satırdan oluşan bir dönüşüm le açıklanır.  
  
> [!NOTE]
> Windows Sunu Temeli (WPF) satır-büyük matriskullanır. Vektörler sütun vektörleri olarak değil, satır vektörleri olarak ifade edilir.  
  
 Aşağıdaki tabloda bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matrisin yapısı gösterilmektedir.  
  
### <a name="a-2-d-transformation-matrix"></a>2-B dönüştürme matrisi  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Varsayılan: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Varsayılan: 0.0|0,0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Varsayılan: 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Varsayılan: 1.0|0,0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Varsayılan: 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Varsayılan: 0.0|1.0|  
  
 Matris değerlerini değiştirerek, bir nesneyi döndürebilir, ölçekleyebilir, çarpıtabilir ve taşıyabilir (çevirebilirsiniz). Örneğin, üçüncü satırın ilk sütunundaki değeri <xref:System.Windows.Media.Matrix.OffsetX%2A> (değer) 100 olarak değiştirirseniz, bir nesneyi x ekseni boyunca 100 birim taşımak için kullanabilirsiniz. İkinci satırın ikinci sütunundaki değeri 3 olarak değiştirirseniz, nesneyi geçerli yüksekliğinin üç katına çıkarmak için kullanabilirsiniz. Her iki değeri de değiştirirseniz, nesneyi x ekseni boyunca 100 birim hareket ettirir ve yüksekliğini 3 kat daha fazla uzatırsınız. Windows Sunu Temeli (WPF) yalnızca affine dönüşümlerini desteklediğinden, sağ sütundaki değerler her zaman 0, 0, 1'dir.  
  
 Windows Sunu Temeli (WPF) matris değerlerini doğrudan işlemenizi sağlasa da, temel matris yapısının nasıl yapılandırıldığı bilmeden nesneyi dönüştürmenizi sağlayan birkaç <xref:System.Windows.Media.Transform> sınıf da sağlar. Örneğin, <xref:System.Windows.Media.ScaleTransform> sınıf, dönüştürme matrisini işlemek yerine <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> bir nesneyi ve özelliklerini ayarlayarak ölçeklendirmenizi sağlar. Aynı şekilde, <xref:System.Windows.Media.RotateTransform> sınıf yalnızca özelliğini <xref:System.Windows.Media.RotateTransform.Angle%2A> ayarlayarak bir nesneyi döndürmenizi sağlar.  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>Sınıfları Dönüştür  
 Windows Sunu Temeli (WPF), ortak <xref:System.Windows.Media.Transform> dönüşüm işlemleri için aşağıdaki 2-B sınıfları sağlar:  
  
|Sınıf|Açıklama|Örnek|Illüstrasyon|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Bir öğeyi belirtilene <xref:System.Windows.Media.RotateTransform.Angle%2A>göre döndürür.|[Nesne Döndürme](how-to-rotate-an-object.md)|![Çizimi döndürme](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Bir öğeyi belirtilen <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> miktarlara göre ölçeklendirin.|[Öğe Ölçeklendirme](how-to-scale-an-element.md)|![Ölçek illüstrasyon](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Bir öğeyi belirtilen <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> tutarlara göre eğriltiyor.|[Bir Öğeyi Eğme](how-to-skew-an-element.md)|![Çarpık illüstrasyon](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Bir öğeyi belirtilen <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> miktarlara göre taşır (çevirir).|[Bir Öğeyi Çevirme](how-to-translate-an-element.md)|![İllüstrasyonu çevir](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Daha karmaşık dönüşümler oluşturmak için, Windows Sunu Temeli (WPF) aşağıdaki iki sınıfı sağlar:  
  
|Sınıf|Açıklama|Örnek|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Birden <xref:System.Windows.Media.TransformGroup> çok nesneyi, <xref:System.Windows.Media.Transform> daha sonra özellikleri dönüştürmek için uygulayabileceğiniz tek bir nesne olarak grupla.|[Nesneye Birden Çok Dönüşüm Uygulama](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Diğer <xref:System.Windows.Media.Transform> sınıflar tarafından sağverilmeyecek özel dönüşümler oluşturur. Bir <xref:System.Windows.Media.MatrixTransform>matrisi doğrudan manipüle emdiğinizde.|[Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Sunu Temeli (WPF) da 3-B dönüşümleri sağlar. Daha fazla bilgi <xref:System.Windows.Media.Media3D.Transform3D> için sınıfa bakın.  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>Ortak Dönüşüm Özellikleri  
 Bir nesneyi dönüştürmenin bir yolu, uygun <xref:System.Windows.Media.Transform> türü bildirmek ve nesnenin dönüştürme özelliğine uygulamaktır. Farklı türde nesnelerin farklı türde dönüşüm özellikleri vardır. Aşağıdaki tabloda, sık kullanılan birkaç Windows Presentation Foundation (WPF) türü ve bunların dönüştürme özellikleri listelenmiştir.  
  
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
## <a name="transformations-and-coordinate-systems"></a>Dönüşümler ve Koordinat Sistemleri  
 Bir nesneyi dönüştürdüğünüzde, sadece nesneyi değil, o nesnenin var olduğu koordinat alanını da dönüştürürsunuz. Varsayılan olarak, bir dönüştürme hedef nesnenin koordinat sisteminin kaynağında ortalanır: (0,0). Tek istisna; <xref:System.Windows.Media.TranslateTransform> a'nın <xref:System.Windows.Media.TranslateTransform> ayarladığı merkezi özellikleri yoktur, çünkü çeviri efekti ortalandığı yere bakılmaksızın aynıdır.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.RotateTransform> varsayılan merkezi <xref:System.Windows.Shapes.Rectangle> (0, 0) hakkında 45 derece ile bir <xref:System.Windows.FrameworkElement>tür, bir öğeyi döndürmek için a kullanır. Aşağıdaki resimde döndürmenin etkisi gösterilmektedir.  
  
 ![Bir FrameworkElement yaklaşık 0,0 &#40;&#41;45 derece döndü](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Bir Dikdörtgen eleman noktası (0,0) hakkında 45 derece döndürülür  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Varsayılan olarak, öğe sol üst köşesinde döner, (0, 0). , <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ScaleTransform>ve <xref:System.Windows.Media.SkewTransform> sınıflar, dönüşümün uygulandığı noktayı belirtmenizi sağlayan CenterX ve CenterY özelliklerini sağlar.  
  
 Bir sonraki örnek <xref:System.Windows.Media.RotateTransform> de 45 <xref:System.Windows.Shapes.Rectangle> derece ile bir öğedöndürmek için a kullanır; ancak, bu <xref:System.Windows.Media.RotateTransform.CenterX%2A> kez <xref:System.Windows.Media.RotateTransform.CenterY%2A> ve özellikleri (25, 25) bir merkezi <xref:System.Windows.Media.RotateTransform> olacak şekilde ayarlanır. Aşağıdaki resimde döndürmenin etkisi gösterilmektedir.  
  
 ![A Geometri yaklaşık 25, 25 &#40;45 derece döndü&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Bir Dikdörtgen eleman noktası (25, 25) hakkında 45 derece döndürülür  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>Bir FrameworkElement dönüştürme  
 Dönüşümleri bir <xref:System.Windows.FrameworkElement>, oluşturmak <xref:System.Windows.Media.Transform> ve <xref:System.Windows.FrameworkElement> sınıfın sağladığı iki özellikten birine uygulamak için:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Düzen geçmeden önce uygulanan bir dönüştürme. Dönüştürme uygulandıktan sonra, düzen sistemi öğenin dönüştürülmüş boyutunu ve konumunu işler.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– Öğenin görünümünü değiştiren ancak düzen geçişi tamamlandıktan sonra uygulanan dönüştürme. <xref:System.Windows.UIElement.RenderTransform%2A> Özellik yerine özelliği kullanarak, performans avantajları elde edebilirsiniz. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>  
  
 Hangi özelliği kullanmalısınız? Sağladığı performans avantajları nedeniyle, özellikle <xref:System.Windows.UIElement.RenderTransform%2A> animasyonlu <xref:System.Windows.Media.Transform> nesneler kullandığınızda özelliği mümkün olduğunca kullanın. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Ölçekleme, döndürme veya eğrilme özelliğini kullanın ve öğenin dönüştürülmüş boyutuna ayarlamak için öğenin üst gerekir. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Özellik ile birlikte kullanıldıklarında, <xref:System.Windows.Media.TranslateTransform> nesnelerin öğeler üzerinde hiçbir etkisi olmadığını unutmayın. Bunun nedeni, düzen sisteminin çevrilen öğeyi işlemenin bir parçası olarak özgün konumuna döndürmesidir.  
  
 Düzen [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]hakkında ek bilgi için Bkz. [Düzen](../advanced/layout.md) genel bakışı.  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Örnek: FrameworkElement 45 Derece döndürme  
 Aşağıdaki örnek, <xref:System.Windows.Media.RotateTransform> bir düğmeyi saat yönünde 45 derece döndürmek için a kullanır. Düğme, diğer iki <xref:System.Windows.Controls.StackPanel> düğmesi olan bir düğmede bulunur.  
  
 Varsayılan olarak, <xref:System.Windows.Media.RotateTransform> bir nokta (0, 0) etrafında döner. Örnek bir merkez değeri belirtmediği için, düğme sol üst köşesi olan nokta (0, 0) etrafında döner. Özellik <xref:System.Windows.Media.RotateTransform> uygulanır. <xref:System.Windows.UIElement.RenderTransform%2A> Aşağıdaki resimde dönüşümün sonucu gösterilmektedir.  
  
 ![RenderTransform kullanılarak dönüştürülmüş bir düğme](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Sol üst köşeden saat yönünde 45 derece dönüş  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Sonraki örnek de <xref:System.Windows.Media.RotateTransform> bir düğmeyi saat yönünde 45 derece döndürmek için <xref:System.Windows.UIElement.RenderTransformOrigin%2A> a kullanır, ancak düğmenin (0,5, 0,5) olarak da ayarlanır. Özelliğin <xref:System.Windows.UIElement.RenderTransformOrigin%2A> değeri düğmenin boyutuna göredir. Sonuç olarak, döndürme sol üst köşesi yerine düğmenin ortasına uygulanır. Aşağıdaki resimde dönüşümün sonucu gösterilmektedir.  
  
 ![Merkezi hakkında dönüştürülmüş bir düğme](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Saat yönünde dönüş merkez etrafında 45 derece  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Aşağıdaki örnek, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> düğmeyi <xref:System.Windows.UIElement.RenderTransform%2A> döndürmek için özellik yerine özelliği kullanır.  Bu, dönüşümün düğmenin düzenini etkilemesine neden olur ve bu da düzen sistemi tarafından tam geçişi tetikler. Sonuç olarak, boyutu değiştiğinden düğme döndürülür ve yeniden konumlandırılır. Aşağıdaki resimde dönüşümün sonucu gösterilmektedir.  
  
 ![LayoutTransform kullanılarak dönüştürülmüş bir düğme](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Button'u döndürmek için kullanılan DüzenTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>Dönüşümleri Animating  
 <xref:System.Windows.Media.Animation.Animatable> Sınıftan miras aldıkları <xref:System.Windows.Media.Transform> için, sınıflar canlandırılabilir. Animasyon <xref:System.Windows.Media.Transform>a, animasyon istediğiniz özelliği uyumlu bir tür animasyon uygulayın.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Storyboard> tıklatıldığında <xref:System.Windows.Media.Animation.DoubleAnimation> yerinde <xref:System.Windows.Media.RotateTransform> bir <xref:System.Windows.Controls.Button> spin yapmak için a ve a ile kullanır.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Numunenin tamamı için [2-B Dönüşüm Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın. Animasyonlar hakkında daha fazla bilgi için [Animasyona Genel Bakış'a](animation-overview.md)bakın.  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable Özellikler  
 Sınıftan <xref:System.Windows.Media.Transform> devraldığı için, sınıf çeşitli özel <xref:System.Windows.Media.Transform> özellikler sağlar: nesneler kaynak olarak bildirilebilir, birden çok nesne arasında paylaşılabilir, performansı artırmak için salt okunur hale getirilebilir, klonlanabilir ve iş parçacığı güvenli hale getirilebilir. [resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) <xref:System.Windows.Freezable> Nesneler tarafından <xref:System.Windows.Freezable> sağlanan farklı özellikler hakkında daha fazla bilgi için [Freezable Objects Overview](../advanced/freezable-objects-overview.md)'a bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Nasıl Dır Konular](transformations-how-to-topics.md)
- [2-B Dönüşüm Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)

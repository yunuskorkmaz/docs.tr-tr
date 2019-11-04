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
ms.openlocfilehash: ead1d114f773cba88e8b3e20f395019fbde3ee15
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458584"
---
# <a name="transforms-overview"></a>Dönüşümlere Genel Bakış
Bu konuda, <xref:System.Windows.FrameworkElement> nesneleri döndürmek, ölçeklendirmek, taşımak (çevirmek) ve eğmek için 2-b <xref:System.Windows.Media.Transform> sınıflarının nasıl kullanılacağı açıklanmaktadır.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Dönüşüm nedir?  
 Bir <xref:System.Windows.Media.Transform>, bir koordinat alanından başka bir koordinat alanına nasıl eşleme veya dönüştürme yapılacağını tanımlar. Bu eşleme, üç satırlık <xref:System.Double> değerleri içeren üç satır koleksiyonu olan bir dönüştürme <xref:System.Windows.Media.Matrix>açıklanmaktadır.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) satır birincil matrislerini kullanır. Vektörler, sütun vektörleri değil, satır vektörleri olarak ifade edilir.  
  
 Aşağıdaki tablo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matrisin yapısını gösterir.  
  
### <a name="a-2-d-transformation-matrix"></a>2-b dönüşüm matrisi  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Varsayılan: 1,0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Varsayılan: 0,0|0,0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Varsayılan: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Varsayılan: 1,0|0,0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Varsayılan: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Varsayılan: 0,0|1.0|  
  
 Matris değerlerini değiştirerek bir nesne döndürebilir, ölçeklendirebilir, eğriltebilir ve taşıyabilirsiniz (çevirebilir). Örneğin, üçüncü satırın ilk sütunundaki değeri (<xref:System.Windows.Media.Matrix.OffsetX%2A> değeri) 100 olarak değiştirirseniz, x ekseninde bir nesne 100 birimleri taşımak için kullanabilirsiniz. İkinci satırın ikinci sütunundaki değeri 3 olarak değiştirirseniz, nesneyi geçerli yüksekliğinin üç katına uzatmak için kullanabilirsiniz. Her iki değeri de değiştirirseniz, nesne 100 birimini x ekseni üzerinde taşır ve yüksekliğini 3 faktörüyle uzatın. Windows Presentation Foundation (WPF) yalnızca Afine dönüştürmeleri desteklediğinden, sağ sütundaki değerler her zaman 0, 0, 1 ' dir.  
  
 Windows Presentation Foundation (WPF), matris değerlerini doğrudan yönetmenize olanak tanısa da, temel matris yapısının nasıl yapılandırıldığını bilmeden bir nesneyi dönüştürmenizi sağlayan birkaç <xref:System.Windows.Media.Transform> sınıfı da sağlar. Örneğin <xref:System.Windows.Media.ScaleTransform> sınıfı, bir dönüştürme matrisini işlemek yerine <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliklerini ayarlayarak bir nesneyi ölçeklendirmenize olanak sağlar. Benzer şekilde, <xref:System.Windows.Media.RotateTransform> sınıfı, bir nesneyi yalnızca <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliğini ayarlayarak döndürmenize olanak sağlar.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Sınıfları Dönüştür  
 Windows Presentation Foundation (WPF), yaygın dönüştürme işlemleri için aşağıdaki 2-b <xref:System.Windows.Media.Transform> sınıfları sağlar:  
  
|örneği|Açıklama|Örnek|Göstermektedir|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Belirtilen <xref:System.Windows.Media.RotateTransform.Angle%2A>bir öğeyi döndürür.|[Nesne Döndürme](how-to-rotate-an-object.md)|![Çizimi döndür](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Bir öğeyi belirtilen <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ölçeklendirir ve miktarları <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>.|[Öğe Ölçeklendirme](how-to-scale-an-element.md)|![Ölçek çizimi](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Bir öğeyi belirtilen <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> tutarlarla eğriltir.|[Bir Öğeyi Eğme](how-to-skew-an-element.md)|![Çizimi eğ](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Bir öğeyi belirtilen <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> tutarlarla taşıyarak (çevirir).|[Bir Öğeyi Çevirme](how-to-translate-an-element.md)|![Çizimi çevir](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Daha karmaşık dönüştürmeler oluşturmak için Windows Presentation Foundation (WPF) aşağıdaki iki sınıfı sağlar:  
  
|örneği|Açıklama|Örnek|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Birden çok <xref:System.Windows.Media.TransformGroup> nesnesini, dönüşüm özelliklerine uygulayabileceğiniz tek bir <xref:System.Windows.Media.Transform> gruplandırır.|[Nesneye Birden Çok Dönüşüm Uygulama](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Diğer <xref:System.Windows.Media.Transform> sınıfları tarafından sağlanmayan özel dönüşümler oluşturur. Bir <xref:System.Windows.Media.MatrixTransform>kullandığınızda bir matrisi doğrudan işleyebilirsiniz.|[Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) Ayrıca 3-b dönüşümler de sağlar. Daha fazla bilgi için <xref:System.Windows.Media.Media3D.Transform3D> sınıfına bakın.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Ortak dönüştürme özellikleri  
 Bir nesneyi dönüştürmenin bir yolu, uygun <xref:System.Windows.Media.Transform> türünü bildirmek ve nesnenin dönüştürme özelliğine uygulamaktır. Farklı nesne türleri farklı tür dönüştürme özelliklerine sahiptir. Aşağıdaki tabloda, yaygın olarak kullanılan birkaç Windows Presentation Foundation (WPF) türü ve bunların dönüştürme özellikleri listelenmektedir.  
  
|Tür|Dönüştürme özellikleri|  
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
 Bir nesneyi dönüştürdüğünüzde, nesneyi dönüştürmeyin, nesnenin bulunduğu koordinat alanını dönüştürüdürler. Varsayılan olarak, bir dönüşüm hedef nesnenin koordinat sisteminin kaynağına ortalanır: (0, 0). Tek özel durum <xref:System.Windows.Media.TranslateTransform>; bir <xref:System.Windows.Media.TranslateTransform>, ortalandığı yere bakılmaksızın çeviri efekti aynı olduğundan ayarlanacak bir merkez özelliklerine sahip değildir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Shapes.Rectangle> öğesini, bir <xref:System.Windows.FrameworkElement>türünü varsayılan merkezi yaklaşık 45 derece (0, 0) olarak döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullanır. Aşağıdaki çizimde, döndürmenin etkisi gösterilmektedir.  
  
 ![0, 0 yaklaşık &#40;45 derece döndürülmüş bir FrameworkElement&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Nokta ile 45 derece döndürülmüş bir dikdörtgen öğesi (0, 0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Varsayılan olarak öğe, sol üst köşesine (0, 0) döner. <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>ve <xref:System.Windows.Media.SkewTransform> sınıfları, dönüşümün uygulandığı noktayı belirtmenizi sağlayan CenterX ve CenterY özellikleri sağlar.  
  
 Sonraki örnek ayrıca, bir <xref:System.Windows.Shapes.Rectangle> öğesini 45 derece döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullanır; Ancak, bu kez <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özellikleri, <xref:System.Windows.Media.RotateTransform> Merkezi (25, 25) olacak şekilde ayarlanır. Aşağıdaki çizimde, döndürmenin etkisi gösterilmektedir.  
  
 ![45 derece döndürülmüş bir geometri &#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Nokta ile 45 derece döndürülmüş bir dikdörtgen öğesi (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>FrameworkElement dönüştürme  
 Dönüşümleri bir <xref:System.Windows.FrameworkElement>uygulamak için bir <xref:System.Windows.Media.Transform> oluşturun ve bunu <xref:System.Windows.FrameworkElement> sınıfının sağladığı iki özelliklerden birine uygulayın:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>: düzen geçirmeden önce uygulanan bir dönüşüm. Dönüşüm uygulandıktan sonra, Düzen sistemi öğenin dönüştürülmüş boyutunu ve konumunu işler.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>: öğenin görünümünü değiştiren ancak düzen geçişi tamamlandıktan sonra uygulanan bir dönüşüm. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği yerine <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini kullanarak performans avantajları elde edebilirsiniz.  
  
 Hangi özelliği kullanmalıyım? Sağladığı performans avantajları nedeniyle, özellikle animasyonlu <xref:System.Windows.Media.Transform> nesneleri kullandığınızda, mümkün olan her durumda <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini kullanın. Ölçeklendirirken, döndürürken veya eğme sırasında <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliğini kullanın ve öğenin dönüştürülmüş boyutuna ayarlanacak öğenin üst öğesine ihtiyacınız vardır. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliği ile kullanıldıkları zaman, <xref:System.Windows.Media.TranslateTransform> nesnelerin öğeler üzerinde hiçbir etkisi olmadığını unutmayın. Bunun nedeni, düzen sisteminin işlemin bir parçası olarak, çevrilmiş öğeyi özgün konumuna döndürmesinin bir parçasıdır.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]düzen hakkında daha fazla bilgi için bkz. [düzene](../advanced/layout.md) genel bakış.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Örnek: FrameworkElement 45 derece döndürün  
 Aşağıdaki örnek, bir düğmeyi saat yönünde 45 derece döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullanır. Düğme, iki farklı düğme içeren <xref:System.Windows.Controls.StackPanel> bulunur.  
  
 Varsayılan olarak, <xref:System.Windows.Media.RotateTransform> (0, 0) noktası hakkında bir değer döndürür. Örnek bir orta değer belirtmediğinden düğme, sol üst köşesi olan nokta (0, 0) ile ilgili olarak döner. <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygulanır. Aşağıdaki çizim, dönüşümün sonucunu gösterir.  
  
 ![RenderTransform kullanılarak dönüştürülen bir düğme](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Sol üst köşeden saat yönünde döndürme 45 derece  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Sonraki örnek ayrıca bir <xref:System.Windows.Media.RotateTransform> bir Button 45 derece saat yönünde döndürmek için bir kullanır, ancak aynı zamanda düğmenin <xref:System.Windows.UIElement.RenderTransformOrigin%2A> (0,5, 0,5) olarak ayarlanır. <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliğinin değeri düğme boyutuna göredir. Sonuç olarak, döndürme sol üst köşesinden değil, düğmenin merkezine uygulanır. Aşağıdaki çizim, dönüşümün sonucunu gösterir.  
  
 ![Bir düğme merkeziyle ilgili olarak dönüştürüldü](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Orta etrafında saat yönünde döndürme 45 derece  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Aşağıdaki örnek, düğmeyi döndürmek için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği yerine <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliğini kullanır.  Bu, dönüşümün düzen sistemi tarafından tam Geçişi tetikleyen düğmenin yerleşimini etkilemesine neden olur. Sonuç olarak, bu düğme döndürülür ve boyutu değiştiğinden yeniden konumlandırılır. Aşağıdaki çizim, dönüşümün sonucunu gösterir.  
  
 ![LayoutTransform kullanılarak dönüştürülen düğme](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
Düğmeyi döndürmek için kullanılan LayoutTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Dönüşümleri Hareketlendirme  
 <xref:System.Windows.Media.Animation.Animatable> sınıfından devraldığı için <xref:System.Windows.Media.Transform> sınıfları canlandırılabilirler. Bir <xref:System.Windows.Media.Transform>hareketlendirmek için, hareketlendirmek istediğiniz özelliğe uyumlu bir tür animasyonu uygulayın.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.DoubleAnimation> ve tıklandığı zaman yerinde bir <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Controls.Button> bir döndürme kullanır.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Tam örnek için bkz. [2-b dönüşümler örneği](https://go.microsoft.com/fwlink/?LinkID=158252). Animasyonlar hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable özellikleri  
 <xref:System.Windows.Freezable> sınıfından devraldığı için, <xref:System.Windows.Media.Transform> sınıfı birkaç özel özellik sağlar: <xref:System.Windows.Media.Transform> nesneler [kaynak](../../../desktop-wpf/fundamentals/xaml-resources-define.md)olarak, birden fazla nesne arasında paylaşılan, performansı geliştirmek için salt okunabilir hale getirilir, klonlanmış ve iş parçacığı güvenli hale getirilir. <xref:System.Windows.Freezable> nesneleri tarafından sunulan farklı özellikler hakkında daha fazla bilgi için, [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Nasıl Yapılır Konuları](transformations-how-to-topics.md)
- [2-b dönüşümler örneği](https://go.microsoft.com/fwlink/?LinkID=158252)

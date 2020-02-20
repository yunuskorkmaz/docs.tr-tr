---
title: Fırça Dönüşümüne Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: 1d3a56014e0975f3616b7f90021b4290ced5daab
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453136"
---
# <a name="brush-transformation-overview"></a>Fırça Dönüşümüne Genel Bakış
Fırça sınıfı iki dönüştürme özelliği sağlar: <xref:System.Windows.Media.Brush.Transform%2A> ve <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Özellikler, fırçanın içeriğini döndürmenizi, ölçeklendirmenizi, eğriltebilir ve çevirmenize olanak tanır. Bu konuda, bu iki özellik arasındaki farklar açıklanmakta ve kullanımları örnekleri verilmektedir.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, dönüştürmelisiniz fırçanın özelliklerini anlamalısınız. <xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>için, [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md)bölümüne bakın. <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>veya <xref:System.Windows.Media.VisualBrush>için bkz. [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md). Ayrıca, [dönüşümler genel bakış](transforms-overview.md)bölümünde açıklanan 2B dönüşümlere de alışkın olmanız gerekir.  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform ve RelativeTransform özellikleri arasındaki farklar  
 Fırçanın <xref:System.Windows.Media.Brush.Transform%2A> özelliğine bir dönüşüm uyguladığınızda, fırça içeriğini merkezine dönüştürmek istiyorsanız, boyanmış alanın boyutunu bilmeniz gerekir. Boyanmış alanın 200 cihazdan bağımsız piksel genişliğinde ve 150 yüksekliğinde olduğunu varsayalım.  Fırçaya ilişkin 45 derecenin ortasına döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullandıysanız, <xref:System.Windows.Media.RotateTransform> 100 ' nin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve 75 <xref:System.Windows.Media.RotateTransform.CenterY%2A> verirsiniz.  
  
 Fırçanın <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğine dönüşüm uyguladığınızda, bu dönüşüm, çıktısı boyanmış alana eşlenmeden önce fırçaya uygulanır. Aşağıdaki listede, fırçanın içeriklerinin işlendiği ve dönüştürülebileceği sıra açıklanmaktadır.  
  
1. Fırçanın içeriğini işleyin. <xref:System.Windows.Media.GradientBrush>için bu, gradyan alanının belirlenmesi anlamına gelir. <xref:System.Windows.Media.TileBrush>için <xref:System.Windows.Media.TileBrush.Viewbox%2A> <xref:System.Windows.Media.TileBrush.Viewport%2A>eşlenir. Bu, fırçanın çıkışı olur.  
  
2. Fırçanın çıkışını 1 x 1 dönüşüm dikdörtgeninin üzerine yansıtın.  
  
3. Eğer varsa fırçanın <xref:System.Windows.Media.Brush.RelativeTransform%2A>uygulayın.  
  
4. Dönüştürülen çıktıyı boyamak için alanın üzerine yansıt.  
  
5. Eğer varsa fırçanın <xref:System.Windows.Media.Transform>uygulayın.  
  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>, fırçanın çıkışı 1 x 1 dikdörtgenle eşlendiğinde uygulandığından, dönüşüm merkezi ve Aralık değerleri göreli olarak görünür. Örneğin, fırçanın merkezi yaklaşık 45 derecesini döndürmek için bir <xref:System.Windows.Media.RotateTransform> kullandıysanız, <xref:System.Windows.Media.RotateTransform> 0,5 ve 0,5 <xref:System.Windows.Media.RotateTransform.CenterY%2A> <xref:System.Windows.Media.RotateTransform.CenterX%2A> verirsiniz.  
  
 Aşağıdaki çizimde <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri kullanılarak 45 derecenin döndürüldüğü birkaç fırçanın çıktısı gösterilmektedir.  
  
 ![RelativeTransform ve Transform özellikleri](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Bir TileBrush ile RelativeTransform kullanma  
 Döşeme fırçaları diğer fırçalardan daha karmaşık olduğundan, bir <xref:System.Windows.Media.Brush.RelativeTransform%2A> bir öğesine uygulamak beklenmedik sonuçlar verebilir. Örneğin, aşağıdaki görüntüyü alın.  
  
 ![Kaynak görüntü](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Aşağıdaki örnek, önceki görüntüyle dikdörtgen bir alanı boyamak için bir <xref:System.Windows.Media.ImageBrush> kullanır. <xref:System.Windows.Media.ImageBrush> nesnesinin <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğine bir <xref:System.Windows.Media.RotateTransform> uygular ve <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliğini, dikdörtgeni tamamen doldurmak için uzatıldığınızda görüntünün en boy oranını koruyacak şekilde <xref:System.Windows.Media.Stretch.UniformToFill>olarak ayarlar.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
 ![Dönüştürülen çıkış](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Fırçanın <xref:System.Windows.Media.TileBrush.Stretch%2A> <xref:System.Windows.Media.Stretch.UniformToFill>olarak ayarlanmış olsa bile görüntünün bozuk olduğuna dikkat edin. Bunun nedeni, fırçanın <xref:System.Windows.Media.TileBrush.Viewbox%2A> <xref:System.Windows.Media.TileBrush.Viewport%2A>eşlendikten sonra göreli dönüşüm uygulanamadığı için geçerlidir. Aşağıdaki listede işlemin her adımı açıklanmaktadır:  
  
1. Fırçanın içeriğini (<xref:System.Windows.Media.TileBrush.Viewbox%2A>), fırçanın <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarını kullanarak temel kutucuğuna (<xref:System.Windows.Media.TileBrush.Viewport%2A>) yansıın.  
  
     ![Görünüm kutusunu görünüm görünümüne uyacak şekilde uzat](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Taban kutucuğunu 1 x 1 dönüşüm dikdörtgeninin üzerine yansıtın.  
  
     ![Görünüm penceresini dönüştürme dikdörtgeniyle eşleme](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. <xref:System.Windows.Media.RotateTransform>uygulayın.  
  
     ![Göreli dönüşümü Uygula](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Dönüştürülen taban kutucuğunu boyamak için alana yansıt.  
  
     ![Dönüştürülmüş fırçayı çıkış alanına yansıt](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Örnek: ImageBrush 45 derece döndürün  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğine bir <xref:System.Windows.Media.RotateTransform> uygular. <xref:System.Windows.Media.RotateTransform> nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özellikleri, içeriğin merkez noktasının göreli koordinatları olan 0,5 olarak ayarlanmıştır. Sonuç olarak, fırçanın içeriği Merkezi hakkında döndürülür.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Sonraki örnek ayrıca bir <xref:System.Windows.Media.ImageBrush><xref:System.Windows.Media.RotateTransform> uygular, ancak <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği yerine <xref:System.Windows.Media.Brush.Transform%2A> özelliğini kullanır. Fırçaya ilişkin fırçayı döndürmek için, <xref:System.Windows.Media.RotateTransform> nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> mutlak koordinatlar olarak ayarlanmalıdır. Fırça tarafından boyanmış dikdörtgen 90 piksel 175, orta noktası ise (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Aşağıdaki çizimde, dönüşümü <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğine uygulanmış ve <xref:System.Windows.Media.Brush.Transform%2A> özelliğine uygulanan dönüşümle birlikte Transform olmadan fırça gösterilmektedir.  
  
 ![Fırça RelativeTransform ve dönüştürme ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır. Tüm örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Fırçalar hakkında daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)

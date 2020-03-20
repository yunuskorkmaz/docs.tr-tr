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
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186521"
---
# <a name="brush-transformation-overview"></a>Fırça Dönüşümüne Genel Bakış
Fırça sınıfı iki dönüştürme <xref:System.Windows.Media.Brush.Transform%2A> özelliği <xref:System.Windows.Media.Brush.RelativeTransform%2A>sağlar: ve. Özellikler, fırçanın içeriğini döndürmenizi, ölçeklendirmenizi, eğriltmenizi ve çevirmenizi sağlar. Bu konu, bu iki özellik arasındaki farkları açıklar ve bunların kullanım örneklerini sağlar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, dönüştürdüğünüz fırçanın özelliklerini anlamanız gerekir. Için <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>ve , [Düz Renkler ve Degradeler Genel Bakış ile Resim](painting-with-solid-colors-and-gradients-overview.md)bakın. Için <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush>, veya , [Resimler, Çizimler ve Görseller ile Boyama](painting-with-images-drawings-and-visuals.md)bakın. Dönüşümlere Genel Bakış'ta açıklanan 2B [dönüşümlere](transforms-overview.md)de aşina olmalısınız.  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform ve RelativeTransform Özellikleri Arasındaki Farklar  
 Bir fırçanın <xref:System.Windows.Media.Brush.Transform%2A> özelliğine dönüştürme uyguladığınız zaman, fırçaiçeriğini merkeziyle ilgili dönüştürmek istiyorsanız, boyalı alanın boyutunu bilmeniz gerekir. Boyalı alanın 200 aygıt bağımsız piksel genişliğinde ve 150 boyunda olduğunu varsayalım.  Eğer fırçanın <xref:System.Windows.Media.RotateTransform> çıkışını merkezi hakkında 45 derece döndürmek için a kullanırsanız, <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100'ün <xref:System.Windows.Media.RotateTransform.CenterY%2A> <xref:System.Windows.Media.RotateTransform> a'sını ve 75'ini verirdiniz.  
  
 Bir fırçanın <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğine dönüştürme uyguladığınız zaman, bu dönüştürme, çıktısı boyalı alana eşlenmeden önce fırçaya uygulanır. Aşağıdaki liste, fırçanın içeriğinin işlenme ve dönüştürülme sırasını açıklar.  
  
1. Fırçanın içeriğini işleme. Bir <xref:System.Windows.Media.GradientBrush>için, bu degrade alanı nın belirlenmesi anlamına gelir. Bir <xref:System.Windows.Media.TileBrush>için <xref:System.Windows.Media.TileBrush.Viewbox%2A> , eşlenir <xref:System.Windows.Media.TileBrush.Viewport%2A>. Bu, fırçanın çıktısı olur.  
  
2. Fırçanın çıktısını 1 x 1 dönüştürme dikdörtgenine yansıtın.  
  
3. Varsa fırçanın <xref:System.Windows.Media.Brush.RelativeTransform%2A>kini uygulayın.  
  
4. Dönüştürülmüş çıktıyı boyamak için alana yansıtın.  
  
5. Varsa fırçanın <xref:System.Windows.Media.Transform>kini uygulayın.  
  
 Fırçanın <xref:System.Windows.Media.Brush.RelativeTransform%2A> çıkışı 1 x 1 dikdörtgen eşlenirken uygulandığından, transform merkezi ve ofset değerleri göreceli görünür. Örneğin, a'yı, <xref:System.Windows.Media.RotateTransform> fırçanın çıktısını merkezi hakkında 45 derece döndürmek için kullanırsanız, 0,5 <xref:System.Windows.Media.RotateTransform.CenterY%2A> ve 0,5'in <xref:System.Windows.Media.RotateTransform> a'sını <xref:System.Windows.Media.RotateTransform.CenterX%2A> verirsiniz.  
  
 Aşağıdaki resimde, 45 derece döndürülen çeşitli fırçaların çıktısı <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri gösterilmektedir.  
  
 ![RelativeTransform ve Transform özellikleri](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>Bir Kiremit Fırçası ile RelativeTransform kullanma  
 Kiremit fırçaları diğer fırçalara göre daha <xref:System.Windows.Media.Brush.RelativeTransform%2A> karmaşık olduğundan, bire bir uygulama beklenmeyen sonuçlara neden olabilir. Örneğin, aşağıdaki resmi alın.  
  
 ![Kaynak görüntü](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.ImageBrush> bir önceki resimle dikdörtgen bir alanı boyamak için bir resim kullanır. Nesnenin <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğine bir uygular ve <xref:System.Windows.Media.TileBrush.Stretch%2A> dikdörtgeni tamamen <xref:System.Windows.Media.Stretch.UniformToFill>doldurmak için gerildiğinde görüntünün en boy oranını koruyacak özelliğini ayarlar.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
 ![Dönüştürülmüş çıktı](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Fırçanınki <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarlanmış olsa bile görüntünün bozuk olduğuna <xref:System.Windows.Media.Stretch.UniformToFill>dikkat edin. Bunun nedeni, göreli dönüşümün fırçanınkine <xref:System.Windows.Media.TileBrush.Viewbox%2A> eşlendikten <xref:System.Windows.Media.TileBrush.Viewport%2A>sonra uygulanmasıdır. Aşağıdaki liste işlemin her adımını açıklar:  
  
1. Fırçanın içeriğini (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) temel döşemesine (<xref:System.Windows.Media.TileBrush.Viewport%2A>) fırçanın <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarını kullanarak yansıtın.  
  
     ![Viewport'a uyacak şekilde Viewbox'ı esnedin](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Temel döşemeyi 1 x 1 dönüştürme dikdörtgenine yansıtın.  
  
     ![Viewport'u dönüşüm dikdörtgenine eşle](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Uygulayın. <xref:System.Windows.Media.RotateTransform>  
  
     ![Göreli dönüşümü uygulayın](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Dönüştürülmüş taban karosu boyamak için alana yansıtın.  
  
     ![Dönüştürülmüş fırçayı çıkış alanına yansıtma](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Örnek: Bir ImageBrush 45 Derece döndürme  
 Aşağıdaki örnek bir <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.Brush.RelativeTransform%2A> . <xref:System.Windows.Media.ImageBrush> Nesnenin <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerinin her ikisi de içeriğin merkez noktasının göreli koordinatları olan 0,5 olarak ayarlanır. Sonuç olarak, fırçanın içeriği merkezi hakkında döndürülür.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Sonraki <xref:System.Windows.Media.RotateTransform> örnek, bir <xref:System.Windows.Media.ImageBrush>, ancak <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özellik yerine özelliği kullanır da uygulanır. Fırçayı merkezi yle döndürmek için <xref:System.Windows.Media.RotateTransform> nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> ve mutlak koordinatlara ayarlanmalıdır. Fırça ile boyanan dikdörtgen 175'e 90 piksel olduğundan, orta noktası (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Aşağıdaki resimde, dönüştürme olmadan fırça, <xref:System.Windows.Media.Brush.RelativeTransform%2A> özellik uygulanan dönüştürme ve <xref:System.Windows.Media.Brush.Transform%2A> özellik uygulanan dönüştürme ile gösterir.  
  
 ![Fırça RelativeTransform ve Transform ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır. Numunenin tamamı için [Fırçalar Örneğine](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın. Fırçalar hakkında daha fazla bilgi için [WPF Fırçalar Genel Bakış'a](wpf-brushes-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)

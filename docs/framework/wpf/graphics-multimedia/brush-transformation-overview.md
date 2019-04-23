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
ms.openlocfilehash: 39b3ad9bebfc56002f77ad6e9026a4446c95455b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298337"
---
# <a name="brush-transformation-overview"></a>Fırça Dönüşümüne Genel Bakış
Fırça sınıf iki dönüşüm özellikleri sağlar: <xref:System.Windows.Media.Brush.Transform%2A> ve <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Özellikleri döndürme, ölçeklendirme, eğme ve bir fırça içeriğini olanak sağlar. Bu konu, bu iki özellik farklılıkları açıklar ve bunların kullanım örneklerini sağlar.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için dönüştürdüğünüz fırça özelliklerini anlamanız gerekir. İçin <xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>, bkz: [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md). İçin <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.VisualBrush>, bkz: [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md). Da açıklanan 2B dönüşümleri hakkında bilgi sahibi olmalısınız [dönüştüren genel bakış](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Dönüşüm ve RelativeTransform Özellikleri arasındaki farklar  
 Bir fırçanın dönüşüm uyguladığınızda <xref:System.Windows.Media.Brush.Transform%2A> özelliği, kendi merkezinde fırça içeriğini dönüştürmek istiyorsanız boyanan alanının boyutunu bilmeniz gerekir. Boyanan alanı 200 cihaz bağımsız piksel genişliğinde ve 150 uzun olduğunu varsayın.  Kullandıysanız bir <xref:System.Windows.Media.RotateTransform> 45 derece merkezi fırçayı döndürmek için çıktı, verirsiniz <xref:System.Windows.Media.RotateTransform> bir <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Bir fırçanın dönüşüm uyguladığınızda <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği çıktısını boyanan alanla eşlenmeden önce dönüşüm fırçaya uygulanır. Aşağıdaki liste bir fırçanın içeriği işlenir ve dönüştürülen sırasını anlatır.  
  
1. Fırçanın içeriğini işler. İçin bir <xref:System.Windows.Media.GradientBrush>, bu gradyan alanını belirleme anlamına gelir. İçin bir <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> eşlenmiş <xref:System.Windows.Media.TileBrush.Viewport%2A>. Bu fırça çıktısı haline gelir.  
  
2. Fırçanın çıkış 1 x 1 dönüşüm dikdörtgenin proje.  
  
3. Fırçanın uygulama <xref:System.Windows.Media.Brush.RelativeTransform%2A>, varsa.  
  
4. Dönüştürülen çıktının boyamak için alan üzerine yansıtın.  
  
5. Fırçanın uygulama <xref:System.Windows.Media.Transform>, varsa.  
  
 Çünkü <xref:System.Windows.Media.Brush.RelativeTransform%2A> fırçanın çıkış 1 x 1 dikdörtgen, dönüşüm merkezi eşlenir ve uzaklık değerleri görünür göreli olarak uygulanır. Örneğin, kullandığınız bir <xref:System.Windows.Media.RotateTransform> 45 derece merkezi fırçayı döndürmek için çıktı, verirsiniz <xref:System.Windows.Media.RotateTransform> bir <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Kullanarak 45 derece döndürülmüş birkaç Fırçalar çıktısı aşağıdaki çizimde <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri.  
  
 ![RelativeTransform ve dönüştürme özelliklerini](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>TileBrush ile RelativeTransform kullanma  
 Kutucuk Fırçalar diğer Fırçalar daha karmaşık olduğu için uygulama bir <xref:System.Windows.Media.Brush.RelativeTransform%2A> birine beklenmeyen sonuçlara neden. Örneğin, aşağıdaki görüntüde yararlanın.  
  
 ![Kaynak görüntü](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.ImageBrush> dikdörtgen bir önceki resimde ile boyamak için. Geçerli bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.ImageBrush> nesnenin <xref:System.Windows.Media.Brush.RelativeTransform%2A> özellik kümeleri ve kendi <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliğini <xref:System.Windows.Media.Stretch.UniformToFill>, koruması gereken görüntünün en boy oranını olduğunda, tamamen dikdörtgen dolduracak şekilde genişletilir.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
 ![Dönüştürülen çıktının](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Görüntü, olsa bile bozuk olduğuna dikkat edin fırçanın <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarlandı <xref:System.Windows.Media.Stretch.UniformToFill>. Göreli dönüşümü fırçanın sonra uygulanan çünkü <xref:System.Windows.Media.TileBrush.Viewbox%2A> eşlenen alt <xref:System.Windows.Media.TileBrush.Viewport%2A>. Aşağıdaki listede işleminin her adımı açıklanmaktadır:  
  
1. Fırçanın içeriğini proje (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) kendi temel döşemesine (<xref:System.Windows.Media.TileBrush.Viewport%2A>) fırça kullanarak <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarı.  
  
     ![Görünüm penceresinin uyacak şekilde Viewbox esnetme](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Taban döşemesi, 1 x 1 dönüşüm dikdörtgenin proje.  
  
     ![Harita Görünüm penceresi dönüştürme dikdörtgene](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Uygulama <xref:System.Windows.Media.RotateTransform>.  
  
     ![Göreli Dönüşümü uygula](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Dönüştürülen taban döşemesi boyamak için alan üzerine yansıtın.  
  
     ![Dönüştürülen fırça çıkış alanına proje](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Örnek: ImageBrush döndürme 45 derece  
 Aşağıdaki örnek geçerli bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği bir <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform> Nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özellikleri hem de ayarlanır 0,5 olarak göreli koordinatları içeriğin merkez noktası. Sonuç olarak, fırçanın içeriğini ortasından döndürülür.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Sonraki örnek de geçerlidir bir <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Media.ImageBrush>, ancak kullandığı <xref:System.Windows.Media.Brush.Transform%2A> özelliği yerine <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği. Kendi merkezi fırçayı döndürmek için <xref:System.Windows.Media.RotateTransform> nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> mutlak koordinatlarına ayarlamanız gerekir. Fırça tarafından boyanan dikdörtgen 175 90 piksel merkez noktası olduğu (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Fırça dönüştürme için uygulanmış bir dönüştürme olmadan aşağıdaki çizimde <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği ile uygulanan dönüştürme <xref:System.Windows.Media.Brush.Transform%2A> özelliği.  
  
 ![Fırça RelativeTransform ve dönüşüm ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Bu örnek, daha büyük bir örnek bir parçasıdır. Tam bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973). Fırçalar hakkında daha fazla bilgi için bkz. [WPF fırçalarına genel bakış](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)

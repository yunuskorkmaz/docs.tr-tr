---
title: "Fırça Dönüşümüne Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b57c5ee36c9ed9c89fc8ca1bfb7ea265c2460c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="brush-transformation-overview"></a>Fırça Dönüşümüne Genel Bakış
Fırça sınıfı iki dönüşüm özellikleri sağlar: <xref:System.Windows.Media.Brush.Transform%2A> ve <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Özellikleri döndürme, Ölçek, eğme ve fırça içeriğini Çevir olanak sağlar. Bu konu, bu iki özellik arasındaki farklılıkları açıklar ve bunların kullanım örnekleri sağlar.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu anlamak için dönüştürdüğünüz fırça özelliklerini anlamanız gerekir. İçin <xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>, bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). İçin <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, veya <xref:System.Windows.Media.VisualBrush>, bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Ayrıca açıklanan 2B dönüşümler hakkında bilgi sahibi olmalıdır [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Transform ve göreli dönüştürme özellikleri arasındaki farklar  
 Fırça için bir dönüşüm uyguladığınızda <xref:System.Windows.Media.Brush.Transform%2A> özelliği, fırça içeriğini merkezi etrafında dönüştürmek istiyorsanız boyanmış alanının boyutunu bilmeniz gerekir. Boyanmış alanın 200 aygıttan bağımsız piksel genişliğinde ve 150 uzunluğunda olduğunu varsayın.  Kullandıysanız bir <xref:System.Windows.Media.RotateTransform> merkezi etrafında 45 dereceyi fırça döndürmek için çıktı, verirsiniz <xref:System.Windows.Media.RotateTransform> bir <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Fırça için bir dönüşüm uyguladığınızda <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği, çıktısını boyanmış alana eşlenmiş önce bu dönüştürme için fırça uygulanır. Aşağıdaki listede fırça içeriğini işlenir ve dönüştürülen sırasını açıklar.  
  
1.  Fırça içeriğini işleyin. İçin bir <xref:System.Windows.Media.GradientBrush>, bu gradyan alanını belirleme anlamına gelir. İçin bir <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> eşlenmiş <xref:System.Windows.Media.TileBrush.Viewport%2A>. Bu fırça çıktı olur.  
  
2.  Proje fırça 1 x 1 dönüşüm dikdörtgenin çıktı.  
  
3.  Fırça uygulamak <xref:System.Windows.Media.Brush.RelativeTransform%2A>, varsa.  
  
4.  Dönüştürülen çıkış boyamak için alan üzerine yansıtın.  
  
5.  Fırça uygulamak <xref:System.Windows.Media.Transform>, varsa.  
  
 Çünkü <xref:System.Windows.Media.Brush.RelativeTransform%2A> fırça çıkış 1 x 1 dikdörtgen, dönüşüm merkezi eşlenen ve uzaklık değerleri görünüyor göreli sırada uygulanır. Örneğin, kullandığınız bir <xref:System.Windows.Media.RotateTransform> merkezi etrafında 45 dereceyi fırça döndürmek için çıktı, verirsiniz <xref:System.Windows.Media.RotateTransform> bir <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Aşağıdaki çizimde 45 kullanarak derece döndürülmüş birkaç Fırçalar çıktısını gösterir <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri.  
  
 ![Göreli dönüştürme ve dönüştürme özellikleri](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Göreli dönüştürme TileBrush ile kullanma  
 Döşeme fırçaları diğer Fırçalar karmaşık olduğu için uygulama bir <xref:System.Windows.Media.Brush.RelativeTransform%2A> birine beklenmeyen sonuçlara neden. Örneğin, aşağıdaki resimde alın.  
  
 ![Kaynak görüntü](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.ImageBrush> dikdörtgen bir önceki görüntüsüyle boyamak için. Geçerli bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.ImageBrush> nesnenin <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği ve kümeleri kendi <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliğine <xref:System.Windows.Media.Stretch.UniformToFill>, koruması gereken resmin en boy oranını tamamen dikdörtgen dolduracak şekilde genişletilir olduğunda.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Bu örnek şu çıkışı üretir:  
  
 ![Dönüştürülen çıkış](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Görüntü, rağmen bozuk olduğuna dikkat edin fırça <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarlandı <xref:System.Windows.Media.Stretch.UniformToFill>. Göreli dönüşüm fırça sonra uygulandığından olan <xref:System.Windows.Media.TileBrush.Viewbox%2A> eşlenmiş kendi <xref:System.Windows.Media.TileBrush.Viewport%2A>. Aşağıdaki liste işleminin her adımı açıklar:  
  
1.  Fırça içeriğini proje (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) kendi temel döşemesine (<xref:System.Windows.Media.TileBrush.Viewport%2A>) fırça kullanma <xref:System.Windows.Media.TileBrush.Stretch%2A> ayarı.  
  
     ![Görünüm penceresinin uyacak şekilde Viewbox uzatma](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Temel Döşeme 1 x 1 dönüşüm dikdörtgenin yansıtın.  
  
     ![Görünüm penceresinin dönüştürme dikdörtgen harita](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Uygulama <xref:System.Windows.Media.RotateTransform>.  
  
     ![Göreli dönüşüm uygulama](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Dönüştürülmüş temel döşemeyi boyamak için alan üzerine yansıtın.  
  
     ![Dönüştürülmüş fırça çıktı alan üzerine yansıtın](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Örnek: ImageBrush döndürme 45 dereceyi  
 Aşağıdaki örnek uygular bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği bir <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform> Nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özellikleri her ikisi de ayarlanır 0,5 olarak içeriğinin merkezinin koordinatlara göre noktası. Sonuç olarak, fırça içeriğini ortasından döndürülür.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Sonraki örnekte de geçerlidir bir <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Media.ImageBrush>, ancak kullanır <xref:System.Windows.Media.Brush.Transform%2A> özelliği yerine <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği. Kendi Merkezi hakkında fırça döndürmek için <xref:System.Windows.Media.RotateTransform> nesnenin <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> mutlak koordinatlara ayarlamanız gerekir. Fırça tarafından boyanmış dikdörtgen 90 piksel 175, orta noktasının olduğundan (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Uygulanan dönüştürme ile bir dönüşüm olmadan fırça aşağıda gösterilmiştir <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği ile uygulanan dönüştürme <xref:System.Windows.Media.Brush.Transform%2A> özelliği.  
  
 ![Fırça göreli dönüştürmesi ve dönüşüm ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Bu örnek daha büyük bir örneğin parçasıdır. Tam bir örnek için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973). Fırçalar hakkında daha fazla bilgi için bkz: [WPF Fırçaları Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Brush.Transform%2A>  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Brush>  
 [Boyama düz renklerle ve gradyan genel bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Dönüşümler genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
